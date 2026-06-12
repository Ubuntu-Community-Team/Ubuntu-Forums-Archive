---
title: "Permissions on external USB drive"
date: 2007-05-10
forum: Apple PPC Users
---

### Post by justinae on 2007-05-10
I have a Western Digital external hard drive that I used with my mac and so was formatted for Mac OS X (journaled). When I plug in the USB Ubuntu recognizes it just fine but I can't add or remove any files or folders. I can copy from the drive though. I have a couple of very large (25Gig) movie files for a home video I'm working on.

When I try to change permissions I can't make any changes.

I'm running Ubuntu 7.04.

many thanx!

---

### Post by stmiller on 2007-05-10
You'll have to do

sudo nautilus

to write to the drive. Reading and writing with hfs+ file format defaults to root access only. You can change this in the /etc/fstab file.

---

### Post by dannyboy79 on 2007-05-10
ubuntu can't write to HFS+ if that's what it is and since you stated it's  a drive from mac os x, it's most likely HFS+. I believe you can recompile your kernel so that you have write support of HFS+ filesystems but I am not sure how. you'd have to check around in gogle or somewhere else. what does this entered into a terminal return?

mount

SORRY, I'll be more clear, you can't write to it if you leave journaling on. check this out: [http://ubuntuforums.org/showthread.php?t=392287&highlight=writing+to+hfs](http://ubuntuforums.org/showthread.php?t=392287&highlight=writing+to+hfs)

---

### Post by justinae on 2007-05-10
i don't have the mac anymore so I'm happy to reformat the external drive in a way that ubuntu can read/write to easily. Will ubuntu let me copy the 25Gig files to the internal hard drive, reformat the external, then copy them back to the external?

what kind of format should i use to be able to handle the large file sizes.

thanx!

---

### Post by stmiller on 2007-05-10
> **dannyboy79 said:**
> ubuntu can't write to HFS+ if that's what it is and since you stated it's  a drive from mac os x, it's most likely HFS+. I believe you can recompile your kernel so that you have write support of HFS+ filesystems but I am not sure how. you'd have to check around in gogle or somewhere else. what does this entered into a terminal return?

mount

SORRY, I'll be more clear, you can't write to it if you leave journaling on. check this out: [http://ubuntuforums.org/showthread.php?t=392287&highlight=writing+to+hfs](http://ubuntuforums.org/showthread.php?t=392287&highlight=writing+to+hfs)

Yes it can. (Ah I see you edited your post) HFS+ read/writing is stable and included, but yeah you do have to deal with disabling journaling.

----------

Yes, you can copy the contents over to your ubuntu internal hard drive. Just open a terminal and type

sudo nautilus

browse to the drive and copy to where you want the stuff.

Then I'd suggest formatting the drive ext3 journaled. Use gparted.  

sudo apt-get install gparted

and run it with

sudo gparted

---

### Post by justinae on 2007-05-12
thank you for all the help. i reformatted the drive using ext3, then changed the owner to be myself rather than root and all is well.

thanx again!

---

