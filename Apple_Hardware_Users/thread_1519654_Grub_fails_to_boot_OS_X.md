---
title: "Grub fails to boot OS X"
date: 2010-06-28
forum: Apple Hardware Users
---

### Post by AliceInWonderland on 2010-06-28
Hello,

I was a nerd in high school and got into Red Hat and all that, but when I went to college, I studied social sciences and became hip and stopped the geekdom. Now I'm unemployed (stupid useless economics degree...) and wishing I had kept up on my (formerly) mad computer skills. So I'm getting back into Linux, but I've forgotten everything and I'm back on square 1: newbieland! Thanks for any assistance you can provide.

I'm running OS X 10.5.8 on a MacBook 3,1. I installed Ubuntu 10.04 a few days ago and haven't been able to get Mac OS to boot through Grub. That is, if I hold down option during the boot up, I can choose the Mac partition (dev/sda2) and it starts fine. But if I let Grub start, and choose Mac OS X 32-bit, the computer screen goes black, turns off, and the computer restarts. I have no idea why.

I've searched through the forums a bit and haven't found any particular clues, but of course I may have missed something so apologies if there is already documentation on how to fix this.

The grub screen calls itself grub1.98-1ubuntu5, which confused me--I thought 10.04 came with Grub2? 

In /boot/grub/grub.cfg, the script for Mac OS 32 bit is as follows: 

menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 8fcf442e97e027ec
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 8fcf442e97e027ec uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}

I tried running grub-mkconfig, and it rebuilt Grub successfully but the problem persists.

Anyone have ideas? Should I install rEFIt?

---

### Post by Helios747 on 2010-06-28
Last time I checked (I single boot my mac), GRUB2 has lousy support for booting OS X. To be honest I don't know why the Ubuntu devs went with GRUB2 when it creates more issues than it solves, at least with me.


If I were you I would just go with rEFIt.

---

### Post by xanadu1988 on 2010-06-28
agreed. rEFIt works great on my late 2006-era macbook - triple booting lucid, win7 and leopard.

---

### Post by AliceInWonderland on 2010-06-28
I installed rEFIt, and it works great. Thanks.

---

