---
title: "[SOLVED] Recovering a hard drive with Ubuntu Live Disk"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Taum on 2007-09-01
This hard drive is my wife's and previously had Windows on it.  It will not boot on its own or as a slave to any other drive.  I've used the Windows software to run CheckDisk to no avail.  

What I want to do is use the Ubuntu Live Disk to dig out pictures and documents from the hard drive and email them to my wife for her.  Can I, from terminal or from GNOME, get to these files while using the Ubuntu Live CD?  Should I install Ubuntu for easier use?

I've looked at similar threads but they don't seem to solve my issue.  I'm not that adept with UNIX commands, so please assume I'm an infant in this matter.  Thanks!

---

### Post by Lucifiel on 2007-09-01
> **Taum said:**
> This hard drive is my wife's and previously had Windows on it.  It will not boot on its own or as a slave to any other drive.  I've used the Windows software to run CheckDisk to no avail.  

What I want to do is use the Ubuntu Live Disk to dig out pictures and documents from the hard drive and email them to my wife for her.  Can I, from terminal or from GNOME, get to these files while using the Ubuntu Live CD?  Should I install Ubuntu for easier use?

I've looked at similar threads but they don't seem to solve my issue.  I'm not that adept with UNIX commands, so please assume I'm an infant in this matter.  Thanks!

Maybe you should try using Testdisk instead. I think it can be found on System Rescue Cd? Not entirely sure.

---

### Post by mgmiller on 2007-09-01
If the drive is readable, you can boot off a Feisty live CD and then go to Places > Computer.  One of the entries there should be the old windows drive.  It will say something like 232.9 GB volume, or whatever size the drive is.  Just double click it to open the drive and you can navigate around and drag stuff to a USB thumb drive or even burn them to a CD.  All done from the Live CD.

If the drive has mechanical issues, and is not readable, you may not be able to recover anything from it.

---

### Post by Taum on 2007-09-01
> **Lucifiel said:**
> Maybe you should try using Testdisk instead. I think it can be found on System Rescue Cd? Not entirely sure.

I don't know about no System Rescue CD (and I'm fresh out of blank CDs so I couldn't burn one if I wanted to) so I'll assume that it's a part of the usual boot up from Ubuntu.  I'll restart and see if that has anything there for me.

---

### Post by Taum on 2007-09-01
> **mgmiller said:**
> If the drive is readable, you can boot off a Feisty live CD and then go to Places > Computer.  One of the entries there should be the old windows drive.  It will say something like 232.9 GB volume, or whatever size the drive is.  Just double click it to open the drive and you can navigate around and drag stuff to a USB thumb drive or even burn them to a CD.  All done from the Live CD.

If the drive has mechanical issues, and is not readable, you may not be able to recover anything from it.

I have:

Floppy Drive
CD-RW/DVD-ROM Drive
Filesystem

I see no mounted disk nor do I really know where to look for such.

---

### Post by Lucifiel on 2007-09-01
> **Taum said:**
> I don't know about no System Rescue CD (and I'm fresh out of blank CDs so I couldn't burn one if I wanted to) so I'll assume that it's a part of the usual boot up from Ubuntu.  I'll restart and see if that has anything there for me.
Well, SystemRescueCd can be downloaded from [http://www.sysresccd.org/](http://www.sysresccd.org/)

Try and get it 'cos seriously, Testdisk is extremely useful for fixing borked up partitions.

---

### Post by mgmiller on 2007-09-01
> I see no mounted disk nor do I really know where to look for such.

In the top panel (task bar), click on Places, then click on Computer.  Does it show your hard drive?

---

### Post by iamhugeinjapan on 2007-09-01
Absolutely you can.

Boot up the Ubuntu live cd and once you're at the desktop, open a Terminal.

Type:
```
sudo fdisk -l
``` 

You'll get a list of partitions on the pc You'll likely have an NTFS partion that is called /dev/hda1 or /dev/sda1 . Just match the name to your list.

We need to make a folder to mount the data in so let's create one

```
sudo mkdir /data
```

Then lets mount the Windows partion into it so you can copy off the data (match the /dev/ name to what you found in the list above

```
sudo mount /dev/hda1 /data
```

If that completed without errors you can open a file browser and go to the /data folder and see the files. Email or copy them off as you wish.

---

### Post by mgmiller on 2007-09-01
> Boot up the Ubuntu live cd and once you're at the desktop, open a Terminal.

You do this by going to Applications > Accessories > Terminal

---

### Post by Taum on 2007-09-01
This is what I get from the fdisk:

```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        7297    58581022+   7  HPFS/NTFS
```

I made sure I used /dev/hda2 and made the Data folder, but the file system says I don't have permission to access it.  I are confused.  When I tried to access it with a DOS prompt, I got a similar error.

---

### Post by iamhugeinjapan on 2007-09-01
Okay sorry about that. Try this to give read write permissions to the normal user:

```
sudo chmod 777 /data
```

---

### Post by Taum on 2007-09-01
> **iamhugeinjapan said:**
> Okay sorry about that. Try this to give read write permissions to the normal user:

```
sudo chmod 777 /data
```

That gives me:

```
chmod: changing permissions of `/data': Read-only file system
```

Is that right?

---

### Post by Taum on 2007-09-01
I still get:

```
ubuntu@ubuntu:/$ cd data
bash: cd: data: Permission denied

```

---

### Post by iamhugeinjapan on 2007-09-01
Ah yes it's because the ntfs partition is read only.  Try the chmod command with 755 if read only access is fine.

---

### Post by bsharp on 2007-09-01
type ```
gksudo nautilus
```

and then navigate to the /data folder and you will be able to do whatever.

---

### Post by Taum on 2007-09-01
> **bsharp said:**
> type ```
gksudo nautilus
```

and then navigate to the /data folder and you will be able to do whatever.

Ha!  That works!  YAY!  Thanks!

---

