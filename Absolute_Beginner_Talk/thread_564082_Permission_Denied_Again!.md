---
title: "Permission Denied Again!"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Arukas on 2007-09-30
Hello,


  I just formatted my HDD with gparted to EXT3, so XP and Windows can use it.  However, when I try to open and write to it in Linux, it says I don't have permissions.

  I would like to remove all permissions, so I may write freely and read from it freely.  Windows has the extra drivers to allow it to write and read from it.  So that problem is taken care of.

-Arukas

---

### Post by julian67 on 2007-09-30
> **Arukas said:**
> Hello,


  I just formatted my HDD with gparted to EXT3, so XP and Windows can use it.  However, when I try to open and write to it in Linux, it says I don't have permissions.

  I would like to remove all permissions, so I may write freely and read from it freely.  Windows has the extra drivers to allow it to write and read from it.  So that problem is taken care of.

-Arukas

here's what to do assuming your user name is arukas and your drive is mounted at /media/disk 

```
sudo chown -R arukas /media/disk
```

chown =changes the owner and -R makes it recursive so everything on /media/disk becomes owned (and hence writeable) by you.

You will need to unmount and remount the disk for this to take effect.

---

### Post by Arukas on 2007-09-30
okay, the command worked


I can put folders in it.  But it will not let me create folders?   How do i fix that?

-Arukas

---

### Post by julian67 on 2007-09-30
I never had that problem....did you unmount and remount the drive?

---

### Post by Arukas on 2007-09-30
Yes I did


-Arukas

---

### Post by Arukas on 2007-09-30
I just restarted my computer, and now I am back at square one.  It says I don't have permission again.  

-Arukas

---

### Post by Arukas on 2007-09-30
I just redo did the code thing and now i it works fine, I dont' know what happened.


So my question is, do I need to type in the code every time I boot up?  or is it permanent?  If it isn't permanent how can i make it that way.?



-Arukas

---

### Post by julian67 on 2007-09-30
should be permanent after the first time you did it.....but I think I made an error, I missed a slash so instead of 

```
sudo chown -R arukas /media/disk
```

do this:

```
sudo chown -R arukas /media/disk/
```

and unmount and mount. I apologise for missing that out.

---

### Post by Arukas on 2007-09-30
That's okay, I just glad, I am in the right direction.  I like the security, on Ubuntu, but when I am the "Prime" user, it gets frustrating to sometimes to figure out, how to access something.


-Arukas

---

### Post by julian67 on 2007-09-30
> **Arukas said:**
> That's okay, I just glad, I am in the right direction.  I like the security, on Ubuntu, but when I am the "Prime" user, it gets frustrating to sometimes to figure out, how to access something.


-Arukas

It can be extremely helpful to have a reference guide. If you have a good book to hand then it's usually going to be quicker than posting to a forum, and also will let you explore freely. I like Wiley's Linux Bible books. I started serious Linux use with openSuse and Wiley's Suse Bible and it was a brilliant resource. The Linux for Dummies books are excellent too, and the o Reilly books. I have the O Reilly Linux Pocket Guide Essential Commands as well, it's great for quick lookups.  There are of course several excellent Ubuntu-specific books including the official one.

I'd also check out the [Linux Reality]("http://www.linuxreality.com/") podcasts. These must be the ultimate podcast for Linux newbies.

---

