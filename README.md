oc和驱动都是自己从官方下的，一步一步自己折腾了几天出来的。EFI很干净 目前使用没发现有啥问题

配置：

CPU i5 8600k

主板 z370n itx

显卡 gt640免驱（如果用的是集显 显示7M 自行注入ID 这个我没测试）

v1

1.关闭了SIP  csr-active-config	E7030000

2.Vault	Kernel-Security-Vault	 Optional

解决开机报错OC:configuration signed vault but no public key provided 

3.UEFI-Quirks-IgnoreInvalidFlexRatio 设置为真 

解决在没有解锁cfg主板上开机报错exitbs:start

4.uefi-Quirks-ReleaseUsbOwnership 设置为真

解决开机报错报错：applefscompressiontypedataless

5.NVRAM-Add-prev-lang:kbd   7A682D48 616E733A 323532 修改为简体中文

6.打开 XhciPortLimit

7.增加219网卡驱动 注入声卡ID

8.增加了SSDT-PLUG.aml补丁,此主板无需AWAC EC PMC补丁

9.ACPI-Quirks选项根据官方要求设置


V2

10.增加序列号(自行设置)

11.设置开机主题
复制OpenCanopy.efi到OC\Drivers目录   复制Resources到OC目录 音频文件仅仅保留OCEFIAudio_VoiceOver_Boot.wav即可
Misc-Boot-PickerMode  External（GUI模式）Builtin(文本模式)

12.打开默认启动项开关,OC引导界面使用CTRL+ENTER设置默认启动项目
Misc-Security-AllowSetDefault  真


v3

13.Misc-Security-ScanPolicy  17763587
这是扫描模式,不能不会引导界面没有 windows启动项.记得把Microsoft放在EFI根目录
14.Misc- boot-HideAuxiliary
隐藏MAC恢复图标启动项

15.每个辅助工具设置为隐藏(隐藏不等于禁用,Enabled为假表示禁用)
Misc-Tools-0-Auxiliary 真
Misc-Tools-1-Auxiliary 真

