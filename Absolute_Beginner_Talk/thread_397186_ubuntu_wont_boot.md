---
title: "ubuntu wont boot"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by uric on 2007-03-30
Hi, 

I have a problem, ubuntu wont boot.

I was trying to install windows on a partition I had reserved, but I it didnt want to install, I got a message that no partition had the right filesystem, and it could'nt make one for some reason, even though I tried making partition both ntfs and just unallocated space with livecd. I had saved space in front of the ubuntu partitions, so it would be C: drive on windows. 

Well anyway it didnt work and now I cant boot. 

I have tried following instructions on how to activate grub. I quote seshomaru samma instructions from this thread. 

[http://www.ubuntuforums.org/showthread.php?t=396889&highlight=find+boot%2Fgrub%2F]("http://www.ubuntuforums.org/showthread.php?t=396889&highlight=find+boot%2Fgrub%2F")

> 
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal.

3. Type "sudo grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD."


Heres what I get
```

grub> find /boot/grub/stage1
 (hd1,2)

grub> root (hd1,2)

grub> setup (hd1,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> quit

```

This is how my hd is partitioned.

sda3 is /
sda4 is /swap
sda5 is /home
sda6 is /usr 

I would appreciate If someone could help, guide me to make  ubuntu boot again.

Thanks in advance!

---

### Post by richbarna on 2007-03-30
[COLOR=Black]My guess is that you haven't used an extended partiton. Or, you have and you are trying to install Windows inside it.

Your drive should look like this :-[/COLOR] 

| WinXp |[COLOR=Blue]||[/COLOR] /root [COLOR=Black]| /Home | /usr | swap |[COLOR=Blue]||

[COLOR=Black]The blue lines indicate the start and end of the Extended partition, we have to use an EXT partition as the maximum is 4 on our harddrives, however you can place as many as you want "inside"[/COLOR] [COLOR=Black]an Ext partition

Check out :-
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
[/COLOR][/COLOR][/COLOR]

---

### Post by uric on 2007-03-30
here is a screenshot from gparted

[IMG]http://ubuntuforums.org/g/images/255299/large/1_GParted.png[/IMG]

any idea how I get ubuntu to boot again? Im running livecd now

*EDIT*

Just wanted to add that ubuntu has been working fine, until I messed around with win setup.

---

### Post by confused57 on 2007-03-30
From the live cd, open a terminal, post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by uric on 2007-03-30
ok, here goes...

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            4503        8462    31808700    5  Extended
/dev/sda3            8463        8778     2538270   83  Linux
/dev/sda4            8779        9039     2096482+  82  Linux swap / Solaris
/dev/sda5            4503        5832    10683193+  83  Linux
/dev/sda6            5833        8462    21125443+  83  Linux

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30515   245111706    5  Extended
/dev/hdb5               1        1343    10787584+  83  Linux
/dev/hdb6            1344       29115   223078558+  83  Linux
/dev/hdb7           29116       30515    11245468+   b  W95 FAT32
ubuntu@ubuntu:~$ 


```

---

### Post by confused57 on 2007-03-30
Have you tried setting up grub on (hd0)?
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by uric on 2007-03-30
I checked my bios and somehow the booting order of my harddrives had changed. So I think I have been tinkering with grub when it wasnt needed, and now its all messed up.

Anyway I changed back and booted up the systen, grub starts, but  I get error 22: No such partition. 

after working grub and editing menu.lst I have gotten ubuntu to boot my root system using the "boot from first harddrive" on livecd with these settings in menu.lst.

```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,2)
kernel	       /boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet
boot

```

The thing is it still refuses to boot with out the livecd "boot from harddrive". If I do I still get the error 22, and I if I press (B) for boot in grub menu i get error 18:

*edit*
I did try hd0, its my other disk and this is what says in /boot/grub/device.map

(hd0)	/dev/hdb
(hd1)	/dev/sda

---

### Post by confused57 on 2007-03-30
Do you get a grub menu when you boot first to your hdb drive?

or try booting first to your sda drive, at the grub menu, highlight your Ubuntu entry, press "e" to edit, then change root to (hd0,2), then press "b" to boot...post back if this works, this change is only temporary.

Added:  If you don't get a grub menu booting first to your SATA drive, you could try "setup (hd1)"...just make sure when you do this that your hdb is set to boot first in bios, and your SATA 2nd...after setting up grub on your SATA mbr, then change the bios boot order SATA first, then IDE drive.

Another possibility for getting Window's install to see the unallocated space is to maybe format it FAT32 using the live cd...the live cd is unable to make a NTFS partition, Window's is natively unable to recognize an ext3 filesystem...this "may" be the problem with your Window's install attempt?

---

### Post by uric on 2007-03-30
ok, I changed the boot so it is first hdb, and it works! ubuntu starts! :)

I dont understand why, but Im very happy its back up.

Thank you confused57 for helping me!

---

### Post by confused57 on 2007-03-30
> **uric said:**
> ok, I changed the boot so it is first hdb, and it works! ubuntu starts! :)

I dont understand why, but Im very happy its back up.

Thank you confused57 for helping me!
Good job getting it working...actually, it's pretty easy to explain why.  Evidently, you had your IDE drive set to boot before your SATA drive in bios when you install Ubuntu...that's why your device. map showed "(hd0) /dev/hdb...(hd1) /dev/sda".  When grub is installed it uses your bios hard drive boot order to determine the order it assigns the drives.
Your Ubuntu root ([COLOR="Red"]hd1[/COLOR],[COLOR="Blue"]2[/COLOR]) is the [COLOR="Red"]2nd hard drive[/COLOR], [COLOR="Blue"]3rd[/COLOR] partition.../dev/sda3(hd1)

---

