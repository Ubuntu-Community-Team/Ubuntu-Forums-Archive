---
title: "The Sleuth Kit: compiling from the most recent source"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by thantos on 2007-02-25
I don't know if this is the right place for this but, since I am basically a new user to ubuntu here goes:

I am trying ot setup the current server version of ubuntu (6.06) with the sleuth kit.  According to the install file in the sleuth kit I have everything I need to compile from source using "make", but when I try to install it I get three error messages, the last of which is "error 3: no-perl", which is not true, since I installed it myself (via apt-get).

The reason I am trying to do this is to learn first hand about how filesystems work and the like.  I am also planning in the future to make a linux based disk recovery usb stick, which would be useful for work.  So if there is a better program that ubuntu supports immediately in a command line environment, this would be good information that solves the problem of having to compile the current sleuthkit source.

Since I am currently far away from the computer that I need to do this on, I will be updating this post to include the full error output for further debug help.

---

### Post by ramjet_1953 on 2007-02-25
If you haven't done so already, you may also need to install the Perl development libraries.

Regards,
Roger 8)

---

### Post by aysiu on 2007-02-25
You mentioned compiling from the most recent source. So I'm assuming you know you can get *sleuthkit* from the repositories, right? Version 2.03 is available for Dapper if you have the Universe repositories enabled.

---

### Post by thantos on 2007-02-25
Thanks to both of you.  The first post will help me compile a latter version of sleuthkit and the second one will give me a version for now.

---

