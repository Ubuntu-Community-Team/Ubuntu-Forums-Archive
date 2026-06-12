---
title: "SOLVED Help! I have borked my xorg.conf"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by gergtreble on 2007-08-04
Sigh....

I was trying to do [this](http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/).

Unfortunately in trying to do it ive messed up my xorg.conf I tried editing the additions I put in and removing them but it still didnt work so I did:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
```

In the command line, followed by:

```
sudo dpkg-reconfigure xserver-xorg
```

To rebuild my xorg.conf but all I get now after the logon screen is a white screen. 

Help!

---

### Post by agds on 2007-08-04
If you post your xorg.conf as it is now, I'd be happy to take a look.  You may be able to temporarily get a working desktop environment by selecting a "failsafe" session from the menu at the login screen.

---

### Post by NilsE on 2007-08-04
You should have one or more xorg.conf with a bunch of numbers after the name (dates).  Try renaming it to just xorg.conf and you should be good to go. You may have to rename the xorg.conf if it is there first.


Easiest to do it in nautilus by entering

gksudo nautilus

in a terminal then going to the /etc/X11  folder.

---

### Post by gergtreble on 2007-08-04
Ok. I only have command line access at the moment. And Im posting this from the windows partition on my hard drive so I dont know how to get my xorg.conf and post it on here. Plus how am I going to get gksudo to work when I cant get an xsession?

I also should point out that stupidly I didnt make a backup. Before I started all this!

---

### Post by gergtreble on 2007-08-04
Ok I have manged to access my ubunu partition via fs-disc on my windows partition so attached is my current xorg.conf

Please take a look at it and tell me how it is still borked! I removed the line I added and it still wont boot!

---

### Post by agds on 2007-08-04
> **gergtreble said:**
> Ok. I only have command line access at the moment. And Im posting this from the windows partition on my hard drive so I dont know how to get my xorg.conf and post it on here. Plus how am I going to get gksudo to work when I cant get an xsession?

I also should point out that stupidly I didnt make a backup. Before I started all this!

Sorry about that.  For some reason, I imagined you could still get a login screen.  You might want to check out the Xserver error log to see if that sheds any light on the problem.

```
tail /var/log/Xorg.0.log
```

If the tail of the file doesn't contain anything interesting, you could view the whole thing.  Just replace "tail" with "less" in the above command.

---

### Post by gergtreble on 2007-08-04
FIXED.

I opened the file in windows. And noticed there was a keybord return on the first line. This was causing the file not to be parsed. I edited it and it worked.

Is this the first time windows has been used to fix an ubuntu problem!?!?

Lesson learned. BACKUP!

---

### Post by agds on 2007-08-04
Fancy that.  Pesky carriage returns&#8230;  Be sure to add "SOLVED" to the thread name, so others can benefit from your experience.

---

### Post by Brunellus on 2007-08-04
thread marked SOLVED.  Good job guys!

---

### Post by gergtreble on 2007-08-04
Groovy! 

I learned a lot today.

---

