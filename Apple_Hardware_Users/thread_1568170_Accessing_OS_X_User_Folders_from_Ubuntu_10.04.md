---
title: "Accessing OS X User Folders from Ubuntu 10.04"
date: 2010-09-04
forum: Apple Hardware Users
---

### Post by vgrisham on 2010-09-04
Hello,

I'm a long time Ubuntu user. Recently though, I have strayed from the flock and become--gulp--an Apple fanboy. I'm trying to amend my ways however, and I've managed to create a nice little triple boot on my Macbook Pro 5,3. 

Everything is working swell in Ubuntu (Lucid). The only thing I can't figure out is how to access my user files in OS X 10.6. I have installed hfsplus, but when I mount the Macintosh drive, my folders are all X'd out. When I try to access them, I'm told, "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of..." 

Would someone please point me in the right direction?

Thanks in advance.

---

### Post by linuxopjemac on 2010-09-05
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95)

---

### Post by vgrisham on 2010-09-05
Thanks. That did the trick. I also turned off journaling in OS X, installed hfsutils in Ubuntu,  and now I can write to the Mac partition as well. 

Now, I need to find out how to write to Ext4 from Mac OS, and from Windows 7 to HFS+ One step at a time, though. I'll start googling.

---

