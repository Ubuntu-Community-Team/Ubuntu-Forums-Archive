---
title: "xorg.conf &quot;Dell Inspiration 1420&quot;"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2007-08-11
I can't boot into the X server on my Ubuntu dell inspiron 1420 Laptop.  I keep trying to reconfigure it but it doesn't work, and I can tell that it is because the /etc/X11/xorg.conf file is wrong. I often get the no screens found error

Does anyone know the proper configuration of this file?  Just so you know, I have a Intel Graphics Media Accelerator X3100 on the computer.

---

### Post by eapache on 2007-08-11
Please post the nature of your problem.

---

### Post by purplearcanist on 2007-08-11
Just edited my first post.

---

### Post by eapache on 2007-08-11
The driver for this card is buggy at the moment (it has been fixed for the next version though). After the error message, it should give you a command line. Type```
sudo nano /etc/X11/xorg.conf
```and scroll down to the section that lists your graphics card (if it isn't there, there should be a section under 'generic video card'). Change the driver from whatever it is to 'vesa', ctrl-o to save, ctrl-x to exit, then```
startx
``` and you should be good to go.

---

### Post by notwen on 2007-08-11
My Inspiron 1420n has came out of the box w/ 1440x900 resolution. To enable my preferred Beryl usage, I simply enabled pre-released updates in my software sources and checked for updates.  Were you having issues w/ your screen out-of-the-box or did you modify something prior to your video issues?  =]

---

### Post by purplearcanist on 2007-08-11
I installed some updates and modified a couple of files.
Thanks for telling me the right driver eapache, now it works again.:)

I almost got frusterated for a second.

---

