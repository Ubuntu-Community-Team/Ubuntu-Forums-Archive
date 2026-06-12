---
title: "Error 2 on boot up"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by bwolper on 2007-04-09
Error 2 on first run of Kubuntu 

--------------------------------------------------------------------------------

I just installed Kubuntu 6.10 with the alt. installation disk. Everything seemed to well during the installation.

Upon booting my system I get "Grub loading stage1.5. the next line says "Grub loading, please wait. . . " the next line says "Error 2" and it just sits there.

What does this mean and what do I need to do from here?

---

### Post by terdon on 2007-04-09
Ok, sounds like you have GRUB configured badly. Error 2 is: > 

2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.
You could try booting into a rescue system from the install cd and then reinstalling GRUB. 


So, it seems that you are telling grub to boot from a disk that it cannot find. Try booting into a rescue system by booting from the cd and then choosing "Recover a broken system" from the cd's menu. Once there, login as root and post the output of ```
cat  /boot/grub/menu.lst   
```
and
```
 cat /etc/fstab 
```

NOTE: I am not sure how ubuntu sets up it's rescue system. If it manages to load your installed system, then the above will work. Otherwise you need to know what partition your root (/) is. For example, in my system it is the 5th partition of my first hard drive (/dev/hda5). What you then need to do is from the rescue system:```
 
mkdir ha
mount -t  reiserfs /dev/hda5 /ha
chroot ha

```

This will create a directory called ha, mount your root partition (/dev/hda5 in my case, i don't know what it will be in yours) at that directory, and then tell ubuntu to use the directory ha as the system's root directory. After that, cat the 2 files mentioned above.

I realize I have rambled a bit, and i don't know how comfortable you are with terminal commands. If you want anything made clearer just let me know.

---

### Post by mesyos on 2007-11-10
I had the same problem after a fresh install of xubuntu 7.10 gusty gibbons. 

...Grub loading...
error 2...

I'ts because your bios doesn't see the disks where they should be. My bios config was set on auto while booting the system so i used the IDE automated detection utility included in my bios and it found out all the disks right away.

I rebooted and finally got a grip of my all new machine (well... i found it in my neighbours trash...but still) 

Got it easy this time.

Hope it'll help

---

