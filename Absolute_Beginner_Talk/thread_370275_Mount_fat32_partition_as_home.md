---
title: "Mount fat32 partition as /home"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Meson on 2007-02-25
I'm creating a Window XP / Ubuntu system.  I have a 10 gig NTFS primary, and the remaining space divided into a 1 gig swap, a 8 gig ext3 to mount / and I'd like the remainder of my hard disk, roughly 40 gigs to be mounted to /home as a FAT32 partition to share between both OSs.  Is it not possible to mount FAT32 as home (as the installer is telling me) or is there a workaround? 

The reason I want to mount it to home is because I'd like to do some things like sharing firefox and thunderbird profiles.

Thanks!

---

### Post by kerry_s on 2007-02-25
No, you can't you need to use linux file system for /home. You can have a separate fat partion to copy files to and from, but not as the included system.

---

### Post by n8bounds on 2007-02-25
Do it the "other" way around:  [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by steve.horsley on 2007-02-25
I'll agree with the others. /home **must** be on a Linux filesystem or all sorts of things won't work.

You could leave /home on the root partition, mount the FAT in /media/hdax and put a symlink into your home directory pointing to /media/hdax Or if only you will use the FAT partition, mount it straight into a folder inside your home directory.

Or make the /home partition an ext3 partition and use the windows driver that n8bounds suggests so that windows can read it.

---

### Post by Meson on 2007-02-25
Cool, I went with a /share directory for the FAT32 disk but I haven't transferred my data yet.  I think I might use this driver.

One question though about access rights.  The website says that it doesn't maintain them.  Does this mean they work normally via linux and windows is immune to them?  Or do the work normally in windows and linux is immune, or are all files always 777 in both environments?

---

### Post by Meson on 2007-02-25
Is there a way to run gparted from Ubuntu or is it only available when running the cd?  If it's only available from the CD, is there a way to only run the gparted and not as part of the install sequence?

Basically I just want to convert my empty fat32 partition to ext3.  I'd also like to mount it to /home - do I do that through fstab or something?

---

### Post by Maestro23 on 2007-02-25
> sudo aptitude install gparted

Will install gparted onto your system. Can then run it as root.

---

### Post by Meson on 2007-02-25
Awesome.  This should be my last question (fingers crossed behind my back):

Now that I've formatted my FAT32 partition into an ext3, I want to mount it to /home through /etc/fstab

What will become of the data in my existing home directory located on the Ubuntu installation partition?  Should I delete it first - will they just merge?  I'm not sure what to do

---

