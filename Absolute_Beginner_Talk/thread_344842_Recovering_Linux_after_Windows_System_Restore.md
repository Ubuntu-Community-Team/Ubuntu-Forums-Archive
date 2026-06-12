---
title: "Recovering Linux after Windows System Restore"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Monkalou on 2007-01-23
Hello all,

I've used Ubuntu Edgy for about a month... got it all setup with recognizing screen, video cards, installing new apps, etc.  

I was dual booting XP and Linux, when XP had a hal.dll error.  Windows offered to restore the system and I agreed (it was late at night, I was tired, etc.)  Now Windows sort of works and my boot manager won't recognize Linux.  I was using Acronis OS Loader as a boot manager, but I'm willing to switch to grub.  I've tried booting with the Ubuntu CD, but it stalls (tried multiple times).  (I've since run the CD through its integrity checks and it comes out fine.)  How do I install grub when I have no access to the command line and Ubuntu CD stalls?  

Thanks

---

### Post by mikewhatever on 2007-01-23
Since you can't install GRUB, why not reinstall Acronis loader?

---

### Post by hyper_ch on 2007-01-23
the ubuntu cd offers a check of the cd integrity... very likely the cd is damaged... if you have a 700mb rewritable cd, just burn ubuntu again on that one and give it a try :)

---

### Post by Monkalou on 2007-01-23
I ran the integrity check on the Ubuntu CD, it came out with no checksum errors.  Umm, just tried to remove and reinstall acronis disk director... now it locks at Acronis OS Loader (which supposedly was uninstalled and not there anymore) and I can't load _any_ OS.  I'm talking to Acronis now, if they can fix the Acronis problems, maybe then I can get working on OS specific ones again. 

Thanks

---

### Post by bodhi.zazen on 2007-01-23
If the Ubuntu CD will not boot, how did you install Edgy ???

You can install grub from almost any Linux Live CD

Follow these directions to install grub:

assuming your Ubutnu root partition is /dev/hda2, you will need to adapt otherwise

From any live CD:

either su to become root or sudo (as below):

```
sudo grub
root (hd0,1)
setup (hd0)
quit
```

Reboot

---

### Post by Monkalou on 2007-01-23
Okay, I got the Linux boot CD to work.  (I don't know why it hung repeatedly before,  I really hope my DVD drive isn't getting flaky.)  Anyway, trying to get grub to install...

Tried the following

grub> root (hd0,2)
Error 21: Selected disk does not exist

grub> root (hd2,2)
Error 21: Selected disk does not exist
 - tried hd2 because I checked BIOS and my hard drive is listed as Third Channel Device 0.

Ran fdisk to see where the partitions are, etc.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         982     7885048+   c  W95 FAT32 (LBA)
/dev/sda2   *         982       17233   130538520    7  HPFS/NTFS  -- Windows
/dev/sda3           17233       23942    53890515   83  Linux         -- Linux
/dev/sda4           23943       30401    51881445    5  Extended
/dev/sda5           27767       30401    21160408+  83  Linux
/dev/sda6           23943       27766    30716217   82  Linux swap / Solaris

How could I redo your instructions to work with my system?

Thanks,
Jason

---

### Post by bodhi.zazen on 2007-01-23
Which partition is your ubuntu root partition ?

Did you run grub as root (sudo grub) ?

At the grub prompt:

```
find /boot/grub/stage1
```

---

### Post by Monkalou on 2007-01-23
My root partition is /dev/sda3.  And I did use sudo.

---

### Post by bodhi.zazen on 2007-01-23
Sorry, I edited my post while you were typing.

What do you get with the find command ?

---

### Post by Monkalou on 2007-01-24
Ok, I thought I had run sudo grub before.  I just ran it again and root works, but setup doesn't seem to work.

grub> root (hd0,2)

grub> find /boot/grub/stage1
 (hd0,2)

grub> setup(hd0)

Error 27: Unrecognized command

---

### Post by bodhi.zazen on 2007-01-24
Small typo:

setup (hd0)

with a space between setup and (hd0) ;)

---

### Post by Monkalou on 2007-01-24
ok, I'll try rebooting.

---

### Post by Monkalou on 2007-01-24
Yay, I'm back in Linux.  I can't thank you enough!!

---

### Post by bodhi.zazen on 2007-01-24
LOL, you are most welcome.

See grub is not so hard ;)

Dare I ask, can you boot windows ?

---

### Post by Monkalou on 2007-01-24
I just checked and I can get into Windows.

Thanks again.

---

