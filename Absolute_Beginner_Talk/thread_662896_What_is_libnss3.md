---
title: "What is libnss3"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-09
Hi there. I'm wondering, just what the heck is libnss3?

Iv seen a few people having problems with it, and when I try to install Sunbird it tells me that there is a conflict with this file. Sunbird installs, but there is no icon in the menu system for it, and running it from the command line just gives me pages of blurb and finally a horrible black and white Sunbird appears, unusable, and has to be terminated.

Is there a new (old) version of this file that I can download and install?

Cheers

Max

---

### Post by reckless2k2 on 2008-01-09
a quick google produced this:

[http://linux.about.com/cs/linux101/g/libnss3.htm](http://linux.about.com/cs/linux101/g/libnss3.htm)

---

### Post by MaxVK on 2008-01-09
Yes, I read something similar by finding it in Synaptic and checking it out there, but it still means very little to me! I mean *what* is it, and what can be done about it breaking things? Something to do with network security? Okay, so why does Sunbird need it and why is there a conflict between them?

---

### Post by reckless2k2 on 2008-01-09
not sure what or how you are installing but this method worked fine for me:

[http://ubuntu-tutorials.com/2007/10/27/installing-sunbird-05-or-07-calendar-ubuntu-710/](http://ubuntu-tutorials.com/2007/10/27/installing-sunbird-05-or-07-calendar-ubuntu-710/)

---

### Post by lswest on 2008-01-10
if you go to synaptic Package Manager, what version of libnss3 do you have installed? i have libnss3-0d v3.11.5-3 installed, and sunbird.  Both programs have no issues on this computer.  you could try to do ```
sudo apt-get install --reinstall libnss3-0d sunbird
``` which should re-install both packages.  If there is an error doing so, take note of it and paste what you have here.  another thing to try would be to completely remove sunbird, re-install libnss3 and then install sunbird again.

---

### Post by MaxVK on 2008-01-10
reckless2k2, yes thanks, I found that one already and it fails like all the others Iv found so far, presumably because of the same thing (The fails all *appear* to be the same).

lswest, yes, Iv been through this one! ;) Iv hunted about all over the place for several days, and Iv tried quite a few different things, all with no joy. :(

---

