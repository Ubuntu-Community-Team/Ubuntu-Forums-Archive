---
title: "getting back my desktop"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by griff01 on 2006-07-30
Hi

Any way to reinstall from the command line

root@griff-laptop:~# 

or recover from a duffers move?!

I installed Ubuntu Dapper Drake - first move from XP - liked the look, but the screen resolution was poor.

Went back and ran auto config (advice from community doc)during which I changed the keyboard from US to UK

Doh!

Numerals not working on the keyboard so couldn't goback. Turned off turned on and now it can't load the desktop (has a go)

Second reboot I'm looking at the command line as above.

Cheers

Griff

---

### Post by taurus on 2006-07-30
If there is a problem with X, you can reconfigure it from a command line with

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by griff01 on 2006-07-30
ok here goes...

---

### Post by taurus on 2006-07-30
> **griff01 said:**
> ok here goes...
Good luck (cross your fingers & probably toes too).

---

### Post by griff01 on 2006-07-30
Hmmm - shouldn't have crossed them whilst using the keyboard.

apparently x server is now disabled.

Going back in.......

---

### Post by griff01 on 2006-07-30
OK - the last good step I get to is the colour depth.

When I enter OK for this option I get thrown back to the command screen (configuring xserver-xorg still above it) and the following message

xsserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in/etc/x11/xorg.conf.20060730231343
griff@griff-laptop:#$

best bet from here is.....

Griff

---

### Post by taurus on 2006-07-30
What color depth did you use?  Did you choose 24?  What does your /etc/X11/xorg.conf look like anyway?

---

### Post by griff01 on 2006-07-30
Yep chose 24

re what does it look like - not sure I'd recognise an answer to the question!

Going to reboot and see what I get from here..

cheers

Griff

---

### Post by taurus on 2006-07-30
You can view the content of /etc/X11/xorg.conf with the more or less command...

```

more /etc/X11/xorg.conf

```

---

### Post by griff01 on 2006-07-30
xorg failed to load

got the splash screen with log file info
(==)Log file:"var/log/xorg.0.log"
(==) Using config file "/etc/x11/xorg.conf"

Back to for another round ....

---

### Post by taurus on 2006-07-30
> **griff01 said:**
> xorg failed to load

got the splash screen with log file info
(==)Log file:"var/log/xorg.0.log"
(==) Using config file "/etc/x11/xorg.conf"

Back to for another round ....
Look at your /var/log/xorg.0.log to see what the error is...

```

more /var/log/xorg.0.log
(hit the space bar for the next 24 lines...)

```

---

### Post by griff01 on 2006-07-30
Yeaay - the drums have sounded the birds have sung!

Back in thanks - taurus!

Griff

---

### Post by taurus on 2006-07-30
> **griff01 said:**
> Yeaay - the drums have sounded the birds have sung!

Back in thanks - taurus!

Griff
So the fat lady has sung!!!  :p

---

### Post by cebobbitt on 2006-07-30
I had this same problem, after you answer all the questions to the best of your ability and you get to the command line interface that says that you might be overiding a previous configuration, just type in startx and see if that works, it worked for me

---

### Post by griff01 on 2006-07-31
That's one for the future!

---

