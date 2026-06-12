---
title: "Ubuntu Froze and now fsck says recovering journal and nothing happens. help"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Dred79 on 2007-07-29
I dual boot between windows and ubuntu i was in ubuntu trying to figure out how to enable read write access for my 500gb partition. when i did a sudo nautilis i was about to setup permissions on my drive when the screen froze. Now on boot up the progress bar freezes half way. I tried Ubuntu recovery mode but fsck got stuck at recovering journal. How can i fix this?

I am in windows right now and i tried to mount the ext3ifs partitions but they come up blank with windows asking me if i want to format. of course i pressed NO!.  =P  This really sucks cause i already have huge amounts of my data sitting on the ext3 500gig partition. If i get this repaired what file system is the most stable and reliable for storing data. I heard there are add ons to ext3 to make it more stable if so what are they. I can't have this happening all the time it freaks me out. hehe


Thanks

---

### Post by ayenack on 2007-07-31
I've been watching this post and seen no replies so I finally decided to post.

Not sure if this will help but may do. Take a look at [this]("http://www.cgsecurity.org/wiki/TestDisk") app I use when I'm recovering drives and partitions. It's compatible with all the MS OS's GNU Linux, Mac and others. It's simple to use and may well do the trick. But be careful it's a powerful app and can do damage so use your discretion to decide if it's for you.

Good luck. ayenack.

The ext3 file system is generally considered to be very stable. It can become nervous if you use hdparm which can apparently cause data loss. As far as I know there are no add-ons for the ext3 file system other than using hdparm which tries to speed up the drive by tweaking a few settings not the actual ext file system.

---

