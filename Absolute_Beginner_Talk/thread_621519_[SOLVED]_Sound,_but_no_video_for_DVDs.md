---
title: "[SOLVED] Sound, but no video for DVDs"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by mubelhor on 2007-11-23
I've tried to follow the advice in several threads, but I'm not finding a fix.  I installed gxine, libdvdnav4, libdvdplay0, and libdvdread3.  I opened a terminal session and typed in: sudo /usr/share/doc/libdvdread3/install-css.sh.

I pressed System-Preferences-Removable Drives and Media, clicked on the Multimedia tab, and in the Video DVD Discs command box typed: gxine -S dvd:/ and then closed.

When I insert a disc into the DVD drive, it's recognized and starts playing, but I get only sound.  Clicking aroung on various menu choices at some point produced this:

---

### Post by CCNA_student on 2007-11-23
I am also having problems with playing DVD's on Linux. I also did those same things you did to no avail. The only thing I can suggest is going into add/remove under applications, search for VLC,and install it. I found that unlike Totem Movie Player in can at least play some movies. It is odd. The Windows version of VLC player can play any DVD I put in it but the Linux version of VLC player only plays some DVD's, which is better than none at all. Hopefully some has this figured out. That is all for now.

---

### Post by mubelhor on 2007-11-23
> **CCNA_student said:**
> I am also having problems with playing DVD's on Linux. I also did those same things you did to no avail. The only thing I can suggest is going into add/remove under applications, search for VLC,and install it. I found that unlike Totem Movie Player in can at least play some movies. It is odd. The Windows version of VLC player can play any DVD I put in it but the Linux version of VLC player only plays some DVD's, which is better than none at all. Hopefully some has this figured out. That is all for now.

I've just iinstallled VLC, but I don't understand which file I should be selecting when I open that program.  I feel like such an idiot.

---

### Post by Flying caveman on 2007-11-23
you may also need libdvdcss2 and win32codecs

---

### Post by CCNA_student on 2007-11-23
After you put the disc in, open VLC player, click on file, and then click on open disc. I should add 
one more thing. To make sure that VLC can play all DVD's use the command:
 sudo apt-get install ubuntu-restricted-extra
  sudo /usr/share/doc/libdvdread3/install-css.sh
in the command line. You need this file to get past some encryption. VLC can only open some discs on its own in the Linux version. If the top line does not work then just use the bottom command. Someone who knows much more about Linux than me helped me out. Here is the link to where I got my help from.   [https://answers.launchpad.net/ubuntu/+source/totem/+question/18414](https://answers.launchpad.net/ubuntu/+source/totem/+question/18414) 
I hope that this works for you. If not email me at [email]limondirk@yahoo.com[/email] or ask the person who helped me out.

---

### Post by mubelhor on 2007-11-23
> **CCNA_student said:**
> After you put the disc in, open VLC player, click on file, and then click on open disc. I should add 
one more thing. To make sure that VLC can play all DVD's use the command:
 sudo apt-get install ubuntu-restricted-extra
  sudo /usr/share/doc/libdvdread3/install-css.sh
in the command line. You need this file to get past some encryption. VLC can only open some discs on its own in the Linux version. If the top line does not work then just use the bottom command. Someone who knows much more about Linux than me helped me out. Here is the link to where I got my help from.   [https://answers.launchpad.net/ubuntu/+source/totem/+question/18414](https://answers.launchpad.net/ubuntu/+source/totem/+question/18414) 
I hope that this works for you. If not email me at [email]limondirk@yahoo.com[/email] or ask the person who helped me out.

I a brief glimpse of some cover art, but then just sound - no video.  I already have the suggested files installed.

---

### Post by zabien1970 on 2007-11-23
I've had varios problems getting my dvd's to play while running compiz, not a solution but a temporary fix I've found is to type  metacity --replace, (two minus signs)

---

### Post by zabien1970 on 2007-11-23
I've had varios problems getting my dvd's to play while running compiz, not a solution but a temporary fix I've found is to type  metacity --replace, (two minus signs) in the terminal  alt+f2

---

### Post by mubelhor on 2007-11-24
> **zabien1970 said:**
> I've had varios problems getting my dvd's to play while running compiz, not a solution but a temporary fix I've found is to type  metacity --replace, (two minus signs) in the terminal  alt+f2

I was sure that I replied to your suggestion  a couple of hours ago.  I was watching a movie!  Thanks!  That worked!

---

### Post by zabien1970 on 2007-11-24
Glad to help, that drove me crazy for the longest time

You should mark this as solved

---

