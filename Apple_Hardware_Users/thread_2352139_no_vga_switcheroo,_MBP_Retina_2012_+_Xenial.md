---
title: "no vga_switcheroo, MBP Retina 2012 + Xenial"
date: 2017-02-09
forum: Apple Hardware Users
---

### Post by themacmeister on 2017-02-09
My system (live external 2TB install of 16.04.1) running on my 15" mid-2012 MacBook Pro Retina, has no /sys/kernel/debug/vga_switcheroo ???

Anyone know how to control this now?

Here is my output from gpu-manager

```
sudo gpu-manager 
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
/etc/modprobe.d is not a file
can't access /run/u-d-c-fglrx-was-loaded file
/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
/etc/modprobe.d is not a file
Looking for fglrx modules in /lib/modules/4.4.0-62-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-62-generic/updates/dkms
Found nvidia module: nvidia_367_drm.ko
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:166
BusID "PCI:0@0:2:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver. Skipping...
Vendor/Device Id: 10de:fd5
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Current alternative: /usr/lib/nvidia-367/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-367/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Single card detected
Driver is already loaded and enabled
Nothing to do
No change - nothing to do

```

---

### Post by themacmeister on 2017-02-09
prime-switch does not work either...

/etc/modprobe.d is not a file

sigh

---

### Post by QIII on 2017-02-10
Moved to Apple Hardware Users.

Hopefully this is a better fit.  Your hardware is Apple, but your OS is Ubuntu.

---

