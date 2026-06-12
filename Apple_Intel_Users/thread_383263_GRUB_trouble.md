---
title: "GRUB trouble"
date: 2007-03-13
forum: Apple Intel Users
---

### Post by squeezy on 2007-03-13
I followed this guide...

[http://doc.gwos.org/index.php/UbuntuOnApple#How_to_Install_Ubuntu_on_Apple.27s_Hardware](http://doc.gwos.org/index.php/UbuntuOnApple#How_to_Install_Ubuntu_on_Apple.27s_Hardware)

I got Ubuntu to install completely. But on the second install of GRUB in the terminal ( it was a part of the guide ), it wouldn't install.

When I rebooted, rEFIt didn't come up. So I figured I may need to install it on OS X (oh yeah, I had to reinstall OS X, not a big deal, but dammit). I did that, rebooted, and there was a linux Icon.

I clicked on it, and I got this...

Grub>

A command prompt. I entered "Boot" and recieved this error; "Error 8: Kernel must be loaded before booting".

I went back into the Live CD and tried to install GRUB again in the terminal, but had no luck.

Now when I click on the Linux icon in rEFIt, the screen goes black.

Please, PLEASE, don't tell me I have to do this all over again. Anyone have any ideas?

---

### Post by squeezy on 2007-03-13
I've done another install, with a clean install of OS X . Everything worked right this time, but I still get the same screen when trying to load Linux. 

From the GRUB command line I've tried these commands with no luck

> root (hd0,2) /boot         (ive used 1, 2, and 3 in place of "2")

> setup (hd0)    <---- that gives me an error; Cannot mount selected partition.

So... can anyone help me?

---

### Post by cyberdork33 on 2007-03-13
Look here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Specifically Step 6

---

### Post by squeezy on 2007-03-14
> **cyberdork33 said:**
> Look here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Specifically Step 6

Thanks. I followed that guide the first time, and had the same results.

I also have done step 6 from inside the Live CD, and in rEFIt, according to it, everything is synced.

---

### Post by Gen2ly on 2007-03-14
Heres a great guide.

[How to restore Grub from a live Ubuntu cd.]("http://www.ubuntuforums.org/showthread.php?t=224351")

It has two methods there of restoring grub. 

If that doesn't work (though it should) Do you see somthing like this in /boot/grub/menu.lst:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash lpj=8000000
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

---

### Post by AnthonyJK@gmail.com on 2007-03-14
I've been trying to install Ubuntu on my macbook all day with no luck :( I tried installing it using LILO but failed so I went on to try installing with GRUB following the instructions at [http://help.ubuntu.com/community/MacBook](http://help.ubuntu.com/community/MacBook) and now this is where im stuck :( 

Please help I'm having this exact same problem. When I boot up in Ubuntu I get taken to a screen that says 

[Minimal Bash-like line editing is supported. For the first word, TAB lists possible comman completions. Anywhere else TAB lists the possible completions of a device/filename]

GRUB>_

Any help would be appreciated :)

---

### Post by spigolo on 2007-03-14
i've been installing this for 2 days (on a imac intel c2d 20")  with the same problem you have, but finally did it.
the problem seems that gpt and mbr are not in sync. if you use the rEFIt tool to sync your partition tables what does it tell you? 
my problem was that gpt was wrong, showing partition 3 (the one supposed to be linux) as fat32, and whenever i synced through the utilities the mbr resulted wrong, not giving grub the possibility to boot. syncing the other way around (have gpt copy mbr) it's not suggested in forums, although there are ones that explain how to reedit the gpt from scratch. for what i understand, part of it seems to be the fact that rEFIt has problems with the boot flag on partition 3.

so i went around it by booting the ubuntu live cd, using gnome partition editor to remove the boot flag from the linux partition. then i used fdisk to set id 83 on the linux partition (gnome partition editor saw it already as linux, fdisk not) with:

sudo sfdisk -c /dev/sda 3 83

then rebooted. then rebooted again (first time didnt work...). the rEFIt sync tool shows slightly different names but it says the partitions are synced.

hope it works :)

---

### Post by cyberdork33 on 2007-03-14
The issue is that you have to sync the partitions at a specific time during the install. the ubuntu partitioner messes up the tables, and they have to be synced again before you can install grub. Also, you have to change where grub is installed, you want to install it to the root partition, not the MBR of the Hard drive!

---

### Post by the.dark.lord on 2007-03-24
I got a Ubuntu Dapper Drake (6.06) CD, and installed it on my intel iMac. When I boot my computer, it Says;

GRUB loading, please wait.... 

forever.

Any help greatly appriciated :).

EDIT: I forgot to mention that, I erased the whole HD -removed OS X- and installed Ubuntu.

---

### Post by Gen2ly on 2007-03-25
ru using a bootloader or just trying to start from the MBR?  It's easiest to prepare a bootloader like rEFIt or BootCamp.

---

### Post by the.dark.lord on 2007-03-25
> **Dirk.R.Gently said:**
> ru using a bootloader or just trying to start from the MBR?  It's easiest to prepare a bootloader like rEFIt or BootCamp.

I just clicked erase while installation, and wiped out OS X. I don't exactly get you, I'm quite new to linux.

---

