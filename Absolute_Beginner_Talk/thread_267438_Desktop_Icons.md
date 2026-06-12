---
title: "Desktop Icons"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Sonic Alpha on 2006-09-28
I have a total of 8 partitions, and 7 icons on the desktop point to the various partitions/HDDs (the Ubuntu partition isn't displayed).

These icons aren't needed, as I can simply use a shortcut/launcher to "computer", so is there any way to remove these icons? (When I try to delete the launchers/shortcuts, it doesn't work).

Thank you in advance :)

---

### Post by bulldog on 2006-09-28
Open gconf-editor and go to apps-nautilus-desktop and alter the settings at your liking.

Hit ALT-F2 and type

```
gconf-editor
```

---

### Post by xpod on 2006-09-28
I got rid of the only icon on my desktop by ridding myself of the os it belonged to:mrgreen: 

Evening BD.. and yerself SA

---

### Post by Sonic Alpha on 2006-09-28
> **bulldog said:**
> Open gconf-editor and go to apps-nautilus-desktop and alter the settings at your liking.

Hit ALT-F2 and type

```
gconf-editor
```

Thank you :)

> **xpod said:**
> I got rid of the only icon on my desktop by ridding myself of the os it belonged to:mrgreen: 

Evening BD.. and yerself SA

Evening ;)  The extra partitions are mostly storage (mp3s, downloads etc).  Ubuntu stuck the icons there when I installed :cool:

---

### Post by CatKiller on 2006-09-28
As an alternative, if you're feeling a bit... hardcore... you could change the mount points to /mnt rather than /media, and then they shouldn't show up on the desktop, but other removable media will.

---

### Post by Sonic Alpha on 2006-09-28
oooOOOooo, I'll have to try that, lol.

---

### Post by xpod on 2006-09-28
You can have the "config.editor" on your menu by going into the "system tools" section in the "alacarte menu editor" and checking the little box.

If it`s a tool you reckon you`ll be using a lot:D 
Just as easy to hit alt-f2 i suppose

---

### Post by Sonic Alpha on 2006-09-28
> **xpod said:**
> You can have the "config.editor" on your menu by going into the "system tools" section in the "alacarte menu editor" and checking the little box.

If it`s a tool you reckon you`ll be using a lot:D 
Just as easy to hit alt-f2 i suppose

Ahh, thank you very much.  Problem sorted :)

---

### Post by xpod on 2006-09-28
Personally it`s been safer for ME to leave such a tool out of harms way for the time being.....I know where it is when i get bored though:mrgreen:

---

### Post by CatKiller on 2006-09-28
I'm going to assume that you don't know much about Linux, so if I'm incorrect please don't take my explanations as patronising. They aren't intended that way. And maybe someone else who stumbles across this post will need more hand-holding than you do.

> **Sonic Alpha said:**
> oooOOOooo, I'll have to try that, lol.

It's easy enough. But it could go wrong, so take it steadily, and if there's anything that you aren't sure about - with any command, especially one that starts "sudo" - take some time to think about it and read the man pages. To view the **man**ual page for a particular command (called <*command*> in this example), type ```
man <*command*>
``` They aren't necessarily that accessible, but they will tell you what it does, and what people are trying to get you to do.

The thing to remember is that Linux uses a unified filesystem - there aren't separate drive letters for different drives and so on. Everything (and I mean everything) is presented as a file in a tree structure that starts at / (root). Other partitions are "mounted" at some point in this tree structure. Some people might have their /home, /boot, /tmp or /var directories on different partitions to the one that contains /, or even on different computers. It's a very flexible system.

Currently, your other partitions are mounted in subfolders of /media, and as a convenience Ubuntu displays all subfolders of /media as icons on the desktop so that you have easy access to your cd drives, iPod, and so on. You would like to keep this behaviour, but not for those partitions. So all you need to do is to mount them somewhere other than /media in the filesystem.

I'm only going to give one example, for ease of typing, for an imaginary partition called "partition". Actually using this example for the particular partitions that you are using is left as an exercise for the reader. This is mostly so that you don't get messed up by my assumptions about what your partitioning scheme is, by copying the instructions verbatim. You'll have to actually **know** what your partitioning scheme is to make use of these instructions in any case, and this decision will force you to do so.

The first step is to make a new mount point. This is just a directory somewhere in the filesystem, but it's not necessarily one that you'll have write access to as an ordinary user. So you get temporary root privileges by using the sudo command. This will ask you for your password. This will be the password that you used to log in. When you type it in, nothing will be displayed on screen. Don't worry, this is supposed to happen. It's so that anyone looking over your shoulder won't know how many letters your password has.

```
sudo mkdir /mnt/partition
```

You might need to give other users read/write access to this directory if they are to use the mounted partitions:

```
sudo chmod 777 /mnt/partition
```

This step might not be strictly necessary. (Edit: It isn't)

Next, you need to unmount the partition from /media:

```
sudo umount /media/partition
```

Note that there is only one "n" in umount. Again, this step might not be strictly necessary.

The list of which partition corresponds to which mount point is kept in a file called fstab. This is in a directory called /etc that contains miscellaneous stuff that you shouldn't fiddle around with under normal circumstances. Hence, to edit it, you'll need root privileges again. First, we'll make a backup:

```
sudo cp /etc/fstab /etc/fstab.backup
```

That way, if it all goes hideously wrong and we can only get terminal access - more likely when fiddling with X configurations than with this procedure - all you need to do is ```
sudo cp /etc/fstab.backup /etc/fstab
``` to get everything back the way it was before. Next, we want to edit it:

```
gksudo gedit /etc/fstab
```

You'll get an error message in the terminal at this point. It's been widely reported and nobody seems to know exactly what causes it, but I have it on good authority that gksudo is the way to go for graphical applications. This will open up a text editor with the contents of /etc/fstab open for editing. If you were using KDE, then **kdesu kate /etc/fstab** would have the same result.

Find the lines that show where and how your partitions are mounted. If the partitions are formatted as FAT, then they might look like this:> /dev/partition	/media/partition	vfat	iocharset=utf8,umask=000	0	0If the partitions are formatted as NTFS, then they might look like this:> /dev/partition    /media/partition ntfs  nls=utf8,umask=0222 0    0

The /dev/partition part is the actual device. This will be a combination of the drive (hda for the first IDE device, hdb for the second, and so on, or sda for the first SCSI/SATA device, sdb for the second, and so on), and the partition number. There are up to four "Primary Partitions", and any number of "Logical Drives" in "Extended Partitions" on a given hard drive. An Extended Partition is also a Primary partition. It is fairly common to have a partition called hda5 that was a data partition in a Windows computer. After that is the place in the filesystem where that device is mounted. That is what we want to change. So change > /media/partition to  > /mnt/partition

You don't need to worry about what the rest of each line means. It is interesting, but not something that you need to concern yourself with for this task.

Save your changes and close gedit.

Now we'd like to mount all of these devices. We could reboot the computer. After all, that's what this file is - the list of devices that get mounted when the computer starts up. However, the command ```
sudo mount -a
``` will mount all of the devices listed in fstab without rebooting. Much better.

Hopefully you've found this information helpful.

---

### Post by Sonic Alpha on 2006-09-29
> **CatKiller said:**
> I'm going to assume that you don't know much about Linux, so if I'm incorrect please don't take my explanations as patronising. They aren't intended that way. And maybe someone else who stumbles across this post will need more hand-holding than you do.

I don't know much about Linux, I'm still learning.

However, I've done the partition mount thing already, folowing [this tutorial]("http://www.psychocats.net/ubuntu/mountwindows"), but made the mount points "/media/whatever".

Thanks for the advice, it's most appreciated ;)

---

### Post by CatKiller on 2006-09-30
Well, there are already lots of good tutorials about mounting out there, like the one that you linked to, but they don't explain exactly what's going on and why. So I thought that it might be good if there was one. Plus I wanted the practise :)

---

### Post by xpod on 2006-09-30
Who better to test on than a complete newcommer......mmmmmmmm;)

Id STILL be reading...lol

---

