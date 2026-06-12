---
title: "[SOLVED] Ubuntu Feisty Partition options"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-30
In the Feisty Live CD,  there is no option to create an Extended partition. There are only two choices
1) Primary
2) Logical
 
So when I create 
/
/home
and/swap as logical partitions, where are they placed?
 
Also I need to create another partition called /shared (ext3) which will have data shared by Ubuntu and Windows. Should that be a primary partition or can it be a logical one with the above 3 ?
AFAIK, Logical partitions reside under an Extended Partition. Correct ?
Since I already have two windows partitions as primary drives
C: and D: (mounted as /windows/sda1 and /windows/sda2)
Will all the above logical partitions that I create go into sda3 ?
 
Sorry, I am a little confused about primary, extended and logical partitions !:confused:

---

### Post by Inxsible on 2007-04-30
Attached is the screenshot of the partitions that i created during install. Could someone please verify if this would be correct?

Or do I need the / and /home on a primary partition?

---

### Post by GrueTamer on 2007-04-30
> **Inxsible said:**
> Attached is the screenshot of the partitions that i created during install. Could someone please verify if this would be correct?

Or do I need the / and /home on a primary partition?That looks like it's going to work fine.  The only thing that I'm going to point out that may be a problem is that the /shared partition might not work in windows, because of the file type.  I've never gotten ext3 partitions to be read in windows, but that might be because they were linux partitions, as that is going to be.  At this point, I recommend using GAIM to talk to me directly through msn (if you have it) or irc (server is irc.freenode.net, I'm in #ubuntu) instead of continuing this over the forum, as it will be faster and easier for the both of us.  But do what you want.

You can go ahead with your setup if you want.  You might want to not make a shared partition just yet, so that we can make sure that it's going to work with windows, but do what you want.

You're so close to using Ubuntu, I bet you can taste it!

---

### Post by apunc1 on 2007-04-30
i had a hard time understanding partitions too. i found this link [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2568898](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2568898) that describes primary, logical and extended partitions much better than i can.

i think your shared partition for linux and windows files should be fat32

---

### Post by Inxsible on 2007-04-30
> **GrueTamer said:**
> That looks like it's going to work fine. The only thing that I'm going to point out that may be a problem is that the /shared partition might not work in windows, because of the file type. I've never gotten ext3 partitions to be read in windows, but that might be because they were linux partitions, as that is going to be. At this point, I recommend using GAIM to talk to me directly through msn (if you have it) or irc (server is irc.freenode.net, I'm in #ubuntu) instead of continuing this over the forum, as it will be faster and easier for the both of us. But do what you want.
 
You can go ahead with your setup if you want. You might want to not make a shared partition just yet, so that we can make sure that it's going to work with windows, but do what you want.
 
You're so close to using Ubuntu, I bet you can taste it!
 
 
How do i add you to my buddy list? What screen name should i search for?
GrueTamer?
 
 
As for the /shared, I plan to use Fs-Driver to access EXT3 partitions from Windows

---

### Post by henrywm on 2007-04-30
I want to install Ubuntu on a laptop which is currently using Fedora Core 6. I want Ubuntu to replace FC6, because there are some things which I have been unable to make work in FC6.

My current partitions are as follows:
boot - 101.04 MB
/ - 7.81 GB
swap - 509.88 MB
extended (including home) - 19.53 GB

I want to replace FC6 while leaving my documents, music files, etc in my home partition intact. How can I do this? The Ubuntu install does not give this option.

---

### Post by GrueTamer on 2007-04-30
> **Inxsible said:**
> How do i add you to my buddy list? What screen name should i search for?
GrueTamer?In #ubuntu, I'm GrueTamer, and on MSN, I'm [email]gruetamer@hotmail.com[/email].  I'm on both right now, but I don't know how much longer I'll be on.

---

### Post by apunc1 on 2007-04-30
> **henrywm said:**
> I want to install Ubuntu on a laptop which is currently using Fedora Core 6. I want Ubuntu to replace FC6, because there are some things which I have been unable to make work in FC6.

My current partitions are as follows:
boot - 101.04 MB
/ - 7.81 GB
swap - 509.88 MB
extended (including home) - 19.53 GB

I want to replace FC6 while leaving my documents, music files, etc in my home partition intact. How can I do this? The Ubuntu install does not give this option.

if you're using the ubuntu live cd, you will use gparted. kubuntu uses gtparted i think. i am only familar with gparted. they both do the same thing.
during the partition section of the ubuntu install, select to edit manually. you then will be showed your existing partitions which you can then choose to delete, resize, or format. you would not select the format box for your /home partition or whichever partition has the data you wish to save. i would delete the partitions which hold fedora and create new partitions for ubuntu.

---

### Post by wetland on 2007-04-30
> **Inxsible said:**
> As for the /shared, I plan to use Fs-Driver to access EXT3 partitions from Windows

I just reloaded my laptop new hard drive the old one crashed. Set it up using fs-driver from the other side and it works great.

---

### Post by henrywm on 2007-07-16
> **apunc1 said:**
> if you're using the ubuntu live cd, you will use gparted. kubuntu uses gtparted i think. i am only familar with gparted. they both do the same thing.
during the partition section of the ubuntu install, select to edit manually. you then will be showed your existing partitions which you can then choose to delete, resize, or format. you would not select the format box for your /home partition or whichever partition has the data you wish to save. i would delete the partitions which hold fedora and create new partitions for ubuntu.

I followed these instructions, but now I do not have permission to access my old home directory.

---

### Post by apunc1 on 2007-07-16
> **henrywm said:**
> I followed these instructions, but now I do not have permission to access my old home directory.

wow sorry you are having a hard time. i think you need to use the chmod command to repair your permissions. i'm not an expert on chmod, so hopefully somebody else will offer advice.

the commands in terminal

```

sudo chmod -R 700 /home/<username>
sudo chown -R <username> /home/<username>
```

where <username> is your ubuntu username may work. i grabbed that from this post [http://ubuntuforums.org/showthread.php?t=498803&highlight=permissions+to+access+home](http://ubuntuforums.org/showthread.php?t=498803&highlight=permissions+to+access+home)

edit: did you make a new /home for ubuntu or did you mount your /home for FC as your /home for ubuntu?
edit again: just notice this was marked solved ;)

---

