---
title: "Resolution Issue"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by Screwworkn on 2006-02-06
In my gnome I try and change to 800x600 or 640x480 and the screen is all scrambled.  Any idea how to fix this or where area I can start looking at to fix it. 

This is the second install I've done, on the first one I only selected 640x480 on the install screen for gnome and it worked fine.

I am using an ati 8100xt video card.

thanks for the help
Chris

---

### Post by Screwworkn on 2006-02-06
I tried running 

sudo dpkg-reconfigure xserver-xorg

When I do and select on the just 640x480 or just 800x600 resolution I can run in that rez.  But whenever I select multiple resolutions I can't switch between them. 

Any thoughts?

Chris

---

### Post by nik on 2006-02-06
Can you post the contents of your /etc/X11/xorg.conf file? Might see whats wrong there...

---

