---
title: "disable dual boot"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by ramlax13 on 2007-11-30
So I just installed Ubuntu on an external usb hard drive.  I have windows xp installed on my internal hard drive on my laptop.  When I start up my laptop it comes up with the boot menu, which seems to be prompted by Ubuntu.  When I disconnect the usb hard drive though, I am not brought to a boot screen but I receive instead an error message. Even if I go into the one time boot menu and select internal hard drive I receive the same problem.  Could someone tell me how to fix this, or how to make Windows boot when the external is not connected.  Thanks

---

### Post by quandary on 2007-11-30
Yes, no problem i had the same problem. You installed grub on the wrong drive.

You have to get Grub out of the MBR (Master Boot Record)
See:
[http://ubuntuforums.org/showthread.php?t=576648](http://ubuntuforums.org/showthread.php?t=576648)

---

### Post by ramlax13 on 2007-11-30
Could I simply get rid of Ubuntu, like repartition the drive or uninstall somehow and then reinstall with the GRUB in the right drive?

---

### Post by quandary on 2007-11-30
> **ramlax13 said:**
> Could I simply get rid of Ubuntu, like repartition the drive or uninstall somehow and then reinstall with the GRUB in the right drive?
Yes. You don't have to uninstall anyway.
 If you install it again to the same partition, your old Ubuntu installation get's formated (erased) automatically. 

But you have to reinstate the Windows MBR.
If you install Ubuntu again, be sure to click on the advanced button and change the grub location...

---

### Post by rsambuca on 2007-11-30
Quandary is correct.  You can achieve what you want without re-installing any Operating Systems.  If you want to dual boot, but only use the grub menu when the external drive is plugged in, then you have to make sure of three things:

1.  Restore your internal drives mbr to the XP.
2.  Re-setup grub to the external drive
3.  Set your computer's BIOS to boot from external USB drive first.  Then it will boot from it if it is plugged in, but will go to the next boot device if the external drive is not plugged in.

To Restore your internal drive's mbr:

Two methods:  Use your XP installation discs and run the command 'fixmbr' from the recovery mode.  The other option is to use your existing Ubuntu installation.  Install the package ms-sys (sudo apt-get install ms-sys).  Then run the following command to fix the mbr:  ms-sys -m /dev/hda (although your drive may not be /dev/hda, it might be /dev/sda).

2.  Grub to the external drive:  From your existing Ubuntu OS:  open a terminal and run the command 'sudo grub'.  At the grub prompt, type:  find /boot/grub/stage2.  It will give you a location in the form (hd1,0).  Whatever location it gives you, use that location for the next command.  Type:  root (hd1,0).  You will replace the (hd1,0) part with what your system tells you.  Then, type: setup (hd1,0).  Then type 'quit' to exit.

---

### Post by quandary on 2007-11-30
> **rsambuca said:**
> 
 At the grub prompt, type:  find /boot/grub/stage2.  It will give you a location in the form (hd1,0).  Whatever location it gives you, use that location for the next command.  Type:  root (hd1,0).  You will replace the (hd1,0) part with what your system tells you.  Then, type: setup (hd1,0).  Then type 'quit' to exit.

Yea true, you don't even have to reinstall Ubuntu ;-)
ms-sys, didn't know that. That's a good one, two flies with one clap, a paradise for a lazy bone like me !

---

### Post by ramlax13 on 2007-12-01
Ok so I got it to boot Windows without the external.  But when I have the external in, it brings up the Ubuntu boot loader, and when I select Ubuntu, I get an error 17, cannot mount partition.

Any suggestions?

---

### Post by meierfra on 2007-12-01
You need to edit  /boot/grub/menu.lst.  You can check out Post 10 in  the following thread for an example how to do it: [http://ubuntuforums.org/showthread.php?t=628951#10]("http://ubuntuforums.org/showthread.php?t=628951#10")

You only need to do Step 1. You did Step 2 and 3 already.   But  you will have to use the Life CD and mount the Ubuntu partition.

If you need further help let me know and post the output of "sudo fdisk -l"

---

### Post by ramlax13 on 2007-12-02
ok so I followed the steps to go edit the menu.lst, and there was nothing in the file.  Here is the output of the sudo fdisk-l command

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14c214c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3187    25599546   83  Linux
/dev/sdb2            3188        3315     1028160   82  Linux swap / Solaris
/dev/sdb3            3316       60801   461756295    f  W95 Ext'd (LBA)
/dev/sdb5            3316       60801   461756263+   7  HPFS/NTFS

---

### Post by quandary on 2007-12-02
> **ramlax13 said:**
> 
ok so I followed the steps to go edit the menu.lst, and there was nothing in the file.  


That's not possible, you wouldn't have any boot options otherwise.
You probably have mistyped, or you were not on the Ubuntu drive that is on your hard disk, but in the RAM drive of the Live CD...

If you use the live cd, you have to go to the respective drive.
On the command line, type:
cd /media/YOUR_MOUNT_NAME_HERE/boot/grub
then type: sudo gedit menu.lst


Grub cannot start your XP, because it has the wrong drive number assigned in menu.lst.
If you would have read my thread, i described how to solve exactly your problem:
[http://ubuntuforums.org/showthread.php?t=576648](http://ubuntuforums.org/showthread.php?t=576648)

You can also change that from the grub start menu with the map option, but that's way unclean.

---

### Post by ramlax13 on 2007-12-02
no its not having a problem booting xp, I can boot xp fine.  I cannot boot Ubuntu from grub.

---

### Post by meierfra on 2007-12-02
From the LiveCD  its is just a little bit more work

Open a terminal (Applications->Accessories->Terminal)

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu
cd /ubuntu/boot/grub
sudo cp menu.lst menu.lst.backup
gksudo  gedit  menu.lst

```
change

"#groot (hd1,0)" to "#groot (hd0,0)"

change all

"root (hd1,0)" to "root (hd0,0)"

Add this to the end

title  Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

(if you already had a windows item remove it)


Save and close the file.




Reboot with the ubuntu drive first in the boot order in the bios.

---

### Post by quandary on 2007-12-02
> **ramlax13 said:**
> 
no its not having a problem booting xp, I can boot xp fine.  I cannot boot Ubuntu from grub.


yea, sorry, i meant ubuntu. but it's the same problem. the above does the job, too, but it's way more complicated

---

### Post by meierfra on 2007-12-02
I edited my instruction. (sudo update-grub  won't work on the LiveCD unless you chainroot into the ubuntu partition)


Let me know if you already tried the faulty instruction. You would have to add a step to undo the damage. (Edit: Actually "sudo update-grub" does not cause any damages. It just produces an error messages without doing anything)

---

### Post by ramlax13 on 2007-12-02
I did try the faulty instructions.

---

### Post by meierfra on 2007-12-02
Sorry about that.  

Boot from the  LiveCD.

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb1 /ubuntu
sudo mount -t proc none /ubuntu/proc
sudo mount -o bind /dev /ubuntu/dev
sudo chroot /ubuntu
sudo update-grub
```


This assumes that you didn't change "menu.lst" since you followed my instruction. The important part is that you have "#groot (hd0,0)" in menu.lst.

For troubleshooting: Before you reboot post the whole content of the terminal.

---

### Post by rsambuca on 2007-12-02
> **meierfra said:**
> This assumes that you did'nt change "menu.lst" since you followed my instruction. The important part is that you have "#groot (hd0,0)" in menu.lst.

For troubleshooting: Before you reboot post the whole content of the terminal.

Are you sure about this?  Won't that incorrectly set the root as the main internal drive?

---

### Post by meierfra on 2007-12-02
```
Ae you sure about this?
```
Yes
```
 Won't that incorrectly set the root as the main internal drive?
```

No. During boot-up Grub sees the hard drives in boot-order.  So if you boot from the ubuntu drive, (hd0) will be the ubuntu drive.

---

### Post by ramlax13 on 2007-12-02
Thanks for your help, that seemed to have worked, and I can boot either operating system now.

---

### Post by meierfra on 2007-12-03
> Thanks for your help, 

Your are welcome. Glad to be of help.  Sorry for initially faulty instruction. This was  the first time  instructed someone to do this from the LIveCD

---

### Post by rsambuca on 2007-12-03
Good job.  Thanks for the info meierfra, I have learned a lot as well here.

---

