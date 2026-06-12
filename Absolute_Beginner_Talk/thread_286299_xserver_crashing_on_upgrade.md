---
title: "xserver crashing on upgrade"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by schreck494 on 2006-10-27
I just upgraded to 6.10 last night and xserver is having some problems.  When I start Ubuntu I get an error message saying that xserver had a problem and to restart gdm when xserver is fixed. So I used this from recovery mode: ```
dpkg --configure -a
dpkg-reconfigure xserver-xorg
dpkg-reconfigure gdm
reboot
```
After the reconfigure xserver-xorg, do all of the defaults and it still won't work.  The error from the xserver log says fatal error no screens found.

---

### Post by cptjaben on 2006-10-27
I had this same problem, I managed to fix it for me by typing:

sudo dpkg-reconfigure -phigh  xserver-xorg 

at the command prompt.

---

### Post by schreck494 on 2006-10-27
I tried that one too, and it still doesn't work.

---

### Post by David_T on 2006-10-27
Do you have an ATI Radeon graphics card?
Have you seen this?
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/28925](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/28925)

---

### Post by schreck494 on 2006-10-27
That says that it is for dapper, does it still matter on edgy?  I have an ATi Radeon 7000 IGP.

---

### Post by David_T on 2006-10-27
I should have listed the source of the link:
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

I solved it on our ubuntu machine here at work by doing
apt-cache search radeon
..and then installing what looked like the main xorg/radeon package, and then doing 
sudo apt-get dist-upgrade
again to install all the X packages that had been held back.  Sorry I know that's a little vague, but that's what I remember doing and I can't check right now.

---

### Post by schreck494 on 2006-10-27
On the ATi proprietary driver website, it says that my graphics card is too old to be supported.  So I think I need something other than the fglrx driver.  Any idea which one I need?

---

### Post by PPAAUULL on 2006-10-27
I had the same problem but it was because the packedges were held back and then I had to reconfigure the config file.

---

### Post by schreck494 on 2006-10-27
So what do I need to do to reconfigure the config file.

---

### Post by ninjad on 2006-10-27
This is what i used to fix xserver. I just used it about 5 minutes ago

```
sudo apt-get install xserver-xorg
sudo reboot
```

and that fixed my xserver problems this time

---

