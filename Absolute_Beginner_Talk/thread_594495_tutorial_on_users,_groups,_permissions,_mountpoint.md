---
title: "tutorial on users, groups, permissions, mountpoints?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by bottleman on 2007-10-28
Hi there, I know nothing about Linux administration, but as a user I've had (K)ubuntu as the primary OS on my laptop for 8 or 9 months now. I've liked it but one thing  has consistently been troublesome: permissions for external drive devices connected by USB... flash drives and external hard drives.   

My experience with these devices is very inconsistent.  Sometimes they are recognized and mounted on the desktop and work fine.  Other times they appear on the desktop but when I try to read them, I get a message that I don't have sufficient permissions to view them (let alone write to them).  Other times they are not mounted at all and I have to go define a mountpoint in gparted or something like that.

It's been a real problem since I have a lot of critical work I need to back up, and external drives are the best way for me to do it.   There are some cool programs like Keep I'd like to use, but seem to have real problems with external drives.  I always seem to have the wrong permissions somewhere.  

So I have two questions: 
1) Can someone recommend a good tutorial or explanation of the user/group file permissions system, especially in reference to external drives?  
2) Generally, is this my problem or Kubuntu's ? (I'm using 7.04 now.)  Have I just set things up wrong?  Or is there something about Kubuntu that really doesn't work well with these devices? 

Thanks for any input you have!

---

### Post by Herman on 2007-10-28
Hello bottleman,
Tuxfiles has a great website with an excellent page on [How to mount filesystems in Linux - 1.1]("http://www.tuxfiles.org/linuxhelp/mounting.html")

   If you have trouble copying and pasting or reading and writing data from one disk to another it could be your file ownership and permissions. 
   Tuxfiles has a great page on how to use the chmod command to fix that, [_Linux File Permissions_]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")
   Tuxfiles has another great page on how to use the chown command too, [How to change a file's owner and group in Linux - 1.0]("http://www.tuxfiles.org/linuxhelp/fileowner.html")

Regards, Herman :)



---

### Post by kellemes on 2007-10-28
> **Herman said:**
> 
Regards, Herman :)

Little of topic I know..
You're "The Herman" of [The Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")?
If so.. you saved my life in the past a couple of times. Thanks for that. :popcorn:

---

### Post by ronmarley1 on 2007-10-28
Here's what I used when starting with Linux, although you've been using it for some time.  Looks like the guide has been updated in Sept. of this year.  The guide has many "do this, this is what you just did" items.
html: [http://tldp.org/LDP/intro-linux/html/index.html](http://tldp.org/LDP/intro-linux/html/index.html)
pdf: [http://tldp.org/LDP/intro-linux/intro-linux.pdf](http://tldp.org/LDP/intro-linux/intro-linux.pdf)

---

### Post by bottleman on 2007-10-28
thanks, i will try those pages.

---

### Post by Herman on 2007-10-29
Hello kellemes,
 Yes, there are one or two other Hermans around here, and I'm the one with the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") site.  I'm glad if I was able to help you. I have noticed you helping a few others around here yourself, so thanks for your work too! :)

Hello ronmarley1
Thanks for those links, I like them too! :)

Hello bottleman,
Good luck, and keep on learning. I'm still learning and I enjoy every minute of it, I hope you do too.

Regards, Herman :)

---

