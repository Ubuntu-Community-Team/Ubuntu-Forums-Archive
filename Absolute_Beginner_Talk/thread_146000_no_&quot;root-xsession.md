---
title: "no &quot;/root/-xsession"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-03-17
:( Okay, before I get to the point,let me just say that I have been to several Debian Forums and no one has answered my question.  I am beginner to Ubuntu and Debian and Linux as a whole.  Here is my problem, I have a pc that has Windows XP, Ubuntu and Debian as a triple boot because it three OS instead of..... well you guys know what I am talking about.  Anyways I first installed XP and partitioned all the space I need for all three OS.  XP 40gigs, Ubuntu 25 gigs and Debian 15 gigs.  Installation for XP went well, the installation for Ubuntu went great and the installation for Debian, went okay but when I boot to Debian I end up in terminal mode.  I tried running commant startx and all I get is a gray screen, with my cursor as an X and a small box in the middle with this info:  **no" /root/-xsession no"/root/.xsession file no session manager, no widows manager and no terminal emulators.**  What Am I doing wrong, do I need to install something else.:cry:

---

### Post by chuckyp on 2006-03-17
you need a window manager installed on debian.  It sounds like you did a base system install.  You need to add KDE or Gnome or whatever window manager you want to use.

---

### Post by NeoGreen on 2006-03-17
How do I do that????  I have a Debian (it came with the Debian DVD) book I purchased and it tell me to configure the Xserver.  I tells me to type the following on the command prompt after I log in as root: **apt-get install x-window-system-core**.  Is that it????:confused:

---

### Post by NeoGreen on 2006-03-17
:( Someone please help, I have looked it up on google to see if I could find anything on install the windows manager and KDE or GNOME but I keep getting the run around.  I did find one site that told me to run this command at the prompt:  **update-alternative --install /usr/bin/x-window-manager \ x-window-manager /usr/local/bin wmaker-cvs 50**.  But it didn't do anything.  Then I ran **apt-get install kdenetwork**, this one did run but when I went to type startx, I got the same response as the beginning of the thread.  Someone Please Help!!!!!!:cry:

---

