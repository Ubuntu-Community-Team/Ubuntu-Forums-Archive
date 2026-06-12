---
title: "Can't boot Windows after installing Ubuntu 7.04"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by cseljatib on 2007-07-18
Hi there:
in an ibm thinkcentre A50p, of 74.54 GB:

- I have first installed Windows XP, and it was working. Then, using the installation live Cd, I have resize the windows partition to 20.12 GB. Then, I have installed Ubuntu (using the option of partitioning 'longest free used space' or something like that), and it is working perfect!. 
- I am not able to boot in Windows XP (but I do in ubuntu). As soon as I select "Windows XP", XP show me that screen where I can select 'last know configuration', 'safe mode' etc, I have tried with all of them, and every time just restart and the GRUB boot menu appear. Furthermore the GRUB boot menu looks OK.
- I know that Windows XP is there because I can see its partition (when I use the Gparted editor), and also I am able to see the files of the Windows XP partition. Here (between ***) is what I got when I typed 'sudo fdisk -l' at the terminal

***********
Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2627    21101346    c  W95 FAT32 (LBA)
/dev/sda2            2628        9434    54677227+  83  Linux
/dev/sda3            9435        9730     2377620    5  Extended
/dev/sda5            9435        9730     2377588+  82  Linux swap / Solaris
***********

- I have typed 'sudo gedit /boot/grub/menu.lst' at the terminal, and here (between ****) is the portion after the default options
**********************
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dd08a51b-2b20-4cdf-8ea0-b14def67fa64 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dd08a51b-2b20-4cdf-8ea0-b14def67fa64 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=dd08a51b-2b20-4cdf-8ea0-b14def67fa64 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=dd08a51b-2b20-4cdf-8ea0-b14def67fa64 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
***********************

I wonder how can i boot to Windows XP without re-installing Windows XP and/or Ubuntu. 
Do you have any idea what could be wrong and how I can fix it? Any help would be greatly appreciated.
Thanks!

---

### Post by tahnok on 2007-07-18
Does windows give you any error messages before it reboots?

---

### Post by cseljatib on 2007-07-18
No, no message :(. I have tried selecting all the options (last know ..., 'start windows normally',etc) but every time it just restart and load the GRUB menu.

any suggestion

---

### Post by nitro_n2o on 2007-07-18
A safe thing you might do without missing with grub is using your windows CD and try to repair the MBR... give it shot... then if it doesn't work we can play  a little bit with GRUB commands

---

### Post by cseljatib on 2007-07-18
Sorry, but what is "MBR"?, Can you give more details how to do this too, please?

---

### Post by nitro_n2o on 2007-07-18
MBR: MasterBootRecord [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
read the first paragraph in wikipedia they explain it really well.. 
For now if you have the windows CD you should be able to fix, just boot from the windows CD and choose repair (i forgot the details about that, but nothing is hard about it) If this doesn't work, you might need to reconfigure GRUB... 
let us knw if the problem is not fixed
good luck :)

---

### Post by tahnok on 2007-07-18
Just push r after your xp cd has loaded it'll give you a few options like install or autorepair but chose repair.

---

### Post by cseljatib on 2007-07-18
I have booted from the windows XP CD. After the blue screen 'Windows Setup' I am asked to choose: to install (press enter), to repair (press R) and quit. I choose R, but then it appears a windows console with C:\>, what should I do there??,
following other posts, I have also tried not selecting Repair, and continue with the installation, but appears that XP is going to format the whole hard disk, then I will loose all my ubuntu instalation.

Please, help me!

---

### Post by Raineer on 2007-07-18
Windows *should* not format the whole disk, only the partition it is installed from.  Then you will need to take a step where you will reinstall GRUB again and you can point it to both OS's.

I am intrigued though, I don't want to get ahead of ourselves.  Typically a dual-boot problem would mean it can't see Windows at all. You are certainly seeing it but you get the black screen with the options. If you pick "Safe Mode"  do you see *any* text at all before it reboots again?

Also to verify, in between the black screen and your GRUB screen you **do** see the BIOS screen as well right?  I want to ensure your PC is actually rebooting.

---

### Post by Erdosain on 2007-07-18
I am having a very similar, or perhaps the same problem. Typing sudo fdisk -l gives me similar result, and my /boot/grub/menu.lst file does not list my windows installation either. I've tried everything I could find instructions on: remounting the partition, updating grub, installing ntfs-3g, but so far, nothing has seemed to work.
I hope someone can help.

---

### Post by Raineer on 2007-07-18
If the install program didn't place Windows into your GRUB menu then you have to do it manually.

[This]("http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot") is the link I followed. It states it is for Vista but it worked fine for me with XP.

---

### Post by tahnok on 2007-07-18
Windows XP is already in the GRUB menu. It's at the end.
You are supposed to get to the windows console. From there you can run a whole bunch of command to try and get XP to work. I suggest  running chkdsk, which will check your windows partition for errors and fix them if it finds any.

---

### Post by cseljatib on 2007-07-18
I gave up!, 
I have tried with my windows XP CD and after choosing 'recovery console' (in the windows setup) I typed 'bootcfg' (following some other post), after that, I couldn't even enter to the previous GRUB menu that I had (that is to say, I could not access to Ubuntu neither). 
Finally I said: "I will install XP again, and after that install ubuntu as I previously did". But, when installing XP, and restart keep me re-starting every time, then I thought, all right I am going to tried with a Windows 98 CD (actually the PC that I am refering to, is one that the 'experts' at my office said: is dead, it can not be fixed, because some problem that they don't really know), because I 'resucited' this PC installing first windows 98, then i installed a clean XP, and then Ubuntu. Nevertheless, now windows 98 give a message that it can not access C.
Finally, the last option that I had was: Install Ubuntu from zero!!, I did it, and in formating give me only one option (something like 'use the entire disk), because I did not have any other OS working, and believe or not, I was able to install Ubuntu, and not is working again (of course now i do not have the option for booting at the start) which is great!!!. Now, I wonder if can I install windows XP (over Ubuntu) to leave to the other people at the office the option to enter to XP?, or should I try installing XP again, and after that install Ubuntu (because I am assuming that as soon as I am going to install XP is going to delete the ubuntu partition).

Any suggestion

Cheers

---

### Post by nitro_n2o on 2007-07-18
ohh man you gave up pretty quickly.. nevermind 
you can certainly install windows on top of ubuntu, but you need to be careful :) 
check this out: 
[http://ubuntuforums.org/showthread.php?t=22537](http://ubuntuforums.org/showthread.php?t=22537)

---

