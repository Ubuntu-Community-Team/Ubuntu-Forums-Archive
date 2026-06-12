---
title: "compiling kernel"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by NAT1V3 on 2007-07-31
im compiling the kernel for the first time to get my 360 controller working and i am supposed to do this 
Device Drivers -> Input device support -> Joystick interface
Device Drivers -> USB support -> USB Human Interface Device (full HID) support
Device Drivers -> USB support -> USB Human Interface Device (full HID) support -> HID input layer support (this cannot be compiled as a module)
Device Drivers -> USB support -> X-Box gamepad support
now first off am i supposed to include these or module them  i found the first one but i dont see the other 3 i am doing a make menuconfig  of kernel version 2.6.22.1 
here are the guides this one is to set up the controller [http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux)
and this one is how to compile the kernel [http://linuxplanet.com/linuxplanet/tutorials/202/1/](http://linuxplanet.com/linuxplanet/tutorials/202/1/)

any help would be appreciated, Brad

---

### Post by IamAcoconut on 2007-08-01
Compiling the kernel doesn't belong here, it's not that easy. 
Maybe try here: [http://ubuntuforums.org/forumdisplay.php?f=140](http://ubuntuforums.org/forumdisplay.php?f=140)
Perhaps this can be of some use: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

