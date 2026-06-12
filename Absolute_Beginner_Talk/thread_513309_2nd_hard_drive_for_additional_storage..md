---
title: "2nd hard drive for additional storage."
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-07-30
I have an 80 GB hard drive that I'd like to use for additional storage, almost as an extention of this drive.  I can access it, but only when I go to places>computer>74.6 GB Volume: Disk.  I can double click it, it asks for a password, than shows up on my desktop.  Then to remove it I have to right click and unmount.  What I'm trying to do is to make it an extenstion of my 120 GB HD, so that Ubuntu will see them as 1 200 GB HD.  I don't know if this is possible, and if not how would I at least get it to automount to my computer, so I don't need to actually go to it, click on it, and enter my password just to get it.  My setup is 120 GB Ubuntu HD, with a windows Virtualbox, and an 80 GB that is currently emtpy.  Both are formatted to ext3.

---

### Post by diatribe on 2007-07-30
I am fairly sure you can not have 2 drives as 1 partition (read: completely sure), as for automounting do you have an entry for it in fstab?

---

### Post by Jellicletrb on 2007-07-30
There is an app called ntfs-3g, that you can install with Synaptic, or by using the terminal;

> sudo apt-get install ntfs-3g

I'd recommended using synaptic, and read all the notes that it displays when you select it.  It will tell you how to set ntfs up.  I have 2 HDD and a USB drive, all of which mount automatically, and all of which I can read and write to from Ubuntu.  Besta luck  :)

---

### Post by diatribe on 2007-07-30
> **Jellicletrb said:**
> There is an app called ntfs-3g, that you can install with Synaptic, or by using the terminal;



I'd recommended using synaptic, and read all the notes that it displays when you select it.  It will tell you how to set ntfs up.  I have 2 HDD and a USB drive, all of which mount automatically, and all of which I can read and write to from Ubuntu.  Besta luck  :)

If you read the post both drives are ext3, ntfs-3g is not necessary

---

### Post by Maxtorm on 2007-07-30
> **diatribe said:**
> I am fairly sure you can not have 2 drives as 1 partition (read: completely sure), as for automounting do you have an entry for it in fstab?
Actually, I believe it is possible to create one partition out of the two drives using RAID 0.  This will take a bit of work and I don't think there is any easy way to retain your existing installation.  There is a good tutorial for setting up a software RAID here: [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html) .  The tutorial demonstrates how to complete a RAID 1 install, but adapting the instructions for RAID 0 should not prove difficult.

---

### Post by Specter043 on 2007-07-30
Okay, Well I don't really want to lose my current installation, so can anyone tell me how to automount the hard drive?

---

### Post by diatribe on 2007-07-30
you need an entry in your fstab ;p

---

### Post by Specter043 on 2007-07-30
I feel lame for saying this, but i'm not sure what that is?

---

### Post by Jellicletrb on 2007-07-30
> **diatribe said:**
> If you read the post both drives are ext3, ntfs-3g is not necessary

Thats why I don't try to post advise very often.  I still suck at this  :lolflag:

---

### Post by Maxtorm on 2007-07-30
> **Specter043 said:**
> I feel lame for saying this, but i'm not sure what that is?

First of all, don't feel lame.  Not too many people would venture as far as you already have.  For a good wiki entry on fstab, see: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Also, I haven't tried this, but there is an application available via Add/Remove called Storage Device Manager that claims to be able to handle your fstab without requiring direct editing of the file (note: it is not a supported Ubuntu application).  You could give that a try.

> **Jellicletrb said:**
> Thats why I don't try to post advise very often.  I still suck at this 

Don't let that stop you.  The more people participating in these forums, the better off we all are!

---

### Post by Specter043 on 2007-07-30
I found the program you mentioned and it worked wonderfully, after I read that Wiki entry a bit to understand what I was doing.  Thank you very much for your help.  These forums never seem to fail me.

---

### Post by Specter043 on 2007-07-30
I spoke too soon in the last post.  It now automatically mounts, but also shows up on my desktop  I'd prefer it wasn't there, although it's no big deal.  Does anyone know how to hide it or just configure it so it doesn't show up on my desktop?

---

### Post by diatribe on 2007-07-30
you're using nautilus I assume? I dont know how to stop it but I have seen other threads about it, try searching the forums

---

### Post by Maxtorm on 2007-07-30
> **Specter043 said:**
> I spoke too soon in the last post.  It now automatically mounts, but also shows up on my desktop  I'd prefer it wasn't there, although it's no big deal.  Does anyone know how to hide it or just configure it so it doesn't show up on my desktop?
Seems the most relevant post is [http://ubuntuforums.org/showthread.php?t=457494&highlight=hide+mount+point](http://ubuntuforums.org/showthread.php?t=457494&highlight=hide+mount+point)
The bad news is that it doesn't look like it is possible to automount and hide the icon.  (Thinking out loud, I'm wondering whether you could create a mount point with a leading "."  For example /mnt/.disk instead of /mnt/disk.  It would probably cause more problems than it solves.)

---

### Post by Specter043 on 2007-08-01
and I return.  I tried to write to the hard drive for the first time today, and either it isn't where it's supposed to be,  Can anyone tell me how to find the hard drive, either through terminal etc, and tell me how to automount it to some directory.  I always hear about mounting it to /media, so that's fine.  Any help would be greatly appreciated.

---

### Post by Maxtorm on 2007-08-01
In a previous post, I referred to the fstab article [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131).  What point do you get stuck at?

---

### Post by Specter043 on 2007-08-01
I went there and clicked mounting partitions automatically.  The script method won't work for me, because it is looking for a windows/mac partition.  My 80 GB drive is formatted to ext3.

---

