---
title: "Saving hard drive with noatime in fstab"
date: 2008-02-09
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-09
I've been manually editing this option to my /etc/fstab for a long time now with no problems on PPC - even though this isn't a ppc-specific option.

I really run it just to save on hard drive writes, especially on my laptop.  Adding noatime to fstab isn't a new idea, but just wanted to point out that I've been running it without any problems for those who may come across it.  There are many articles about it, I started with this one:

[http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148)

UPDATE:  Hardy now uses a newer version which only performs this function on a weekly basis with *relatime*, but not sure if this is available for pre-hardy installs.


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a5f25c82-3439-433e-9f11-4cfa49e770c8 /               **ext3**    defaults,errors=remount-ro**,noatime  0       1**
# /dev/sda4
UUID=f4d40c0a-c0a7-4857-a131-b81f1475f7cc none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

(Scroll right to see the ,noatime option)

Note that I did not change any default write-caching options for any sort of speed tweak - this was just to save a bit of head movement.

Unless you need forensic-type security of timestamps written when each file was read (!), this could speed up slow drives a little and save some wear and tear.

---

### Post by stream303 on 2008-04-13
Hardy-Beta update:

While I liked to manually insert the *noatime* parameter into my /etc/fstab in the past, it caused problems only for the package statistics "popularity contest" if you decide to participate in that.  (in your sources preferences)

Today, I took a look at my /etc/fstab in Hardy-Beta, and find that **relatime** has been used by default.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199427](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199427)

Interesting!

---

### Post by slacka-vt on 2008-04-13
looks like you're rela-(head-of-your)-time !! Budda-Boom-Cha *crowd claps* :)

~s

---

### Post by Scientia on 2008-05-27
How exactly do you change the system to use noatime?
Sorry, but i'm floundering around in the Linux environment.

---

### Post by stream303 on 2008-06-10
Just use an editor, say nano:

```
sudo nano -w /etc/fstab
```

Ctrl-O to write out your changes, and Ctrl-X to exit nano.

Note the comma preceding noatime.  Be careful if you are new to editing system files.  In fact, back it up first so you can go back in with a rescue shell if you make a big mistake:

```
sudo cp /etc/fstab  /etc/fstab.bak
```

---

