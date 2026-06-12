---
title: "Dialup Modem: essential but impossible?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Coburn on 2006-04-26
Trying to set up 5.10 since early March.

Using dual boot WinMe to access Net.  My only sources for code are the CD and dialup/download/copy/paste (or eq.).  For large files I have access to borrowed cable connection & CDRW.

Intel537EP driver won't compile.

<apt-get install> won't recognize kernel headers on CD, or install them.

Synaptic _has_ installed them, but <make 537> still exits w/ errors.

gcc 4.0 is default, but have 3.4 installed from source.  This online session I ran across <CC=gcc-3.4...> and will try it soon.

I am stuck, following the instructions in the Dialup Modem HowTo, on compiling the driver.  Either something is wrong with my kernel header install, or with gcc, or I missed something.

Oh, and by the way:
EXTRAVERSION=
(This is a fresh install)

Reading the scanModem documentation is like trying to trace the path of one noodle in a whole bowl without using your hands.  I am beginning to wonder if any of it applies.[http://ubuntuforums.org/images/smilies/rolleyes.gif](http://ubuntuforums.org/images/smilies/rolleyes.gif)
:rolleyes:

It mentions Debian distros use kernel-kbuild-3.n.  I take it Ubuntu is not included.

Thanks,

Coby

---

### Post by gr0kzer0 on 2006-04-26
For a start, that stuff about kernel-kbuild is a crock. I read that Ubuntu _does_ need it, but I couldn't find it anywhere. So I went ahead without it, and it all worked fine.

My advice, try to find a .deb of the driver youy need. I found one, at [http://phep2.technion.ac.il](http://phep2.technion.ac.il), and it installed without a hitch.

Look at the thread in Networking about 2.6.12-9-386 drivers. My post is near the end, and describes my trouble-free driver installation for my Lucent/Agere winmodem.

---

### Post by Coburn on 2006-05-03
Good advice.  I will check it out.

Lately I have been frustrated that developers and documenters do not seem to display the teamwork you speak of.  Changes are made to the software, e.g. dropping kernel-kbuild from the system and from Universe, and the writers of documentation do not update their material.  On a monolithic work team like MS, that would be _de rigeur_.  

Reading your post, however, gives me a new perspective.  I _am_ on the development team, in a sense.  I am in the position of reviewing changes, testing them, and communicating the results where appropriate.

Thanks,

Coby

---

### Post by Coburn on 2006-05-10
Just a note:

There does not appear to be a .deb of the driver for the Intel 536/537 chipset family, either at linmodems or intel.com.

---

### Post by Coburn on 2006-05-10
Thanks, guys.

I'm online now.

Thanks for the help, both in person and through your previous posts.

---

