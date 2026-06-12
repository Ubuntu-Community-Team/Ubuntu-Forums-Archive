---
title: "Error 15 : File not found"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by nitinwagale on 2008-04-06
Dear Friends,
                       I am new to Ubuntu. I have installed Ubuntu 7.10 AMD64 bit edition on my computer. It was working fine for the last two weeks. Yesterday, it was updated. After that, i cannot boot into Ubuntu or access it. I get the following message 

Error 15 : File not found

press any key to continue....

After pressing any key, still I am not able to access it.

I read the solutions given in the posts and followed them, but no success. Given below is the output, I received, please see it tell me what to do. 

**My entire Ph.D thesis is on Ubuntu, kindly help me to recover it.**

I am also using Windows XP Professional version, which is installed on C drive. Ubuntu was installed on one half of the D drive. 

C drive has a capacity of 80 GB and D drive has a capacity of 80 GB. On D drive, out of the 80 GB available 40 GB is used by Ubuntu.

The computer configuration is as follows :

AMD Athlon64 X2 Dual-Core 4800+
AUSU M2N8-VMX motherboard (Nvidia GeForce 6600 nForce430)
Transcend DDR II 533 2GB RAM
Seagate Barracuda 7200 RPM 160 GB HDD
Moser Baer DVD writer
IBM E74 Colour Monitor 17"
iBall cabinet
Logitech keyboard & mouse.

The message I received from Ubuntu after following the solutions in the post is as follows :

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf673f673

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sda2            9729       14660    39616290    f  W95 Ext'd (LBA)
/dev/sda3           14661       19457    38531902+  83  Linux
/dev/sda5            9729       14449    37921401    7  HPFS/NTFS
/dev/sda6           14450       14660     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 495 MB, 495582208 bytes
16 heads, 60 sectors/track, 1008 cylinders
Units = cylinders of 960 * 512 = 491520 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      810559     1999631   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(810558, 3, 49)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(1999630, 12, 19)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      175719     2192415   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(175718, 4, 3)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(2192414, 5, 22)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     1947794     3964490   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(1947793, 3, 6)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(3964489, 3, 37)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1     3788778  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(3788777, 9, 36)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,2)
grub> root (hd0,2)
root (hd0,2)
grub> setup (hd0,2)
setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.

I shall be grateful, if someone could help me in this and restore Ubuntu back to normal. I shall be happy if someone could write down the exact command, I have to execute to restore Ubuntu.

Thank you in advance, please help me.

---

### Post by alzie on 2008-04-06
I found a similar problem as your with a solution here : [http://ubuntuforums.org/showthread.php?t=644773](http://ubuntuforums.org/showthread.php?t=644773)

I hope this helps you out

Good luck with your thesis

---

### Post by bumanie on 2008-04-06
Looks as though you need to reinstall grub. Can you supply the output of > sudo gedit /boot/grub/menu.lst

---

### Post by nitinwagale on 2008-04-06


I typed the following :

sudo gedit /boot/grub/menu.lst

A blank file opened. There is nothing in that file.

Please, somebody help me. I am on the verge of having a nervous breakdown.

Thanks in advance

---

### Post by alzie on 2008-04-06
When you typed "sudo gedit /boot/grub/menu.lst " did you enter .lst as lowercase .LST?

I've messed that up before.

I looks like you are using a live disk to use ubuntu right now.  Can you copy your file to a cd or a usb flash drive.  At least that way you should be able to recover you thesis and move it to your xp partition until this problem is resolved.

I hope this helps

---

### Post by coolen on 2008-04-06
I've had this happen a few times, usually after updating my kernel. The scripts to reconfigure GRUB point it to the wrong files.

First, grab a copy of the Super GRUB Disc: [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

You should be able to follow the menu options to boot Gnu/Linux directly (booting normally will take you to your installed GRUB, which is broken). This is assuming you can't boot...your message seems a little unclear on that point...

Once you're in Ubuntu, try to open the menu.lst file. Try doing it the GUI way to make sure you're not misspelling (gksudo nautilus will get you a priveleged window).

If it's still blank, open the terminal. Type this command:

ls -a /boot/grub

Look for any file named menu.lst~ or menu.lst.bak, or anything like that.

Now, whether you have anything in your menu.lst or a backup file, post the contents here.

---

### Post by Tatty on 2008-04-06
If i were you I would try to rescue your Theseis before you do anything else.

Boot into a live CD.  Your hard drive should automount, then find your file and copy it to a USB stick.  If you have another computer i would check that it has copied to the stick correctly before you carry on (it sounds like its a pretty important file).

Then try the above suggestions to get your computer booting again.

---

### Post by bsharp on 2008-04-06
> **Tatty said:**
> If i were you I would try to rescue your Theseis before you do anything else.

Boot into a live CD.  Your hard drive should automount, then find your file and copy it to a USB stick.  If you have another computer i would check that it has copied to the stick correctly before you carry on (it sounds like its a pretty important file).

Then try the above suggestions to get your computer booting again.
+1 Fixing your existing installation is your last priority right now, get your work off first and keep it in a safe place, then you can mess around with fixing/reinstalling.

---

### Post by geezerone on 2008-04-06
Are any of these drives SATA per chance as I got error 15 when installing on a two drive setup with the Ubuntu partition on the SATA drive. I had to physically remove the power from the IDE drive so grub could only be written to the boot drive (SATA). For some reason I have always had problems when SATA drives are installed with Ubuntu and 'grub'.

The 'error 15' msg could be bypassed by changing from hd0 to hd1 in my setup (I think) during the boot process (e to edit) . Then when I updated the kernel grub changed this to the 'error 15' mode again :(

I copied the pertinent part of a post from link above which is similar to that which I carried out:

```
 At the boot prompt, hit "e".
Edit the first line
Change hd(1,0) to hd(0,0)
hit 'b' to boot..
```

HTH

I re-installed (disconnecting IDE drive first) to make the error 15 not return regardless of kernel update in the future.

---

### Post by nitinwagale on 2008-04-08
Dear Friends,
                      Thank you for the help. I am very sorry for the delay in reply. I tried what all you ahd asked me to do, but no success. I also referred to the ubuntu guide but no success.

I have managed to rescue my thesis. A big thank you to you all.
[B]
THANK YOU ![/B]

I also tried Super Grub. I downloaded an image and then burned it to disk. Then I booted from the disk. The menus appeared and I followed the guidelines. In the end, it showed that it ahd embedded 15 files and installed grub. I rebooted and removed the Super Grub CD. The regular boot options appeared. I pressed enter on the Ubuntu 7.10 boot option and I got the following error message:

Error 15 : File not found

Before trying Super Grub, when I started the computer, I could see on the screen the following message :

Grub loading stage etc.

Now, after Super Grub, I do not see the above message.

I am giving the output below, I hope this could help you all in solving my problem.

ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# mkdir /mnt/root
root@ubuntu:~# mount -t ext3 /dev/sda3 /mnt/root
root@ubuntu:~# ls /mnt/root
bin   cdrom  etc   home    lib    lost+found  mnt  proc  sbin  sys  usr
boot  dev    grub  initrd  lib64  media       opt  root  srv   tmp  var
root@ubuntu:~# mount -t ext3 /dev/sda3 /mnt/root/boot
root@ubuntu:~# ls /mnt/root/boot
bin   cdrom  etc   home    lib    lost+found  mnt  proc  sbin  sys  usr
boot  dev    grub  initrd  lib64  media       opt  root  srv   tmp  var

root@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf673f673

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sda2            9729       14660    39616290    f  W95 Ext'd (LBA)
/dev/sda3           14661       19457    38531902+  83  Linux
/dev/sda5            9729       14449    37921401    7  HPFS/NTFS
/dev/sda6           14450       14660     1694826   82  Linux swap / Solaris

I feel very bad as I cannot use Ubuntu. I have a few questions :

1. Is it possible to repair the current Ubuntu 7.10 installation
2. If no, then how do I remove it.
3. If I reinstall Ubuntu 7.10, will it install in the same place or a different one.
4. While reinstalling, will it detect the earlier installation and repair it.

Please help me as you all have done earlier.

Thanks in advance.

---

### Post by coolen on 2008-04-08
My experience with this issue:

The grub update scripts point Grub to a kernel file that doesn't exist. Look at the root of what would normally be your root directory (from a Live CD, if need be). You'll see two relevant files: vmlinuz and initrd.img

On my machine, they're just like that, but the grub update scripts add a version number to the end of them. Find the boot options for Ubuntu in your menu.lst file and make sure they match those found in your root directory.


You've got your thesis, which is the most important thing. Hopefully you can get your favourite OS in the entire world back, too :)

---

### Post by geezerone on 2008-04-08
Sorry to hear of your predicament but glad you retrieved your crucial information. Do you get any Grub menu now or mention of one during boot up or what is displayed?

Like said above, edit your menu here: *sudo gedit* (or nano)  [I]/boot/grub/menu.lst.
[/I]Do you have only one hard disk?If you can do this and post your menu.lst here that may help us.

What did you carry out with the Super Grub disk btw?

I found [** this link** ]("http://ubuntuforums.org/showthread.php?t=297261") which may help too.

---

### Post by nitinwagale on 2008-04-08
Dear Friends,
                      Thank you very much for the help. 

First, about the initrd.img file, I checked it in the root directory. I clicked on it to view the properties, it says that link is broken for initrd.img.

Second, about the menu.lst, it is empty. I mean when it opens there is absolutely nothing in it, it is completely blank.

Thanks in advance.

---

