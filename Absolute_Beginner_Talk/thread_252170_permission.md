---
title: "permission"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-06
I downloaded a souce file and I wanted to send it to the trash.  But it wouldn't let me delete some of the file which had a 'lock' symbol on it. How do I get the permission to delete these files?  I am setup as adm.

Also what is the easy way to compile a source file?

---

### Post by electricshoes on 2006-09-06
In a terminal you could do

```
sudo chown username filename
```

That should change the permisions of the file to you and not root.

I think you can also just

```
sudo rm filename
```

> Also what is the easy way to compile a source file?

Is there a README in the folder, it may be a compressed file that you have to uncompress to get the folder, in there it will probably have a readme file with configure and make instructions

---

### Post by Omnios on 2006-09-06
Hi counting on what the ownership is for the files which is probably root you can either use sudo rm in terminal or  use sudo nautilus to open a root window to remove the files.

Installing software, also has some very good links from other users
[http://ubuntuforums.org/showthread.php?t=171822](http://ubuntuforums.org/showthread.php?t=171822)

Also see know your terminal commands thread
[http://ubuntuforums.org/showthread.php?p=990636#post990636](http://ubuntuforums.org/showthread.php?p=990636#post990636)

---

### Post by aysiu on 2006-09-06
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by jbumgar on 2006-09-07
Thank you all for your help!  I decided to take the easy way out for now and went to the [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) site which I found very informative. Little by little I'm learning from you guys.

---

