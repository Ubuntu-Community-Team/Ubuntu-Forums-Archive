---
title: "No longer able to access my other hard drives"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by ICEcoffee on 2007-11-14
Hi all,

Since downloading KDE from within the Ubuntu Synaptic manager, things were fine until I was informed on the forums, I was still running in the Ubuntu sessions, and that is why I had the appearance of Gnome  desktop and not KDE. After switching though to KDE session at login, I can no longer access my files on the windows hard drives. When running in the Gnome session manager, and clicking on the drive Icon I wanted within the file manager, I was the asked for my password. Under KDE session I just get refused access, and not asked for any password.

An error code id given with a message, it os: Hal-storage-fixed-mount-all-options refused uid 1000.

How do I access my drives now? or can I only do this in the gnome session manager?

---

### Post by taurus on 2007-11-14
Why not add an entry in /etc/fstab for that windows partition so it would be mounted automatically each time you boot whether you will use Gnome or KDE.

Post the outputs of these commands here.

```
sudo fdisk -l <-- Lower case letter l, not number 1.
cat /etc/fstab
```

---

### Post by knutschr on 2007-11-14
This is a silly bug in Kubuntu 7.10
The reason is that your other partitions are set to be owned by root.

sudo dolphin

I think you then can open your Win partition.

---

### Post by ICEcoffee on 2007-11-14
knutchr,

Thanks for your advice, but it didn't work. Below is the output from the command line/terminal:

briand@Ubuntu710:~$ sudo dolphin
Error: "/var/tmp/kdecache-briand" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-briand" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-briand" is owned by uid 1000 instead of uid 0.

Any other ideas?

---

### Post by knutschr on 2007-11-15
When you start PC and shall choose to start Kubuntu or Win, see what drive Win is. (hda1..)
Start Kubuntu.
[PHP]
sudo chown briand /media/hda1
sudo dolphin
[/PHP]

---

### Post by olwe on 2007-11-18
I went into the System Settings, Advanced tab, Disk and File Systems, and there I was able to fool around until I got my /dev/sda2 to mount onto /media/sda2 and get the green light "enabled." However, following knutscher's advice,  the dolphin install now has taken over from konqueror file manager and gives me this error when I start it:

Will not save configuration.
Configuration file "/home/olwe/.kde/share/config/d3lphinrc" not writable.
Please contact your system administrator.

It also gives this error when I kill it:

Unable to save bookmarks in /home/olwe/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.

...which is bogus.

Any further thoughts out there?

---

### Post by fabiomb on 2007-11-18
in KDE is even easer to configure the different partitions, you only must to go (via menu) to the system preferences app, then go to the advanced options and there to hard drive item.

DO NOT EDIT FSTAB IF YOU DON'T KNOW WHAT IT IS.

in KDE you can configure all of this without use a terminal, if you edit wrong the fstab file you will have a lot of problems.

---

### Post by jrslv on 2008-01-13
I had the same problem - it is a privilege problem. When you click on the harddrive and it gives you this error - Just click on the "Open as root" at the right side of the Dolphine and it all will work fine.

Jaroslav

---

### Post by visionthing on 2008-02-09
Anyone found a solution to this? It only happens for me using Kubuntu not when I load Ubuntu Gnome.

---

### Post by wuxarn on 2008-02-10
> **visionthing said:**
> Anyone found a solution to this? It only happens for me using Kubuntu not when I load Ubuntu Gnome.
Yeah, you just do as jrslv says, klick open as root in dolphin, go to your /media folder, rightclick the partition ---> "Mount" and you're done.

---

### Post by CrazyArcher on 2008-02-14
> **wuxarn said:**
> > It only happens for me using Kubuntu not when I load Ubuntu Gnome.Yeah, you just do as jrslv says, klick open as root in dolphin, go to your /media folder, rightclick the partition ---> "Mount" and you're done.

I have exactly the same problem... I tried doing that through dolphin, but got the same error msg again. 
Here's my  'fdisk -l' output:```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b9b4b9b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/hda2            3188        9729    52548615    f  W95 Ext'd (LBA)
/dev/hda5            3188        6374    25599546    7  HPFS/NTFS
/dev/hda6            6375        9729    26949006    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29e429e3

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4660    37431418+  83  Linux
/dev/hdb2            4661        4865     1646662+   5  Extended
/dev/hdb5            4661        4865     1646631   82  Linux swap / Solaris
```
Specifically, I'd like to access partitions marked hda5 and 6. I'm not familiar with Linux commands, and I'll be glad if someone could help me with that, 

PS. BTW, is there a comprehensive reference list of all the console commands with all the paramters?

---

### Post by CrazyArcher on 2008-02-15
Both problems solved, now I'm cool :)

---

### Post by anegro on 2008-02-17
Hi!

How did you solved the problem?
I have the same problem...:confused:

---

### Post by mathonwy on 2008-03-08
Hi, i get the same error message, but when i go to Storage Media in Dolphin, the only option on the right hand side is mount, and so i cannot click 'open as root'

any ideas??     Thanks

---

