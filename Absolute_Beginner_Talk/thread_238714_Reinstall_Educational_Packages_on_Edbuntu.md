---
title: "Reinstall Educational Packages on Edbuntu"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by ScouseMouse on 2006-08-18
Hi This is my first post and first real delve into Linux land.  So please don't flame me, with not knowing all the technical bits.

Just installed on an old IBM PC Edbuntu for my children. PC is not connected to the Internet. All was fine until I thought I would load the game KBattleship onto it.  I found the package's on the Ubuntu site along with dependencies in the deb format.  Here is the list of dependencies that I obtained from a machine at work running 32bit Ubuntu.

kdelibs4c2a_3.5.2-0ubuntu18.1_i386.deb
kdelibs-bin_3.5.2-0ubuntu18.1_i386.deb
libarts1c2a_1.5.2-0ubuntu1_i386.deb
libkdegames1_3.5.2-0ubuntu3_i386.deb
libopenexr2c2a_1.2.2-4ubuntu2_i386.deb

Extracted each OK working my way up the list, until I came to the following package

kdelibs-bin_3.5.2-0ubuntu18.1_i386.deb

I received back a message unable to install run this command in the terminal, sorry forgot actual command but it had the -f switch.  The next minute it said removing games.  Then all the Educational  just uninstalled themselves.:confused: 

Help How can I reinstall all the Educational software from the Ebuntu CD, or do I have to find away of obtaining necessary packages to download from Internet?

---

### Post by kepos on 2006-08-18
Just go to synaptic and select those packages and aplay the changes. I think it shuld work without downloading, because ubuntu keeps copy of every package downloaded(including ones that where already there when system was installed).
If i'm wrong someone please correct me.

---

### Post by ScouseMouse on 2006-08-19
Cheers for that I'll give that a go, perfect english.:cool:

---

### Post by ScouseMouse on 2006-08-20
I tried using synaptic and slecting required packages and all I received was a message informing me that packages were not available from repositories.  then I remembered that I could mout the CD through Synaptic.  Then I was able to this to install required packages.  Cheers for your help.:)

---

