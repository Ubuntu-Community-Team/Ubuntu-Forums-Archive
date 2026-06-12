---
title: "Installing Dapper"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by kasdaye on 2006-06-07
I'm a long time windows user, and everyone in my family has gotten fed up with its constant instability and vulnerability. I've gotten my parents and sibling to give Ubuntu a shot, so I downloaded the .iso ("ubuntu-6.06-desktop-i386.iso" via torrent) burned the image to CD and booted it.

I choose the first option and it loaded a desktop, but the resolution is at 640x480. This presents a problem, as I cannot see all of the installer. My friend suggested editing a "xorg" file. I looked at the "Modes" and it says 1024x768 and 800x600 are available, but the screen resolution dialog box only has 640x480.

So, I have no idea what I'm doing. ](*,)

---

### Post by J0E0NE on 2006-06-07
I had the same problem as you and someone kindly told me this:
To add resolution's open a terminal APPLICATIONS --> ACCESSORIES --> TERMINAL
type:
sudo dpkg-reconfigure xserver-xorg

pick the default's for everything unless you know better, and when you get to resolution's, add the extra one's you need using space bar when the ones you want are highlighted.

Good luck and note for the changements to work you have to reboot after doing this.

When its done go to system then preferances then screen resolution and it should be in the drop down list.

Good luck :)

---

### Post by kasdaye on 2006-06-07
[QUOTE=J0E0NE]Good luck and note for the changements to work you have to reboot after doing this.[/QUOTE]

I'm not currently at that computer (I'm actually at school...) but I was wondering, since I'm booting from a LiveCD how can I reboot? Wouldn't that negate any changes?

---

### Post by J0E0NE on 2006-06-07
O ye sorry it would damn errr im kinda a newb too ive only had this for like 4 days i didn't think about the ram clearing itself on re-boot sorry man.
Well there are plenty more people here much more experianced than I that can help.

Really sorry about that.

---

### Post by kasdaye on 2006-06-07
Well, thanks anyway, that's half the problem fixed, ne?

I was talking to one of the guys in my class (Computer Programming!) and he suggested:
```
/etc/init.d/gdm restart
```
Would that work?

---

### Post by flurl on 2006-06-07
yes, i think that should work.

you could also try pressing ctrl+alt+backspace. that restarts the X server.

respectively try pressing ctrl+alt++ or ctrl+alt+- which changes the resolution on the fly (never tried this with a live cd, dont't know if it works)

greets

---

### Post by wpshooter on 2006-06-07
I believe you are doing something wrong during the installation.

Are you using the latest RELEASED version of Dapper ?  Probably want to get the DESKTOP version.

If not, download and burn that and it should allow you to boot from the CD and then when you get to the desktop click on the INSTALL icon if you want to install the O/S to your hard drive.  I believe this will probably get your screen resolution straighted out.

P. S. - you might want to do a wipe of the hard drive (if there is nothing on it you want), BEFORE you insert the Ubuntu CD.

Good luck.

---

