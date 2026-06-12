---
title: "Installing problem"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by tkafik on 2007-10-04
Yesterday I tried to install ubuntu.
The install was completed without problem but when I reboot the computer I see only Windows and the partition of ubuntu deleted.
what can I do?

---

### Post by jrev on 2007-10-04
the ubuntu partition didn't delete by itself

Was there a partitioning made before the installation (by gparted live CD) for example ?
It's always simpler to make th partitioning before the actual installation procedure.

Which release did you try to install ? Dapper ? feisty ?

---

### Post by tdrusk on 2007-10-04
Did you partiton the hard drive for windows and ubuntu?

Did you click install when you loaded the live cd?

---

### Post by tkafik on 2007-10-04
I used live CD
and I have 2 hard disk: one for ubuntu and one for linux.
The computer doesnt read the ubuntu's hard disk.

---

### Post by d_iane1954 on 2007-10-04
> **tkafik said:**
> I used live CD
and I have 2 hard disk: one for ubuntu and one for linux.
The computer doesnt read the ubuntu's hard disk.

would your second hard disc happen to be a external drive?if it is you have to go to your bios screen to switch op systems.

---

### Post by tkafik on 2007-10-04
what meaning external driver?

---

### Post by tkafik on 2007-10-04
someone said that I need to configure the grub from the live cd.
Can it work?

---

### Post by d_iane1954 on 2007-10-04
is your second drive a external (hooked up through a usb connection?

---

### Post by tkafik on 2007-10-04
No.

---

### Post by tdrusk on 2007-10-04
Is the harddrive in your computer, or outside of it (like though usb)?

---

### Post by tkafik on 2007-10-04
In, no external by usb.
it's into the computer

---

### Post by mlentink on 2007-10-04
So what is the configuration of that computer? If I understand you correctly, you have:
drive 1 (internal) : Windows (version?)
drive 2 (internal) : unreadable
Is that correct?

---

### Post by d_iane1954 on 2007-10-04
> **tkafik said:**
> No.

sorry tkafik not really sure how to help you at this point have only installed and ran ubuntu ultimate gamers on a single hd and have ran a duel boot system with windows and ubuntu 7.04 on the same drive.

---

### Post by tkafik on 2007-10-04
correct.
I have windows XP.
The second driver doesnt appear at "my computer" on windows.
It possible that i succsed to install the ubuntu but how i active ubuntu?

---

### Post by mlentink on 2007-10-04
You could find out by booting from the Ubuntu LiveCD. Do not install (yet) but if you have installed it previously you should be able to see it. 
You could start up terminal and type (or copy and paste)
```
sudo fdisk -l
``` letter L, not 1

and post the results here

---

### Post by tkafik on 2007-10-04
So what can I do?

---

### Post by mlentink on 2007-10-04
Get your Ubuntu LiveCD
Boot from it
Go Applications > Accessories> Terminal and open it
type:
```
sudo fdisk -l
```
Mark the output of that command and copy it
Paste the outcome of the command in a new post here

---

### Post by tkafik on 2007-10-04
Now the live cd give me error message.

---

### Post by mlentink on 2007-10-04
What does it tell you? What is the error message? Please help us help you by telling as much as possible.

---

### Post by tkafik on 2007-10-04
ok i wrote "sudo fdisk -l"
and this the result:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2551    20490876    7  HPFS/NTFS
/dev/sda2            2552       20023   140343840    f  W95 Ext'd (LBA)
/dev/sda5            2552       20023   140343808+   7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9331    74951226   83  Linux
/dev/hdc2            9332        9729     3196935    5  Extended
/dev/hdc5            9332        9729     3196903+  82  Linux swap / Solaris


what the meaning?
what I need to do now?

---

### Post by mlentink on 2007-10-04
Ok. I have to go now for a couple of hours. 
A linux distro, most probably Ubuntu got installed on your second drive, so it's there.
Two questions:
1. Was the first drive attached, connected, when you installed Ubuntu?
2. When you restart your machine, does it present you with a menu of operating systems to boot?

---

### Post by tkafik on 2007-10-04
1. Yes
2. No

 i installed grub and this dont appear again.

---

### Post by tkafik on 2007-10-04
What can I do now after I installed grub?

---

