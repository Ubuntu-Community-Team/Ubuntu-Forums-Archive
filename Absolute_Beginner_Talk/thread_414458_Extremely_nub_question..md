---
title: "Extremely nub question."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-04-19
When I boot into Ubuntu what folder do I go to find my windows XP folders.
There is some stuff I can't delete on Windows and was wondering if I could delete it with Ubuntu.

---

### Post by dangerpl on 2007-04-19
sda1 in media folder which is located in your root folder. If you have only two partitions that is

---

### Post by Comzee on 2007-04-19
I have three. 1gb for Linux-swap, 10gb for EXT3 and 68 for NTFS. Does that change anything.

---

### Post by dangerpl on 2007-04-19
No, go to the media folder and tell me what's in there

---

### Post by Pobega on 2007-04-19
Which partition of your hard drive is Windows located on?

```
sudo fdisk -l
```

The above command will run a check on all of your removable drivers, Under System it should say something like "Windows" or "NTFS" (I've never used Windows before so I don't know exactly, sorry), and that would be your Windows partition.

Do you want rw access to Windows or just read? I think read should work out of the box, but to get r/w access you'll need a package (ntfs-3g in Debian's repositories, not sure about Ubuntu), and mount it using the mount command.

```
mount -t ntfs /dev/sda1 /mnt
```

And you can find all of your Windows documents in the /mnt folder.

---

### Post by dunedust on 2007-04-19
you will have to mount your windows partition for that

If the partition uses a FAT format  then use this command line

[I] sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000[/I]

assuming that /dev/hda1 is the location of your windows partition 
you should find your partition under  /media/windows



If the partition uses NTFS format use this command line

[I]sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222[/I]

youll find the partition mounted under /media/windows


the NTFS partition will be mounted as read only 
the FAT partition will have read/write permissions

---

### Post by Comzee on 2007-04-19
Ok when I go into my root folder I don't see anything.

This is my partition setup.

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8414    67585423+   7  HPFS/NTFS
/dev/hda2            8415        8545     1052257+  82  Linux swap / Solaris
/dev/hda3            8546        9729     9510480   83  Linux

And when I used this code "mount -t ntfs /dev/sda1 /mnt" it said only root can do that???

---

### Post by bobplano on 2007-04-19
> **Comzee said:**
> 
And when I used this code "mount -t ntfs /dev/sda1 /mnt" it said only root can do that???

that just means you need to use sudo

---

### Post by Comzee on 2007-04-19
> **dunedust said:**
> \


If the partition uses NTFS format use this command line

[I]sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222[/I]

youll find the partition mounted under /media/windows


the NTFS partition will be mounted as read only 


Ok it worked. But as I said in my original post I need to delete something in my windows file system. So how can I access it as r/w.

---

### Post by Pobega on 2007-04-19
> **bobplano said:**
> that just means you need to use sudo

And use hda1 instead of sda1. That was the point of using fdisk :)

---

### Post by Comzee on 2007-04-19
> **Pobega said:**
> And use hda1 instead of sda1. That was the point of using fdisk :)

Thanks, Since I've already mounted it though I need to know how to,
1: Unmount if necessary
2: Mount it as r/w.

---

### Post by Tundro Walker on 2007-04-19
If nautilus / file manager won't let you delete Windows files, then launch nautilus as root...

```
sudo nautilus
```

...from a terminal.  If you've installed a dual-boot Win/Ubuntu, I'm pretty sure you're savvy enough to know, but I'll say the following anyways...you can seriously hose up your computer if you delete the wrong thing.  I say this especially because Linux shows hidden and normal files on a Windows partition by default.  

EG: in someone elses post, he was surfing his Windows partition / drive, and noticed all the desktop.ini and thumbs.db files, which are normally hidden.  

Before deleting something you don't know about, google it up and see what others say about it.  It's a hassle, but ti'll save a lot of four-letter vocabulary building if it keeps you from having to reinstall Windows (to which you'd have to reinstall GRUB again, since Windows loves to overwrite the whole MBR).

---

### Post by Pobega on 2007-04-19
> **Tundro Walker said:**
> If nautilus / file manager won't let you delete Windows files, then launch nautilus as root...

```
sudo nautilus
```

...from a terminal.  If you've installed a dual-boot Win/Ubuntu, I'm pretty sure you're savvy enough to know, but I'll say the following anyways...you can seriously hose up your computer if you delete the wrong thing.  I say this especially because Linux shows hidden and normal files on a Windows partition by default.  

EG: in someone elses post, he was surfing his Windows partition / drive, and noticed all the desktop.ini and thumbs.db files, which are normally hidden.  

Before deleting something you don't know about, google it up and see what others say about it.  It's a hassle, but ti'll save a lot of four-letter vocabulary building if it keeps you from having to reinstall Windows (to which you'd have to reinstall GRUB again, since Windows loves to overwrite the whole MBR).

Do not use sudo, use gksudo for graphical applications.

And as for unmounting, you use the umount command.

umount /dev/hda1
**OR**
umount /mnt

---

### Post by dpar on 2007-04-19
Some files get locked by windows and can only be removed on boot. Take a look at this program for windows....[http://www.snapfiles.com/get/moveonboot.html](http://www.snapfiles.com/get/moveonboot.html)

---

### Post by Comzee on 2007-04-19
Ok I mounted hda1 under /media/windows.
Then I ran "gk nautilus" it opened up the file system. I went to windows and still couldn't delete anything. It still said this is a read only  disk. I'm not trying to delete system files from windows or anything, just a desktop icon.

Thing is making me mad, :mad:

---

### Post by Pobega on 2007-04-19
Have you installed ntfs-3g yet? Should cure your problems.

---

### Post by NicoleM on 2007-04-19
that's normal performance for linux.  linux can only read NTFS

you need to install something like ntfs-3g in order to get read/write access to ntfs drives.  once you have that set up it won't matter whether you use the terminal or nautilus.

conversely, if you were to boot into windows, you won't be able to read your linux partitions at ALL.  for that you'd need something called fs-driver i believe (not 100% on that)

i use ntfs-3g and am very happy with it.  no stability issues in the past 5 or so weeks that i've been using it.

---

### Post by Pobega on 2007-04-19
> **NicoleM said:**
> that's normal performance for linux.  linux can only read NTFS

you need to install something like ntfs-3g in order to get read/write access to ntfs drives.  once you have that set up it won't matter whether you use the terminal or nautilus.

conversely, if you were to boot into windows, you won't be able to read your linux partitions at ALL.  for that you'd need something called fs-driver i believe (not 100% on that)

i use ntfs-3g and am very happy with it.  no stability issues in the past 5 or so weeks that i've been using it.

I can't believe how fast that became stable; I remember just five months ago I was reading how reading NTFS drives was a challenge, and writing to them was even worse!

---

### Post by Comzee on 2007-04-19
> **Pobega said:**
> Have you installed ntfs-3g yet? Should cure your problems.

Ok, ntfs-3g where do I get it. If there is a code to install it, if so please tell. Or do I get it from synaptic.

---

### Post by Pobega on 2007-04-19
sudo aptitude install ntfs-3g

---

### Post by NicoleM on 2007-04-19
i can't remember if i got it from the repositories or not but here's their website [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

there should be a pretty detailed walkthrough on there.

---

### Post by NicoleM on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

also, that thread was here on the forum...you can dl ntfs-3g through synaptic but you have to add the repository to your sources list

---

### Post by Comzee on 2007-04-19
Ok, I installed it though aptitude, after it installed I still couldn't delete. So I went to the web site. They had a method for atp. It was alot of code work. But I still I can't delete anything.
I'm tweaked out here. WTF.

Apparently this isn't such a nub question.

---

### Post by Tundro Walker on 2007-04-19
> **Pobega said:**
> I can't believe how fast that became stable; I remember just five months ago I was reading how reading NTFS drives was a challenge, and writing to them was even worse!

It's a machismo thing.  The more challenging something is, the more likely they'll do it.  The less challenging, the less likely ("yeah, I'll get right on that bug squishing..ooh, candy!").  

That's why Program / Project Managers or Team Leads have to act like [Vince Lombardi]("http://www.brainyquote.com/quotes/authors/v/vince_lombardi.html") to motivate programmers sometimes.  They have to make a project seem more challenging then it really is, or make it seem like the programmer's trying to prove their very worthiness as a human being instead of just "coding some software".

---

### Post by Comzee on 2007-04-20
Ok, I found out something. I installed the NTFS tool correctly. When I go, Applications->system tools->NTFS configuration tool, it has two options, enable write support for internal devices, and enable write support for external devices. It will only let me enable write support for external devices, the internal devices box is grayed out. Can anybody tell me how to configure it correctly.

---

### Post by NicoleM on 2007-04-20
> **Comzee said:**
> Ok, I installed it though aptitude, after it installed I still couldn't delete. So I went to the web site. They had a method for atp. It was alot of code work. But I still I can't delete anything.
I'm tweaked out here. WTF.

Apparently this isn't such a nub question.

it helps if you tell us exactly what you did...did you mount the partition as it explains to?  were there error messages?

---

### Post by NicoleM on 2007-04-20
> **Comzee said:**
> Ok, I found out something. I installed the NTFS tool correctly. When I go, Applications->system tools->NTFS configuration tool, it has two options, enable write support for internal devices, and enable write support for external devices. It will only let me enable write support for external devices, the internal devices box is grayed out. Can anybody tell me how to configure it correctly.

the link i posted above ([http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)) is very detailed.

if you can't get the automatic method to work skip to part 3 (the manual configuration)  it gives step by step instructions.

---

### Post by Comzee on 2007-04-20
> **NicoleM said:**
> it helps if you tell us exactly what you did...did you mount the partition as it explains to?  were there error messages?

No error messages. I followed the official steps one through three. I used the automatic configuration. When the NTFS configuration panel came up the propblem that I posted happened. 
I couldn't check the box for enable write for internal devices.

---

### Post by juanhunglow on 2007-04-20
> **Comzee said:**
> Ok, I found out something. I installed the NTFS tool correctly. When I go, Applications->system tools->NTFS configuration tool, it has two options, enable write support for internal devices, and enable write support for external devices. It will only let me enable write support for external devices, the internal devices box is grayed out. Can anybody tell me how to configure it correctly.

I didn't happen to notice what flavor/version of Ubuntu your running.

If it's feisty, and you have all the repos enabled, go into synapitc and search for ntfs.  select ntfs-config.
It will add an icon/item to your applications menu.  when you select ntfs-config, it asks what you want to do (mount internal or external NTFS) and where (just type windows).  you done.  It's very easy in Feisty

---

### Post by juanhunglow on 2007-04-20
> **Comzee said:**
> No error messages. I followed the official steps one through three. I used the automatic configuration. When the NTFS configuration panel came up the propblem that I posted happened. 
I couldn't check the box for enable write for internal devices.

If you have the drive mounted already you need to unmount it.

```
sudo umount /dev/whateveryourdriveiscalled
```
Insert the location of your drive.

---

### Post by Comzee on 2007-04-20
Ok, With your help and my 1337 terminal skills (I really don't have them), I manually configured/owned my hda1 partition. :D:D:D. I really appreciate all the people that helped me with this.

Problem solved,

EDIT: This should be a sticky or something.

---

### Post by Tundro Walker on 2007-04-20
Just edit your original post so the subject line reads "[RESOLVED] Mounting NTFS drive" or something, so folks know it's resolved.

---

