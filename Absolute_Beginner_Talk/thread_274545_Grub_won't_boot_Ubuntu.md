---
title: "Grub won't boot Ubuntu"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-10-10
Hi,
   I start my PC and Grub loads: I'm presented with the option of "Ububtu, kernel 2.6.15-15-27-386" -it's highlighted and I hit ENTER. I then get the following error:
"root(hd0,0) 
   File system type unknown, partition type 0x5
kernel  /boot/vmlinuz -2.6.15-27-386 root=/dev/sda1 ro quiet splash
Error 17: cannot mount selected partition
Press any key to continue"

Background: I had been dual-booting Windows XP and Ubuntu Dapper Drake and all was working well -then I reinstalled Windows so I lost my MBR. I followed these instructions to get it back:
1.Boot to the Ubuntu live CD.
2.sudo grub.
3.at grub prompt enter: "find /boot/grub/stage1"
This returned  "(hd0,2)"
4.enter "root (hd0,2)"
5.enter "setup (hd0)"
6.enter "quit"
7.reboot

and that's when I get to the grub menu and get the errorwhen I select Ubuntu.
I have a feeling I missed something in the above instructions...could someone point me in the right direction?
Thanks for your time.

---

### Post by halitech on 2006-10-10
how are your drives set up? sounds like you have the wrong numbers in somewhere

sudo fdisk -l

---

### Post by fiver22 on 2006-10-10
fdisk -l gives:
/dev/sda1     2     889     6713280     5     Extended
/dev/sda2 *   890   15276 108765720     7     HPFS/NTFS
/dev/sda3    151277 16663  10485720    83     Linux 
/dev/sda4    16664  16802  1050840     82     Linx Swap/Solaris
/dev/sda5     2     889    6713248+     7     HPFS/NTFS

is that any help? -and thanks again for your help.
 

> **halitech said:**
> how are your drives set up? sounds like you have the wrong numbers in somewhere

sudo fdisk -l

---

### Post by jorn on 2006-10-10
Next time you boot try to press the e key. Means edit.
If you have just one HD grub must be installed on the first patition on that drive. And that's (hd0,0). Is that what comes up after pressing the e?

---

### Post by halitech on 2006-10-10
to be honest, I'm not familiar with sata drives but maybe this will help

[http://www.ubuntuforums.org/showthread.php?t=133330&highlight=grub+sata]("http://www.ubuntuforums.org/showthread.php?t=133330&highlight=grub+sata")

[http://www.ubuntuforums.org/showthread.php?t=256263&highlight=grub+sata]("http://www.ubuntuforums.org/showthread.php?t=256263&highlight=grub+sata")

---

### Post by jorn on 2006-10-10
Have you got both sata and Ide disks installed?
I had the same issue ones.
Solved it by editing /grub/boot/menu.lst.
> 
title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
I had to change the "root" to (hd1,0)

---

### Post by Bigbluecat on 2006-10-10
I agree that it sounds like grub is looking at the wrong partition during boot. I found the following guides very helpful in solving boot issues.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This guid tells you everyhting you ever wanted to know about grub. You can use it to manually boot your kernel from the grub command line interface (press c during boot). Scroll doen the page to the grub CLI section. There is a very good step by step guide.

Super Grub Disk is also very useful to keep around:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

If your boot sector get's messed up this will let you boot and recover just about anything

---

### Post by fiver22 on 2006-10-11
Tried 'edit' via GRUB menu -but nothing I tried booted properly:

I did notice that when in Windows if I use Partition Magic it reads as follows:
(*)                   unallocated     7.4MB
(*)                   extended        6555.9MB
Windows(D:)           NTFS            6555.9MB
Data+Pograms(M:)      NTFS            106,206.5MB
Local Disk(*:)        Linux Ext3      10,240.0MB
SWAPSPACE2(*:)        Linux Swap      1026.2MB
(*)                   unallowcated    114,426.2MB

It's that last entry that I'm focusing on -the one that says:
"(*)                   unallowcated    114,426.2MB"
-that should be a Linux partition with all my data is what I'm thinking: 
does this shed any light on it?
I would really Love to be able to boot back into Ubuntu -any help/suggestion will be explored and tried -thank you for any help you can give.
Yours,
      Jimmy (learning Linux and enjoying the process).

EDIT: I hope you ignore the smileys and read them as colon, end-parenthesis)

---

### Post by petri on 2006-10-11
> **fiver22 said:**
> Hi,
   ...
"root(hd0,0) 
   File system type unknown, partition type 0x5
kernel  /boot/vmlinuz -2.6.15-27-386 root=/dev/sda1 ro quiet splash
Error 17: cannot mount selected partition
Press any key to continue"
...
1.Boot to the Ubuntu live CD.
2.sudo grub.
3.at grub prompt enter: "find /boot/grub/stage1"
This returned  "(hd0,2)"
4.enter "root (hd0,2)"
5.enter "setup (hd0)"
6.enter "quit"
7.reboot
...

Error says yours grub is looking for root at (hd0,0) but your grub setup points your root to (hd0,2), that doesn't make sense.

Your **fdisk -l** says root is located to sda3 which is in "grub language" (hd0,2)

Next time you boot edit (with ***e***) the root line > root		**(hd0,0)** to **(hd0,2)** like this > root		**(hd0,2)** you might even need to edit the line **kernel**, not so sure, can't remember :rolleyes: 	> kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/**sda1** ro quiet splash  to **sda3** like this > kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/**sda3** ro quiet splash 

Then boot. After you logged in Ubuntu open terminal and paste this ```
gedit /boot/grub/menu.lst
``` You don't have to read it yet. Now paste this ```
sudo update-grub
``` it works a couple of seconds... then paste this again ```
gedit /boot/grub/menu.lst
``` Now you can compare the old menu.lst and the new one. Now your grub should be updated with same changes as you edited with ***e*** at boot. Close gedit, don't worry you can't save any changes just discard.

It is strange that your grub-install didn't work, it seems that you've done it right. I hope this worked otherwise just ask again and tell us what did you get.

---

### Post by fiver22 on 2006-10-12
I've tried editing "e" at the grub menu but no luck regardless of the edits I try. (edited everything I can think of)

So I'm left with this problem:
(*) unallowcated 114,426.2MB

It's that last entry that I'm focusing on -the one that says:
"(*) unallowcated 114,426.2MB"
that shouldnt be unallowcated -it should be my Linux Data partition.
-anyideas? 
-I so don't want to have to start over -as this partition has all my many GB of music,
-Any other ideas?

---

### Post by petri on 2006-10-12
Boot up with your LiveCD and browse System > Administration > Disks where you can mount the partitions and browse them.

If it still appears that unallowcated 114,426.2MB is gone there is program called Autopsy which helps to recover lost files. There sure are more programs like Autopsy...

---

### Post by Bigbluecat on 2006-10-12
One other thing to try is just to see if the linux kernel still exists. While grub is starting press "c" to get grubs command line interface. It does look as if you should use root hd(0,2). Let's see what grub thinks.

Once there type:

null (hd0,

This will list your partitions and file types. Grub does not recognise NTFS so don't worry if your windows partition shows as type unknown

find /vmlinuz

This will search your drives for the linux kernel and return the location in grub nomenclature.

find /sbin/init 

This is provides useful information.

find /boot/grub/stage1

Take a note of the results and post them back. This should give us all the info we need.

When you are done type:

quit

to exit grub CLI

---

### Post by fiver22 on 2006-10-15
I hate to say this: but I think I'm admitting defeat... I am NOT giving up on the wonderful world of Ubuntu -I'm just admiting defeat on this issue.
   So what I think is that I'm going to lose over a 100GiB of music -I can live with that -I'll get it back eventually.
   What I think must be done is to wipe this whole 250 GiB drive to factory specs, then repartition, install Ubuntu FIRST, then install Windows. 
   I'm not exactly sure how I will do this but I've tried every suggestion in this thread to no avail -so I think it's time to start over.
   I wish I knew what happened.
   If you could keep an eye out for my future posts (fiver22) I would really appreciate it. And I will get Ubuntu running again!
   My next steps are as follows:
1) figure out how to wipe my entire 250GiB HDD
2) figure out how to partition it properly to accept Ubuntu > then Windows.
I have both the regular Ubuntu 6.06 and the Alternate -the Alternate doesn't seem to want to boot 'LIVE' at all -and the regular  (Ubuntu 6.06) disk fails to load a graphical interface. -But I'll figure it out.
Thanks again for your responces.
   STILL LOVE UBUNTU!
Thanks to everyone who tried to help with this issue.
I'm sure that it was solveable but my limited knowledge made things difficult.

[EDIT: I'm gonna give it a day or two before I do anything too drastic -just to get my thoughts in order -so any suggestions would be appreciated.
(This message is SADLY posted from Windows)]

---

### Post by petri on 2006-10-15
1. Always install windows before Ubuntu, but in this case do not install windows att all.

Alternate CD does not have a Live session, it just installs without the graphics. Have you tried to boot the DesktopCD with Safe graphics mode?

If the 100GB data isn't damaged then don't format it! Download another LiveCD try Knoppix och PCLinuxCD. With Knoppix you can install Ubuntu. BTW You can install Ubuntu from Windows. Follow the [link]("https://help.ubuntu.com/community/Installation#head-e87f88f2cc723e9cfbd1ce8698de949d31004d2c") and in advanced section find out all the ways to install Ubuntu.

---

### Post by louieb on 2006-10-15
```
fdisk -l gives:
/dev/sda1 2 889 6713280 5 Extended
/dev/sda2 * 890 15276 108765720 7 HPFS/NTFS
/dev/sda3 151277 16663 10485720 83 Linux
/dev/sda4 16664 16802 1050840 82 Linx Swap/Solaris
/dev/sda5 2 889 6713248+ 7 HPFS/NTFS
```

Unless I am missing something it look like sda1 and sda2 overlap.
I don't know much about sata drives. but if this were a ide drive I would think the partition table is messed up.

---

### Post by petri on 2006-10-15
SATA and IDE should work the same with fdisk. 
On his sda1 beginning is 2 and stop is 889. 
On his sda2 beginning is 890 and stop is 15276 as I see it. 
The lines are pushed together too much I think.

EDIT: I have nonenglish OS (beginning?)

---

