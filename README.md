# R7000-brightness-control



(一).自动运行

下载并以root运行change.sh，若出现问题请检查文件完整或手动更改

$sudo chmod +x change.sh

$sudo ./change.sh

$reboot 

重启后生效

(二).手动运行

1.修改/etc/default/grub

将GRUB_CMDLINE_LINUX=""

更改为GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

2.执行 $sudo update-grub

3.在/usr/share/X11/xorg.conf.d中添加

Section "Device"

Identifier "Device0"

Driver "nvidia"

VendorName "NVIDIA Corporation"

Option "RegistryDwords" "EnableBrightnessControl=1"

Option "Nologo" "True"

EndSection

4.在/etc/modprobe.d/blacklist.conf中禁用nouveau和ideapad_laptop

$sudo gedit /etc/modprobe.d/blacklist.conf

添加：

blacklist nouveau

blacklist ideapad_laptop

5.更新配置

$sudo update-initramfs -u

$reboot

重启后生效

