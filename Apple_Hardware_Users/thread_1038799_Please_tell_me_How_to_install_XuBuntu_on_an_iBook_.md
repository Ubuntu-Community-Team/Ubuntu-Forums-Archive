---
title: "Please tell me: How to install XuBuntu on an iBook G3 600MHz?"
date: 2009-01-13
forum: Apple Hardware Users
---

### Post by NewsAndHistory on 2009-01-13
So far, I've done the following steps:
**1.** Load Xubuntu into the CD-drive of my iBook G3
**While it was loading I held the "Option" key until a screen appeared, which presented me the option to either choose Mac OS X image or XuBuntu disk-image.*
**2.** Select "US Macintosh" as my keyboard layout.
**3.** I selected _Xubuntu_ disk-image, of corse
**4.** [Here's where I'm stuck] - It cannot detect a CD-ROM drive on my iBook G3

Now I'm not sure what to do. The Xubuntu install disk brings up this message:
> Detect and mount CD-ROM
Please choose whther PC card services should be started in order to allow the use of PCMCIA cards.
Start card services?
<Yes>      <No>:confused: What should I do next? Is there an official Xubuntu guide for installing Xubuntu 8.10 on an old iBook G3? [This Ubuntu tutorial]("http://ubuntuforums.org/showthread.php?t=405934") isn't what I need. I need an official Xubuntu installation tutorial for noobs, who use iBook G3.

---

### Post by mkvnmtr on 2009-01-14
There is a work around in a thread here on this forum for installing 8.10 that you can search for. I really think you will have an easier time installing 8.04 on a ppc machine but others have installed 8.10.

---

### Post by NewsAndHistory on 2009-01-20
Thanks for helping me. I appreciate your patience & kindness. What's wrong with installing 8.10, rather than 8.04 on a PPC machine?

---

### Post by avtolle on 2009-01-20
I've installed both on G4 PPC cubes. The trick for 8.10 to get by the error is to open a new terminal screen by pressing Ctrl+Alt+F2 and typing ```
modprobe ide-scsi
``` then pressing Ctrl+Alt+F1 to return to the other screen and seeing if it continues (it did for me). I presume you are using the "alternate" install iso burned to CD, as I did for Ubuntu. 

Good luck; once you get past the CD drive problem, the next trick you will likely have to undertake is manual editing of the /etc/X11/xorg.conf file.

---

### Post by NewsAndHistory on 2009-01-20
Thanks for helping me. You're very kind & patient.

---

### Post by DaveyJones1 on 2009-01-23
I've gotten all the way to the end of the installation.. only to find an error message stating that Yaboot failed to install.
I keep hearing about having to edit some configuration file, but I'm using the text-only intsaller for Xubuntu and have no idea what I'm doing, hehe. Help?

---

### Post by avtolle on 2009-01-23
Yaboot failed to install? That's a new one on me. Anyway, the configuration file "everyone" is posting about editing is /etc/X11/xorg.conf which deals with trying to get a reasonable setting for your graphics and monitor. However, if yaboot failed to install, I think that's the more important thing for you to tackle at the moment. And, I'll be of no help with this, as I've not run into this particular problem.

---

### Post by DaveyJones1 on 2009-01-23
I fixed the yaboot error. It was a bit of temporary stupidity on my part ;)

Anyhoo, I'm installing Xubuntu (alt ppc iso) on an iBook G3 with the 12-inch display. Is there anyway to change the resolution of the text installer so that it doesn't run off the screen?
...I'm missing about five lines of text at the bottom o_O

---

### Post by avtolle on 2009-01-23
When you boot from the installation cd, there are at least a few options at the boot prompt. Pressing TAB gives them to you. One I use often is "video=ofonly" (without the quotes, of course); IIRC, the entry is Linux video=ofonly at the boot prompt. Give that a go.

---

### Post by DaveyJones1 on 2009-01-25
EDIT--

Alright, I've gotten that working; thanks :)
But now it boots up and I get a gray error box stating that I must use low graphics mode... I get like... 8 bit color on the screen. I edited the xorg.conf so next to driver it says "ati".
I know there's a choice of using ATI, Radeon, R128, or Vesa, but I don't know which one the iBook G3 uses.

Any ideas?

I messed around with the yaboot.conf... not sure if it helped.
Also, should I enter in different HorizSync and VertRefresh values?
If someone else had a G3 and uploaded their xorg.conf, it would be really appreciated ^_^

Sorry for the noobiness :/

---

### Post by Windsurferdude on 2009-06-02
Hello, I am new to all of this. I'm not sure I'm even posting in the right place.  I have an iBook G3 with OX 10.3.9.  It's a nice little machine and I probably shouldn't mess with it. I now have several versions of Xubuntu that I purchased  on eBay.  Here is my question, I understand that it is possible to test the operating system without actually installing it.  I have been searching all over the place and can't seem to find out how to do this.  In this thread the questioner stated that he was unable to reboot into OS X, after he booted from the live cd.  Any wise guidance from someone with patience would be greatly appreciated. Thank you in advance.

---

