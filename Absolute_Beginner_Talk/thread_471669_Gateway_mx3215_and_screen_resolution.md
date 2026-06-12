---
title: "Gateway mx3215 and screen resolution"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by choox2 on 2007-06-12
Everyone,
   First thanks for taking the time to read this post. I am using a gateway mx3215, but ubuntu by default will not allow me to go into 1024x768. Now this same system running Xorg from FreeBSD worked fine. I currently have windows installed on the box but wondering if anyone has had ubuntu on the system or somthing close. Windows describs the video card as: VIA/S3G Unichrome Pro IGP. Of course I tried all the basics, editing Xorg and adding in the proper resolutions. Still no go. Advice anyone?

---

### Post by xhizors on 2007-07-31
use 

```
sudo dpkg-reconfigure xserver-xorg
```


to edit your xorg. near the end it asks which resolutions would you like. use spacebar to select them.

---

### Post by anewguy on 2007-08-01
I see you already found my how-to, but please don't post on it if possible.  Thanks!:)

BTW - I've tried everything to heck and back and I'm convinced you can't run Beryl or Compiz-Fusion on the MX3215.  If you look at the log file for X, you'll see it gives an error for the v-bios, tries to go VESA mode, and tries BDE modes.  This is if you use the openchrome.org driver.  From everything I've tried, you can't run them in VESA or VESA wiht glx either.  I've posted on this and eveyone seems to say "it can't be done with that IGP".  If you somehow get it working, PLEASE post a how-to and message me also - it would be GREATLY appreciated!!:)

Glad to meet another MX3215 user.  BTW - have you increased your memory, and if so, to what?  Have you tried vmware?  I've got 512MB, but want to go the max (supposedly 1gig for this laptop) to see if I can get vmware to speed up a little.

---

