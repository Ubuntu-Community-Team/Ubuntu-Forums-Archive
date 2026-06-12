---
title: "Help finding dual boot thread"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by YoungPastor on 2007-10-24
I know there's a thread for this somewhere, I just haven't been able to find it. 'Little help. please!

I love my Ubuntu, and I've been using an WinXP virtual machine for my XP desires, but the VM doesn't solve all my problems. I'm going to leave VMware for the moment in favor of a dual boot. How do I add an XP bootable partition to my already Ubuntu system? There are many threads for adding a Ubuntu partition to an XP system, but I need it the other way. So where's the thread for that?

Thanks!

---

### Post by rameshg87 on 2007-10-24
open the file menu.lst of grub

$ sudo vim /boot/grub/menu.lst

add the following lines to the end

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

if the windows exists on the first partition of you primary master harddisk (normally) . OTherwise edit the line
rootnoverify (hd0,0) accordingly. The second 0 is the partition number..as for grub partition numbering starts from 0

---

### Post by YoungPastor on 2007-10-24
I'm not sure I understand what you just said. But you did talk about my windows partition. I don't have one of those just yet.

---

### Post by maybeway36 on 2007-10-24
1. shrink your Ubuntu partition. GParted can do this, Knoppix and Ubuntu live CD both have GParted on them.
2. install Windows.
3. restore GRUB. I don't know how, but just search the forums for "restore GRUB" and something will pop up.

---

### Post by jimod4 on 2007-10-24
1) boot off a live cd with gparted and make enough space for a windows partition. reboot into linux
2) if grub is loaded on the MBR run this command "sudo dd if=/dev/hda of=/boot.lnx bs=512 count=1" without the quotes. save the file boot.lnx to a floopy or usb key or email it to yourself.(/dev/hda assumes an ide harddrive).
3) load xp on your newly created space and let it load the xp bootloader.
4) copy the boot.lnx file to your windows c:\ partition.  assuming it is C:\, if not substitute your winders system partiton.
5) edit your boot.ini with this line "c:\boot.lnx="Linux""

you can boot linux or xp from the xp bootloader.

---

### Post by YoungPastor on 2007-10-24
Thanks for the help, I'm just going to need a little more:

1. "if grub is loaded on the MBR...." How do I know if that's true?
2. what do each of these commands do specifically? I don't want to lose any data, and so I just want to make sure I know what--specifically--I'm doing before I do it.

---

### Post by jimod4 on 2007-10-24
Q> 1. "if grub is loaded on the MBR...." How do I know if that's true?
A> if you don't know where it is loaded its about a 99% chance it is on the MBR.  when you install ubuntu it asks you where to install the bootloader  and gives you the option of MBR or boot partition. MBR is the default.

Q> 2. what do each of these commands do specifically? I don't want to lose any data, and so I just want to make sure I know what--specifically--I'm doing before I do it.
A> the only command you are running is the dd command.  It's hard to explain what it does.  it copys raw data from partitons.  google it.  the parameters if= is infile and of= is outfile.  so you are creating an 512kb file named boot.lnx from the boot partiton /dev/hda.  you could name it anything like ronpaul2008.lnx. 512 is the size of the MBR.

---

