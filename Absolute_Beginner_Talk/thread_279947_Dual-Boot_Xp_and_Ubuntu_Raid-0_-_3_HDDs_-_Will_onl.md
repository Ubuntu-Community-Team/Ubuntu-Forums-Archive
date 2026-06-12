---
title: "Dual-Boot Xp and Ubuntu Raid-0 - 3 HDDs - Will only boot to XP"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by X3R0420 on 2006-10-18
I started out by installing XP onto the RAID-0 Array using 40GB for the windows install and left the other 178GB as a drive to store MyDocs on. I then installed Ubuntu on the 3rd HD (All 3 HDD are sata.) which is not part of an array. I part'ed it as 80GB for an additional primary partition in windows, created a 512mb swap partition and a 30GB partition for the /root partition. I then proceeded to install Ubuntu on that partition..everything seemed to go fine but after install and reboot I get no option for Linux, the machine only recg. XP and boots straight to it...I'm wedged! Any help will be greatly appreciated. I did all the RTFM I could find and still stuck.

---

### Post by Aberrix on 2006-10-18
So ubuntu is on the 3rd, non-raid hard drive? correct?

sounds like you just need to reinstalled GRUB on the raid drives mbr

---

### Post by gn2 on 2006-10-18
Perhaps this might be adapted to suit your needs?

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Or Super Grub disc to boot the Raid? 

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by X3R0420 on 2006-10-18
Correct..Linux is on the 3rd, not RAID drive. I will explore the links provided..thanks! I have no exp. with Grub so I prolly need to read up a bit more

---

### Post by X3R0420 on 2006-10-18
BTW Aberrix...I have the exact same MB as you have listed in your sig.

---

### Post by Scunizi on 2006-10-18
Although I'm not running RAID there is some information in the release notes for Ubuntu Dapper concerning this.  I do have 3 drives, 2 STAT and one IDE and also ran into a problem.  Doing the following just prior to installing fixed my install issues with grub.  It's also very easy. The quote was taken from [HERE]("http://www.ubuntu.com/download/releasenotes/606")

> If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer.

---

### Post by X3R0420 on 2006-10-18
The boot option menu worked!!! Thanks a ton..I am now booted into Ubuntu and posting this reply. This is my first go round with Linux so I feel like I accomplished something!!! I just installed about 42 updates so I'm going to reboot and see what happens..hopefully XP install has not been thrashed. Thanks again fellas!

---

### Post by gn2 on 2006-10-18
> **X3R0420 said:**
> The boot option menu worked!!! 

Can you give more details of how you got sorted please? 

Was it the "F8" trick?

Glad you're enjoying Linux, just think the money you'll save......

---

### Post by X3R0420 on 2006-10-18
Yea F8 did it. Went to a BIOS boot menu and I selected the 3rd non-Raid HDD and Linux booted. I rebooted and by default the machine booted back to XP! Exactly what I was lookin for!

---

### Post by gn2 on 2006-10-18
> **X3R0420 said:**
> Yea F8 did it. Went to a BIOS boot menu and I selected the 3rd non-Raid HDD and Linux booted. I rebooted and by default the machine booted back to XP! Exactly what I was lookin for!

Excellent. Thanks for the info.

---

### Post by X3R0420 on 2006-10-19
Thank u for the link!

---

### Post by adrian15 on 2006-10-20
> **X3R0420 said:**
> Yea F8 did it. Went to a BIOS boot menu and I selected the 3rd non-Raid HDD and Linux booted. I rebooted and by default the machine booted back to XP! Exactly what I was lookin for!

Can you add
```

title Boot Win 1st test
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1)
chainloader +1
boot
title Boot Win 2nd test
map (hd0) (hd2)
map (hd2) (hd0)
rootnoverify (hd2)
chainloader +1
boot
title Boot Win 3rd test
map (hd0) (hd3)
map (hd3) (hd0)
rootnoverify (hd3)
chainloader +1
boot

```

to the end of /boot/grub/menu.lst as root? 

(Using sudo gedit /boot/grub/menu.lst)

If when booting ubuntu you can choose one of the boot win option and it boots your windows system... then the only thing you have to do is set the bios so that the 3rd non-Raid HDD is the one that it boots by default.

This way you will never need to use F8 anymore.

Does it work?

adrian15

---

### Post by gn2 on 2006-10-20
> **adrian15 said:**
> Can you add
```

title Boot Win 1st test
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1)
boot
title Boot Win 2nd test
map (hd0) (hd2)
map (hd2) (hd0)
rootnoverify (hd2)
boot
title Boot Win 3rd test
map (hd0) (hd3)
map (hd3) (hd0)
rootnoverify (hd3)
boot

```

to the end of /boot/grub/menu.lst as root? 

(Using sudo gedit /boot/grub/menu.lst)

If when booting ubuntu you can choose one of the boot win option and it boots your windows system... then the only thing you have to do is set the bios so that the 3rd non-Raid HDD is the one that it boots by default.

This way you will never need to use F8 anymore.

Does it work?

adrian15

But if it's working well and he's happy with the way it is, why start mucking about and potentially causing further problems?

Grub editing simply isn't necessary in all cases.

If it ain't broke don't fix it....
.

---

### Post by Herman on 2006-10-20
It won't do any harm though, and it's fun, and it might get his system working the way it's supposed to. I thought that was a very clever idea of adrian15's to devise a testing strategy like that.
Most people enjoy learning how to tweak their systems to make them work the way they want. 
He can still fall back to the F8 trick if he still needs to. Don't you enjoy exercising your brain, and seeing if you can devise better ways to configure your system? 
Regards, Herman :D

---

### Post by gn2 on 2006-10-20
> **Herman said:**
>  Don't you enjoy exercising your brain, and seeing if you can devise better ways to configure your system? 
Regards, Herman :D

No, I just want a simple system that requires minimal maintenance and maximum stability.

Which is why I use Linux.
.

---

### Post by confused57 on 2006-10-20
> **Herman said:**
> It won't do any harm though, and it's fun, and it might get his system working the way it's supposed to. I thought that was a very clever idea of adrian15's to devise a testing strategy like that.
Most people enjoy learning how to tweak their systems to make them work the way they want. 
He can still fall back to the F8 trick if he still needs to. Don't you enjoy exercising your brain, and seeing if you can devise better ways to configure your system? 
Regards, Herman :D
I would like to thank adrian15 for his development of the Super Grub Disk...I agree that making the changes in /boot/grub/menu.lst will not affect booting the different drives using the F8 option.  If one of the entries adrian suggested works, one could choose to boot either way, F8 or grub, whichever they desire.  There are different ways to accomplish the same task, it nice to have a choice.

---

