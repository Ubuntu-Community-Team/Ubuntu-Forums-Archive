---
title: "Accessing separate HDD - ntfs"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by phuturism on 2007-01-03
Hey all,

My first try of ubuntu - installed yesterday and loving it so far.  Crossed over from win XP.

On my machine I have two separate drives - each 20GB.  I reformatted the C drive that had XP and installed ubuntu 6.10 in a standard way nuking the winxp installation completely  - all my data files I stowed on the other drive - which is NTFS.   And yes I know 40GB is not a lot these days!

Using the tutorial at [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) I have successfully mounted the drive and can view contents.  Amazing.  I would like to convert this drive to a more useable linux volume but I want to keep the data on it.

OK - stupid questions follow.

Can I convert to fat32 without deleting the data?  Or do I have to move stuff across to drive A and then start to partition?  The data drive is quite full - about 16GB or so.

Any suggestions or tips would be appreciated!  Last resort is just to burn the data onto DVD media I suppose.

---

### Post by Sef on 2007-01-03
> Can I convert to fat32 without deleting the data?

No.  The reformat will erase any data.

> Or do I have to move stuff across to drive A and then start to partition?

Yes, you have to move it to another partition or hard drive. 

> Last resort is just to burn the data onto DVD media I suppose.

Yes, that probably would be the best, unless you wanted to buy an external hard drive.

---

### Post by sm1thson on 2007-01-03
partition magic 8 on windows can convert without reformating ie it keaps the data. Im still waiting for someone to tell me how to do it on linux [in my similar thread]("http://www.ubuntuforums.org/showthread.php?t=330418")

---

### Post by phuturism on 2007-01-03
> **sm1thson said:**
> partition magic 8 on windows can convert without reformating ie it keaps the data. Im still waiting for someone to tell me how to do it on linux [in my similar thread]("http://www.ubuntuforums.org/showthread.php?t=330418")

Yeah - had heard partition magic can do this but I dont want to reinstall windows just to use that app...  good- luck!

---

### Post by aberry5555 on 2007-01-03
I do not think there's any need to do any of this, you can use a program called ntfs-3g that will let you read-write on your ntfs drive:

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

This is the website, though rather than downloading it from there I would open a terminal in Ubuntu and type in "sudo synaptic", then use synaptic to download it if it's available from the ubuntu repositories. To install it you'll either need to set up a script at boot or figure out how to label your partition as an ntfs-3g drive, read up on the website it should tell you more.

---

### Post by jck3j on 2007-01-03
I had the same problem with the NTFS drive. What I did was i used the GParted LiveCD from [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") and it is the same program you could have used to manually partition your hard drive during installation. It worked well for me. I didn't lose any information and it works really well with Ubuntu and XP.

---

