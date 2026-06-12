---
title: "MacOSX on Ubuntu multiboot -- except it won't boot!"
date: 2010-01-22
forum: Apple Hardware Users
---

### Post by quixote on 2010-01-22
OSX is on a partition of an Ubuntu system. (Yes, I do have a full price retail DVD.)  It runs well, but now I'd like to get my Ubuntu multiboot back.  I have a Chameleon bootloader which points to the OSX partition, but how do I get it to also see Ubuntu?  

Or, I hear that grub2 understands EFI, but I'm intimidated by grub2 :).  Are there nice step-by-step instructions on how to get it to work with **existing** OSX and ubuntu partitions?  I really don't want to reinstall for about the fifth time.  (My old grub was installed to sda rather than the ubuntu partition specifically, and no longer works of course.)

As for rEFIt, the instructions I've seen say to install that first on your existing Mac, and then install Ubuntu.  That doesn't work for me.  I'd just like to use a bootloader, any bootloader, that I can point to the two existing installations.

My HD is partitioned as follows:
```
sda1: Ubuntu  /     ext3
sda2: Ubuntu  /home ext3
sda3: OSX           hfs+
sda4: swap
```

---

### Post by quixote on 2010-01-22
I found an answer on the on the [insanelymac forum]("http://www.insanelymac.com/forum/lofiversion/index.php/t189079.html") in a comment by kr4zycld.  It works for old grub, not grub2.

After installing both OSes and the chameleon/ darwin bootloader for the OSX partition:

++boot with an ubuntu (or other linux?) liveCD

++use gparted (aka "Partition Editor") (found under System > Administration).  If your linux partition is flagged "boot", go to Partition > Manage Flags and uncheck "boot".  If your OSX partition is not marked boot, then go through the same process to mark it "boot."  Close gparted.

++Install grub to the linux partition, NOT to the MBR:
while still booted on the liveCD, open a terminal (Accessories > Terminal) and type
```
$sudo grub                   *[that gives you the grub prompt]*
grub>find /boot/grub/stage1  *[that returns the linux boot location, say (hd0,0)]*
grub>root (hd0,0)            *[tells grub where the linux root is located]*
grub>setup (hd0,0)              
    *[tells grub to install in partition 1 of HD 1.  (hd0) would install to the MBR]*
grub>quit
$
```
and restart to...

Boot back into OSX, and open a terminal
type the command:
```
sudo fdisk -u -f /usr/standalone/i386/boot0 /dev/rdisk0 
```
          [replaces the previous mbr install of grub with the chameleon / darwin loader]
         [fdisk will reformat your whole drive if done wrong.  don't make any typos!]
          -u says rewrite the MBR and preserve the partition table
         -f says use the following file
         /dev/rdisk0  says write the MBR on the first HD.  You can check the correct designation on your system by running "diskutil list" in the terminal.

And then reboot.  When the chameleon loader comes up, hit any key when it says you can to make the actual choice for another OS to show up.

Hope it works as well for you as it did for me :)

---

### Post by linuxopjemac on 2010-01-23
great for you

---

### Post by natgab on 2010-01-24
> **quixote said:**
> I found an answer on the on the [insanelymac forum]("http://www.insanelymac.com/forum/lofiversion/index.php/t189079.html") in a comment by kr4zycld.  It works for old grub, not grub2.

After installing both OSes and the chameleon/ darwin bootloader for the OSX partition:

++boot with an ubuntu (or other linux?) liveCD

++use gparted (aka "Partition Editor") (found under System > Administration).  If your linux partition is flagged "boot", go to Partition > Manage Flags and uncheck "boot".  If your OSX partition is not marked boot, then go through the same process to mark it "boot."  Close gparted.

++Install grub to the linux partition, NOT to the MBR:
while still booted on the liveCD, open a terminal (Accessories > Terminal) and type
```
$sudo grub                   *[that gives you the grub prompt]*
grub>find /boot/grub/stage1  *[that returns the linux boot location, say (hd0,0)]*
grub>root (hd0,0)            *[tells grub where the linux root is located]*
grub>setup (hd0,0)              
    *[tells grub to install in partition 1 of HD 1.  (hd0) would install to the MBR]*
grub>quit
$
```
and restart to...

Boot back into OSX, and open a terminal
type the command:
```
sudo fdisk -u -f /usr/standalone/i386/boot0 /dev/rdisk0 
```
          [replaces the previous mbr install of grub with the chameleon / darwin loader]
         [fdisk will reformat your whole drive if done wrong.  don't make any typos!]
          -u says rewrite the MBR and preserve the partition table
         -f says use the following file
         /dev/rdisk0  says write the MBR on the first HD.  You can check the correct designation on your system by running "diskutil list" in the terminal.

And then reboot.  When the chameleon loader comes up, hit any key when it says you can to make the actual choice for another OS to show up.

Hope it works as well for you as it did for me :)

I have been trying to get the same thing working.  Except for a few deatails differnt in my setup:

3 OS, not 2: OS X Hackintosh / Ubuntu / Haiku

Each has its own HD.  I will try your method and see if it works. I posted this yesterday and have been searching both Here & InsanelyMac forums for help.

btw: Haiku is expendable, it might become a FAT32 transfer HD.

[http://ubuntuforums.org/showthread.php?t=1387581](http://ubuntuforums.org/showthread.php?t=1387581)

---

### Post by quixote on 2010-01-24
Linuxopjemac: yeah, I was really tickled when I finally got it.  Now I just have to figure out the same for grub2!

natgab: your thread was actually one of the ones I read while I was looking for an answer to this question :).  I'd never even heard of Haiku, so it was interesting to find out it's good old BeOS v2.  Since it is a unix-family OS, I'm pretty sure all you need to do is point grub to it.  

Multibooting with a MacOS, afaik, is always a matter of 1) using a Mac-type bootloader to choose between MacOS and everything else, and then 2) using grub or the like to choose between the other OSes.  So, I think, you could basically follow the method above for two OSes, and then add your other OSes to grub just like you normally would.

Let me know if that makes sense and/or works :D.

(I just read your thread again, and I think the only thing you did differently was try to add OSX to grub.  I'm pretty sure that never works, although grub2 is supposed to be able to deal with it.)

---

### Post by natgab on 2010-01-25
Quixote,

I just solved everything this weekend after my last post.  I have all 3 operating systems booting from Chameleon.  I am glad you mentioned about Haiku, since I was assuming most people knew it was based on Be OS.

You should go and see the Haiku website.  I had it working fine on Virtual Box on Ubuntu before I took the plunge and installed it to my computer.

see my old thread for explanation:

[http://ubuntuforums.org/showthread.php?p=8704950#post8704950](http://ubuntuforums.org/showthread.php?p=8704950#post8704950)

---

### Post by quixote on 2010-01-25
*How* did you get Chameleon to deal with all 3 OSes??  I've been trying to figure that out!

Haiku does indeed look very interesting.

---

### Post by natgab on 2010-01-27
> **quixote said:**
> *How* did you get Chameleon to deal with all 3 OSes??  I've been trying to figure that out!

Haiku does indeed look very interesting.

See the other post. I made all HD GUID partition table. Chameleon now sees Ubuntu without problem.  

Haiku is still giving me an " initialize this HD? " message in OS X.  No problems in Ubuntu.  But of course Haiku is till an alpha release so it could be Haiku's fault in not identifying itself properly to OS X.

Don't have any idea how it works with Windows.  I only have Windows under VirtualBox to test media.

---

### Post by quixote on 2010-01-27
*I made all HD GUID*  

Oh, okay, I see.  That makes sense.

Re Windows, that's how I have it too.  As somebody said, "Windows should only run under Linux supervision."

---

