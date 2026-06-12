---
title: "Upgrade/Reinstall [Resolved]"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-12-18
Hello,

My video is messed up so I only see a black screen when I start Ubuntu.  Can I just download the .iso for edgy eft and burn to CD(I am using Drake now) and restart to upgrade and hopefully fix this problem?

---

### Post by benuski on 2006-12-18
You can, but you need to burn the CD iso into a new cd.  If you have a dual boot with Windows, or a another  computer with windows, great!  Just use that.  If you need to do it through the command line though, try this:

```
wget http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-desktop-i386.iso
```

Thats just one mirror, there are plenty others out there.

Then do ```
     cdrecord -v -pad speed=1 dev=0,0,0 ubuntu-6.10-desktop-i386.iso  
```

That should burn the cd for you.  Then keep it in there, restart, and the live cd should pop up.

---

### Post by aysiu on 2006-12-18
You can only upgrade with the Alternate CD or the internet.

You **cannot** upgrade with the Desktop CD. The Desktop CD can do only a clean reinstall.

Have you tried this?
Control-Alt-F1 (switch to terminal)
Log in
```
sudo dpkg-reconfigure xserver-xorg
``` (answer the questions as best you can--if you don't know the answer, go with the defaults)
Control-Alt-F7 (return to graphics mode)
Control-Alt-Backspace (restart X server)

---

### Post by brandoncolorado on 2006-12-18
Thanks!

The reconfigure worked, I used -phigh because there were too many options.  I have an NVidia card, but that didn't work, so I used Vesa and that worked.

---

