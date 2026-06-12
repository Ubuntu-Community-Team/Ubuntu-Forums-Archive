---
title: "Wasted evening re-installing."
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-06-29
So I re-installed tonight so I could have all the extras and ease of use that the 32 bit version of 4.10 apparently has over the 64 bit version. Except after a 90 minute install process (had to download 108mb updates) it launched ubuntu...on the command line. And I have no idea how to get the GUI running so after a while I gave up tried re-installing it again without the auto updates so it was quicker and to see if I had missed an option or something. But that one hung when unpacking the x-server. Great. So finally I have had to install the 64 bit version again just to post this!

So my questions are these. 

1)Why is the 32-bit version so different? I would have thought the 64 bit version just allowed larger memory addressing etc.

2) How do I get the 64-bit version to contain all of the ease of use stuff that the 32 bit version has?

3) If question 2's answer is "you can't" how do I launch the GUI (I tried sudo GNOME and various other things I could think of) from the command line?

---

### Post by monchichi on 2005-06-30
1.) The 64-bit version does allow larger memory addressing, better performance, etc.

2.) You can't. The problem is that many codecs and programs that are closed source are only compiled in 32-bit, which you can only *sometimes* use with the builtin 32-bit compatibility libraries. 

3.) Did you get an error about why the X server wouldn't start up? run "/etc/init.d/gdm start" from the command line and see what happens. Or just run "startx". It's possible that something got screwed up during the upgrade or maybe you just need to configure your xserver.

P.S. it's not a wasted night, its a learning experience... and 4.10 is old! why arent you using 5.04 (hoary)?

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=gammyhand]. But that one hung when unpacking the x-server. Great. So finally I have had to install the 64 bit version again just to post this![/QUOTE]

From my vast experiance, I'm almost positive you had a bunk install CD (I've made a few). Bunk CDs always have xserver problems. Why not install hoary?

> 1)Why is the 32-bit version so different? I would have thought the 64 bit version just allowed larger memory addressing etc.

They are pretty much the same. Its the third party support (closed drivers, w32codecs, flash) that is different. Thats because 64 bit is new.

> 2) How do I get the 64-bit version to contain all of the ease of use stuff that the 32 bit version has?

You install the 32 bit one inside the 64 bit one. chroot.

> 3) If question 2's answer is "you can't" how do I launch the GUI (I tried sudo GNOME and various other things I could think of) from the command line?


First get a working install CD. Be sure to burn it at low speeds.

---

