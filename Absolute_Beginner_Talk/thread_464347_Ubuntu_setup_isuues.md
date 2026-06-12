---
title: "Ubuntu setup isuues"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by BenLi on 2007-06-04
Hey everyone, I'm a new user

When I attempt to install the 7.04 version it says:

"Failed to start the X server (your graphical interface). It is likely it is not set up properly."

What Caused this problem? I never had this problem before when installing 6.06 or 6.1

---

### Post by thelocust on 2007-06-04
Could be your video card (post you system specs) I would suggest using the alternate install CD.

---

### Post by BenLi on 2007-06-04
Dell inspiron e1505

C2D T7200
2GB
ATI x1400 on Omega drivers (latest)


I actually tried. I downloaded three different cds from three different sources. I also tried the 64 bit version. All of them had this problem... which goes to say the problem is probably in my end.

---

### Post by Cypher on 2007-06-04
But did you download the Alternate CD or the Desktop(Live) CD from those different sources? The Alternate CD uses a text-based installer, so you won't have any issues with the X-server..

---

### Post by Mazza558 on 2007-06-04
> **BenLi said:**
> Dell inspiron e1505

C2D T7200
2GB
ATI x1400 on Omega drivers (latest)


I actually tried. I downloaded three different cds from three different sources. I also tried the 64 bit version. All of them had this problem... which goes to say the problem is probably in my end.

So I assume it brings you to the command line after saying this? Does it tell you to login?

---

### Post by Krosis on 2007-06-06
I too, am having the same problem.  I tried installing Ubuntu on my Laptop this morning and got the exact same error.

Dell Inspiron E1505
ATI Radeon Mobility X1300

I **did** use the alternative CD to install Ubuntu, and the installation completed fine.  When I rebooted to try it out, it gave me the same error.  And something to do with my Boardcom Wireless Card.  I have searched the forum about that error, but it seems I actually need to be able to boot up Ubuntu without problems first.  Right now, it tries to boot up like normal but then gives me the X server error.

"Failed to start the X server (your graphical interface). It is likely it is not set up properly."

Ideas?

---

### Post by tchoklat on 2007-06-06
[http://www.ubuntux.org/x-server-problem-during-install](http://www.ubuntux.org/x-server-problem-during-install)

---

### Post by Krosis on 2007-06-06
Thanks, a lot of great posts in there.  I decided to do a re-install of Ubuntu on my Laptop (although I probably did not need to) just to be sure, so I'll try the solutions found when it's finished.

Thanks again for the link.

---

### Post by Krosis on 2007-06-06
Following the given tutorial, I cannot even begin for some reason.  It's asking me to login.  I assume the correct login is the user name and password I entered during installation.  For some reason it's telling my "Login incorrect".  It was also telling me this before I tried to re-install, I just assumed I miss typed something.  This time, I know I didn't and yet it's still telling me that my login is incorrect.

Missing something?

One thing, I noticed I can put in the user name fine "tim" but when it comes to put in my password, it will not let me type unless I press enter, and then the password.  I have thought, could it be thinking that I'm leaving my password blank?  That might be it.  For some reason it will not let me type in the Password: field.  It's not something DUH like Num Lock, don't worry.  It will not only not let me type numbers, but letters aswell.

Any ideas?

Need to be able to login before anything. ;)

- **Update**: Login problem solved.  Attempting to fix X server problem.
- **Another Update**: X server problem solved using [this tutorial]("http://ubuntuforums.org/showthread.php?t=399913").  Best of luck BenLi.

---

