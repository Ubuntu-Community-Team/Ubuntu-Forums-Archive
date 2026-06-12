---
title: "Duel-boot two harddrives, need to access opposite drive."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Blessed_Coffee on 2008-02-25
Hello again,

I'm trying to access a second harddrive that contains an installation of windows XP.  The first one is a SATA drive with Ubuntu 7.10 gusty, and the other one  that contains windows XP is an IDE drive.  I need to use windows to run some software that refuses to operate with wine.  I was able to see, and write in the second drive before windows was installed.  Any ideas?

---

### Post by Duck2006 on 2008-02-25
Post the output from the terminal post the outputs

sudo fdisk -l

If you use the linux drive to boot the system your have to map the windoze drive to boot so it thinks it is the C: drive.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Blessed_Coffee on 2008-02-25
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024599

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9375    75304656   83  Linux
/dev/sda2            9376        9729     2843505    5  Extended
/dev/sda5            9376        9729     2843473+  82  Linux swap / Solaris

Disk /dev/hdc: 45.0 GB, 45020602368 bytes
16 heads, 63 sectors/track, 87233 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x213f213e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       87231    43964392+   7  HPFS/NTFS
```

---

### Post by Duck2006 on 2008-02-25
You will have to edit your menu.lst

gksudo gedit /boot/grub/menu.lst

and add these map line so it looks like this..

title Windoze
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
savedefault
chainloader    +1

---

### Post by Blessed_Coffee on 2008-02-26
No, I think you misunderstood.  I can already boot into windows.  I want to access files off of the windows drive while I am in ubuntu.

---

### Post by gpilkay on 2008-02-26
I have the same setup, except both my drives are IDE.  What I do is go to places-computer- and then I pick the windows drive (listed on mine as 71.1 gig volume but it may be different on yours, I double-click this).  Then I input my sudo password to let it mount.  Before shutting down I unmount it the normal way, sometimes having to give the password again.  This will let you access your files but not run the programs.  To run windows IN Ubuntu you need some sort of virtualization program, such as VirtualBox or the like, with your Windows drive listed in place of the virtual one.  I use it in XP on my laptop to run Ubuntu.  However, be warned that running an existing Windows installation in a VM may cause it to try to de-licence itself as it thinks you've installed it to new hardware.

Hope this works!

---

### Post by Duck2006 on 2008-02-26
> **Blessed_Coffee said:**
> No, I think you misunderstood.  I can already boot into windows.  I want to access files off of the windows drive while I am in ubuntu.


Ok in your package manager search for ntfs-3g and mark it apply and you will be able to read ntfs file systems. Is your win drive mounted?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by thisiam on 2008-02-26
i just dual booted my computer on 1 300GB hard drive. gave Ubuntu 50 GB and windoze 50GB. 200 GB left over i wanted to share with both OS, so i formated the rest with fat 32, as i believe from what i have read if you use NTFS Ubuntu wont be able to read it. and now i have a shared partition that i can read and write to from both windoze and Ubuntu.

---

### Post by Blessed_Coffee on 2008-02-27
Hmm... I still get an error message saying that it is unable to mount the volume. :/

---

### Post by Blessed_Coffee on 2008-03-09
Okay, I got it working.

1) I installed ntfs-3g.

2) I then made the directory to be used as a mount point:

```
mkdir /media/windows
```

3) I then added this line to /etc/fstab:

```
/dev/hdc1 /media/windows ntfs defaults 0 0
```

The drive is located at /dev/hdc1, not /dev/hda1.  I also wanted the mount point to be at /media/windows.

4) I then ran ntfs-3g configuration tool, and checked off "enable write support for internal device."

Now the line I added in /etc/fstab looks like this:

```
/dev/hdc1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

I also had to change some permissions, so I can access the drive without having to be root.  I don't care if ubuntu messes up windoze, because I'll probably have to reinstall it in a few months anyway. :lol:

---

