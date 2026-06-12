---
title: "Windows remove+grub fix?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-30
Hello i have windows on one hdd and anoter one with linux. How to format the windows hdd and fix grub?

---

### Post by aysiu on 2006-09-30
Is Grub not installed to the MBR? Are you currently using Windows' boot loader to dual boot?

**If you're not using Windows' boot loader (i.e., you're using Grub)**, delete the Windows partition with GParted ```
sudo aptitude update && sudo aptitude install gparted gksu
gksudo gparted
``` Make sure to unmount it before reformatting it.

Then mount the newly created Ext3 partition:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Finally remove Windows from the Grub menu: ```
sudo nano -B /boot/grub/menu.lst
``` Find the Windows entry and delete those lines (Control-K). Then save (Control-X, Y, Enter).

**If you *are* using Windows' boot loader**, just install Grub to the MBR:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by wieman01 on 2006-09-30
You can format a harddisk by booting the Live CD and using GParted which is a partition manager that comes with the CD.

As for GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

But perhaps let us know what you are trying to achieve, we can help. Simply upload a screenshot of your partitions (GParted) and tell us which partition you plan to remove or keep.

---

### Post by haxer on 2006-09-30
Hmm.. im using 2 different hdds one with linux and one with windows and i dont got any live cd havent used it ever ... im using mbr i think becouse i installed windows first :S and i only need to format and remove grub or?

---

### Post by aysiu on 2006-09-30
A lot faster than uploading a screenshot of your partitions, just post the output of this command: ```
sudo fdisk -l
``` That's a lowercase *L*, by the way, not an uppercase *i* or the number *one*.

---

### Post by aysiu on 2006-09-30
> **haxer said:**
> Hmm.. im using 2 different hdds one with linux and one with windows and i dont got any live cd havent used it ever ... im using mbr i think becouse i installed windows first :S and i only need to format and remove grub or?
If you installed Windows first and Ubuntu second and didn't manually edit the boot.ini file, then you can follow the first approach and you do **not** need to remove Grub or reinstall Grub--just remove Windows.

---

### Post by haxer on 2006-09-30
But ive got grub dont i need to uninstall grub then after removing windows?

and heres the output 

oem@haxer:~$ sudo fdisk -l
Password:

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       23944   192330148+  83  Linux
/dev/hdb2           23945       24321     3028252+   5  Extended
/dev/hdb5           23945       24321     3028221   82  Linux swap / Solaris
oem@haxer:~$

---

### Post by xtacocorex on 2006-09-30
> **aysiu said:**
> []("http://www.psychocats.net/ubuntu/mountlinux") Finally remove Windows from the Grub menu: ```
sudo nano -B /etc/X11/xorg.conf
```

This command is wrong, you have it editing xorg.conf.

It should be:
```
sudo nano -b /boot/grub/menu.lst
```

---

### Post by aysiu on 2006-09-30
[quote=xtacocorex]This command is wrong, you have it editing xorg.conf.[/quote] Yeah, I just fixed it. [quote=haxer]But ive got grub dont i need to uninstall grub then after removing windows?[/quote] No. Grub isn't just for dual-booting. It's for booting in general. If you remove Grub, you won't be able to boot into Ubuntu at all. Just remove Windows from the /boot/grub/menu.lst file.

---

### Post by haxer on 2006-09-30
I dont know shit please explain again and type it all in one replay please or i dont got any idea please :-k

---

### Post by wieman01 on 2006-09-30
> **haxer said:**
> But ive got grub dont i need to uninstall grub then after removing windows?

and heres the output 

oem@haxer:~$ sudo fdisk -l
Password:

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       23944   192330148+  83  Linux
/dev/hdb2           23945       24321     3028252+   5  Extended
/dev/hdb5           23945       24321     3028221   82  Linux swap / Solaris
oem@haxer:~$
Great. So what your target system/setup?

---

### Post by haxer on 2006-09-30
What? :S

---

### Post by wieman01 on 2006-09-30
What exactly are you trying to achieve? Simply format hda1 and thus ditching Windows?

---

### Post by aysiu on 2006-09-30
> **haxer said:**
> I dont know shit please explain again and type it all in one replay please or i dont got any idea please :-k
Step 1: **Delete the Windows partition with GParted**
Paste in this code to install GParted. It's a partition editor that can delete, resize, and reformat partitions: ```
sudo umount /dev/hda1
sudo aptitude update && sudo aptitude install gparted gksu
gksudo gparted
``` In GParted, I believe you can simply right-click /dev/hda1 and choose to delete it. Then you can reformat it as Ext3.

Step 2: **Mount the newly created Ext3 partition**
Follow the instructions in this link:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Step 3: **Finally remove Windows from the Grub menu** Paste this command into the terminal: ```
sudo nano -B /boot/grub/menu.lst
``` Find the Windows entry and delete those lines (Control-K). The lines you want to delete will probably look something like this: ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

``` Delete them; then save (Control-X, Y, Enter).

---

### Post by haxer on 2006-09-30
I want to remove windows becuse i need that extra hdd and i want to know how and if i need to remove grub and then how im trying to kick me free from windows :)

---

### Post by haxer on 2006-09-30
That from [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)  sound hard :(

---

### Post by aysiu on 2006-09-30
> **haxer said:**
> I want to remove windows becuse i need that extra hdd and i want to know how and if i need to remove grub and then how im trying to kick me free from windows :) You do not need to remove Grub.

In fact, if you remove Grub, you won't be able to boot Ubuntu any more.

You do, however, have to edit the /boot/grub/menu.lst file--the instructions for doing so I gave in Step 3 of my last post.

> **haxer said:**
> That from [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)  sound hard :( I have screenshots. What else can I do to make it easier?

What exactly seems daunting to you? I'm not trying to sound mean about it--I actually want to know what specific things seem difficult. For commands (the green text), just highlight them and paste them in the terminal. You've seemed to be doing a great job with pasting things into the terminal so far.

---

### Post by haxer on 2006-09-30
Ok ill try if not im logging in to my brothers computer and post to you for help :)

---

### Post by haxer on 2006-09-30
Ok now i get this 
oem@haxer:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

WTF should i do now?

---

### Post by aysiu on 2006-09-30
Looks as if I forgot a step.

In addition to removing Windows from the /boot/grub/menu.lst file, we'll also have to remove it from /etc/fstab, too.

```
sudo nano -B /etc/fstab
``` Delete (Control-K) the line that has /dev/hda1 in it. Then save (Control-X, Y, Enter). ```
sudo mount -a
``` should work now.

---

### Post by haxer on 2006-09-30
Ok now when i should be finished i get this when i go to computer- and double click on the hdd
 error: device /dev/hda1 is not removable

error: could not execute pmount

---

### Post by aysiu on 2006-09-30
Can you post the output of these two commands? ```
sudo fdisk -l
cat /etc/fstab
``` If you've reformatted Windows, *sudo fdisk -l* should now give a different output.

---

### Post by devinkray on 2006-10-03
What about merging the new ex3 partition to the current one? Meaning, after you have remove the windows partition/formatted/ and re-mounted.

---

### Post by jhaquo on 2006-10-31
> **devinkray said:**
> What about merging the new ex3 partition to the current one? Meaning, after you have remove the windows partition/formatted/ and re-mounted.


i would love to know that too please

---

