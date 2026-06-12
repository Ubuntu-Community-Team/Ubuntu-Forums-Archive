---
title: "[SOLVED] HowTo image one drive to directory on another"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2007-11-03
My machine has two hard drives. Windows system is on one, ntfs data on the other. 

I want to make the machine dual boot, but I'm not going to do that until I have an image of the windows system (drive c:) to a directory on the other drive (drive d:).

Using Ubuntu live 7.x I tried to use partimage but I cannot figure out how to put the image on the second drive, which I believe is mounted as hdb, in a directory called /backup. 

Assuming the image file will be named winbackup, how do I tell gparted to place it on the /backup directory of the second drive?

TIA -- Gary

---

### Post by cmnorton on 2007-11-03
Dismount the windows drive, and use dd. Read up on dd first.

---

### Post by Jose Catre-Vandis on 2007-11-03
Better still, download a copy of System Rescue Live Cd or Parted Magic 1.8 Live CD, then follow this howto. (you may be able to do this with your live cd?)

[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

The trick is to mount the drive you want to save the image to at the command line BEFORE you start partimage, and remember what it is and why.

---

### Post by Duck2006 on 2007-11-03
The DD commands are good to use.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

This has just about it all.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Jose Catre-Vandis on 2007-11-03
> **Duck2006 said:**
> The DD commands are good to use.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

This has just about it all.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

I quite agree with you but: (and quoted from your first link)

[COLOR="Red"]"THE DD COMMAND
This is one of the more complex Linux commands and actually not really suited for new Linux users"[/COLOR]

---

### Post by Duck2006 on 2007-11-03
> I quite agree with you but: (and quoted from your first link)

"THE DD COMMAND
This is one of the more complex Linux commands and actually not really suited for new Linux users"

Yes this is true but you have to start some where.

---

### Post by Jose Catre-Vandis on 2007-11-03
lol@Duck2006

---

### Post by Gary Nored on 2007-11-04
So many kind folk have offered answers, but I still can't make it work. I can unmount the data drive with no error messages being returned, but I can't mount it anywhere. At least I think that's what's happening. I've created mount points/directories under /dev, /media and everywhere else I've been told that it doesn't exist, but no joy. I've installed the ntfs configuration tool, but nothing. Partimage always fails, telling me that a device doesn't exist, or that it cannot write a temp file, suggesting that perhaps I'm out of space. lsof is certain that neither drive exists and/or that neither have a valid ntfs signature. 

Curiously, no matter what I do, the live-cd gui can always see both hard drives, and I have full control over both, but neither can EVER be seen from the terminal! 

Anybody have any idea of what's going on? I really, really, NEED to do this.

tia - gary

---

### Post by Jose Catre-Vandis on 2007-11-04
Let's take a step back.

Both your hard drives are formatted ntfs.

When you run the Ubuntu Live CD it mounts both of these drives and you can see files and data on each.

You need to unmount your Windows OS drive only

You need to have read/write access to your data drive (assumes the live cd sorts this out for you?)

Look in your /etc/fstab file for live cd and see where the drives are mounted, then you can unmount the windows one and see the path to your /backup directory

Then fire up partimage and follow the howto i pointed at earlier

Now this is what I would do, if using the live cd, where do you get stuck?
Outputs of sudo fdisk-l, cat /etc/fstab and df -Th will help.

---

### Post by Gary Nored on 2007-11-05
Thanks Jose.

I think the problem lay with some quirk of the live OS. Nothing seemed to successfully mount any drive even though the gui was able to do anything/everything with it. When I mounted it using the ntfs utility, it worked, and and appropriate entries were made in the file system so that I could find out exactly what the mount point was called. Plugged this string into partimage and viola! It worked. 

Thanks again, both to you and everyone who helped me with this. This is a great community!

Gary

---

### Post by Jose Catre-Vandis on 2007-11-05
Ta da :)

---

