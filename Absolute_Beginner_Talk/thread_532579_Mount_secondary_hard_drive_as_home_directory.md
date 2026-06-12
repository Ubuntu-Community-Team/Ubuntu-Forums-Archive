---
title: "Mount secondary hard drive as home directory"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-08-22
So I have Ubuntu installed on a 10 gb hard drive, but I have a much larger hard drive that I recently reformatted to ext3 for holding my files. So it's in my computer, configured as a slave. But what I want to do is mount it as my home directory, so that all of my files can be there, so I want to copy all of the files in my current home directory over to the other HD, delete my home directory, and have the big HD automount as my home directory. So the question is...how do I do this? Also, even though I chmod-ed the drive to 777, when I browse it in Nautilus, I'm still told that access to the drive is restricted to administrative users only. How do I change this? Thanks

---

### Post by igknighted on 2007-08-22
In theory, you would add the proper entry into fstab and then cut/paste the contents of your home directory (including the hidden files) onto the root of the disk (must be a linux file system IIRC... in other words not ntfs or fat32).  In reality, however, I would not do that.  I would mount the external drive inside your home folder (for example, /home/username/everything_goes_here) and store all your documents/files there.  This way if you don't have the external plugged in for some reason your system will work just fine because your user settings will still be on the main HD.

EDIT: I thought that was an external, I suppose you could do the cut & paste of the whole /home/username folder, but the safer bet is to just mount it inside the home folder.

---

### Post by southernman on 2007-08-22
> **chimerical_brio said:**
> So I have Ubuntu installed on a 10 gb hard drive, but I have a much larger hard drive that I recently reformatted to ext3 for holding my files. So it's in my computer, configured as a slave. But what I want to do is mount it as my home directory, so that all of my files can be there, so I want to copy all of the files in my current home directory over to the other HD, delete my home directory, and have the big HD automount as my home directory. So the question is...how do I do this? Also, even though I chmod-ed the drive to 777, when I browse it in Nautilus, I'm still told that access to the drive is restricted to administrative users only. How do I change this? ThanksFirst off I have to say... never chmod a partition to 777. AT the very most it should be no more than 755. I've also read on securing Ubuntu your home partiton should be 700, but I can't attest to that being proper since your home directory also stores hidden configuration files for all the programs you use.

What you need to do to change it's ownership is: 

sudo chown -R username:username /path/to/partition/or/directory

First you need to get your home partition setup though... don't we! ;) Have a go at it with this link below:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by qpieus on 2007-08-22
Here's another good how-to for moving your home directory:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

