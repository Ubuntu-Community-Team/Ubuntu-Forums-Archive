---
title: "I need to make a harddrive image for my ubuntu partition"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by grogger13 on 2007-03-14
I just got ubunutu functioning pretty good and i had a couple of bad sectors on my drive so dell sent me a new harddrive, but i have to return the other one so i need to create a backup of my the linux partition so i dont have to install all the drivers again like my wireless card.   How would i go about creating a harddrive image of just my ubuntu partition.

---

### Post by buuntuu! on 2007-03-14
just do it with [TAR]("http://www.ubuntuforums.org/showthread.php?t=35087")

---

### Post by hyper_ch on 2007-03-14
well, basically I would install ubuntu again on the new drive (setup doesn't take that long..) while the old drive is not connected and then I would plugin the old drive and copy it all over from the old to the new one with the -p option (keep permissions).
The only thing you have to be carefull about will be your /etc/fstab file as it contains the UUIDs of the auto-recognized discs... so that one shouldn't be overwritten then...

I'm far from being a linux expert but since (all) configs are stored in files you should be able to "copy" over your system that way.

---

### Post by grogger13 on 2007-03-14
i use a laptop and have no means of connecting two internal harddrives at once, the only really backup method i have is my archos 504 80gb pmp.

---

### Post by buuntuu! on 2007-03-14
TAR just copies IT ALL right over, no hassle!
in the thread i posted you'll even find the howto for creating the grub entry on your new disc.
easy!

---

### Post by buuntuu! on 2007-03-14
> **grogger13 said:**
> i use a laptop and have no means of connecting two internal harddrives at once, the only really backup method i have is my archos 504 80gb pmp.

and TAR compresses, if disc-space is the issue.
as it says in my signature:

---

### Post by koshari on 2007-03-14
i would get a laptop usb drive enclosure, and use gedit/rsync to copy to prepare/copy the data over to the new drive, 

then you could use the old drive as a removable storage in the future until it fails completely,

---

### Post by grogger13 on 2007-03-20
i dont want to get a case because i have to return the other one to dell or they'll charge me for the new one.

---

### Post by rccharles on 2007-03-22
> **grogger13 said:**
> I just got ubunutu functioning pretty good and i had a couple of bad sectors on my drive so dell sent me a new harddrive, but i have to return the other one so i need to create a backup of my the linux partition so i dont have to install all the drivers again like my wireless card.   How would i go about creating a harddrive image of just my ubuntu partition.
I read about this somewhere. 

I haven't done this for real, but I tested what I could.

You can make a copy of the names of all the packages that you downloaded.  With your new drive installed and Ubuntu too, you install all the packages on your new system.  You do not have to worry about installing the same package twice since the second install will be ignored.

On old system:

 sudo dpkg-query --show --showformat='${package} ' >newfile

cat newfile
# to verify

#copy newfile to new system

# on new system
sudo bash


cat newfile | xargs  aptitude --assume-yes  install

exit

Robert

---

### Post by louieb on 2007-03-22
> **buuntuu! said:**
> just do it with [TAR]("http://www.ubuntuforums.org/showthread.php?t=35087")
That how I do it. Even leaned how by following the thread buuntuu linked to.
or look at the psychocats link in my signature there a page on using  Partimage there.

---

