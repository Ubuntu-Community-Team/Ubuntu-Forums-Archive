---
title: "Delayed Boot and Reversed Drivers"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Bionic Apple on 2007-12-15
I have two problems:

1.  When Ubuntu boots up, it displays no GUI and only text displaying Proftpd at the top (a FTP program) and some other status messages.  The screen waits 3 seconds then refreshes.  It does that about 5 times before I get to the login screen.  What can I do to fix it?

2.  I recently took out my old video card (with restricted NVIDIA driver installed) and put in a new one.  Needless to say, Linux didn't recognize the new card and ran in a "Low-Graphics Mode".  So, I uninstalled the driver and then installed it again.  Guess what?  It still ran in "Low-Graphics Mode".  So I uninstalled the driver, which caused it to actually work with no "Low-Graphics Mode" displaying.  So here is the question:  Is the driver present?  If it is, how can I make the restricted drivers menu say it is enabled?  If it isn't, how do I get the driver?

Please help me!

---

### Post by Bionic Apple on 2007-12-15
Can someone help me?

---

### Post by Bionic Apple on 2007-12-16
I am sorry, but I cannot find the answer myself.  Help would be appreciated!

---

### Post by Partyboi2 on 2007-12-16
Have you tried using envy to install the correct restricted drivers for nvidia?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Another thing is to check your /var/log/Xorg.0.log for any errors that might be able to tell you whats going on.
I take it you have reconfigured xorg when you change drivers over?
```
sudo dpkg-reconfigure xserver-xorg
```
try it again and try "nv" if not try "vesa"

---

### Post by Bionic Apple on 2008-02-27
Envy worked and I was happy, but yesterday I decided to get the latest nvidia drivers for another problem I have.  I went through the install provided with the driver,then Ubuntu didn't recognize that I had a graphics card (again).  So, I decided to see if using Envy's uninstall and install feature would work.  It didn't.  It gave me a driver, but the horrid ProFTPd message keeps coming up now.  But, that is not the reason why I am bumping this thread.  You see, *I can't login*.  Everytime I enter my username and password, the ProFTPd message comes up and brings me right back to the login screen.  Failsafe GNOME works, but I need the real GNOME for obvious reasons.  By the way, the command that is above crashed on me.  Also, it is way too long and tedious.  Any suggestions?

---

### Post by Bionic Apple on 2008-02-27
I can't use Ubuntu properly without your help!  To be more specific:  Is there a special way to remove a manually installed nvidia driver?  Or is it simply removing the packages?  And how do I get rid of those ProFTPd messages?

---

### Post by Bionic Apple on 2008-02-27
A much needed bump.

---

### Post by Bionic Apple on 2008-02-28
Bumpety Bump.

---

### Post by Partyboi2 on 2008-02-28
boot into recovery mode and run
```
dpkg-reconfigure xserver-xorg
``` and choose the correct driver you are using so if its a nvidia graphics card you can choose nv and answer the rest of the questions.
The message you are getting about ProFTPd is something to do with the ProFTPd package  which is a ftp application. If you do not need it then remove it
```
sudo apt-get remove profrpd
``` or post the exact message you are getting.

---

### Post by Bionic Apple on 2008-02-28
Here are two pictures of the problem.  The dark one shows the main message that always shows up, while the flash-on one shows it more clearly with some other random error message:

[IMG]http://img86.imageshack.us/img86/1393/dsc00735lo9.jpg[/IMG]

[IMG]http://img509.imageshack.us/img509/7382/dsc00740jd5.jpg[/IMG]


Oh and by the way, removing the proftpd package did not work.

---

### Post by Bionic Apple on 2008-02-29
I think it is the command after the local boot scripts file that messes everything up.  Just my guess.  Also, using the 'complete removal' tool in synaptic for gproftpd and proftpd removed the first line from the pictures above.  Everything else is intact.  Could it be a program that is set to run automatically on start up?  Failsafe Gnome prevents start-up scripts and it works...

---

### Post by Bionic Apple on 2008-02-29
Bump

---

### Post by Bionic Apple on 2008-02-29
I need some help!  Even though I do have a working /home directory, I don't want to reinstall Ubuntu because of a problem I get all the time.

---

### Post by Bionic Apple on 2008-03-01
I just reinstalled Ubuntu, but it took about 5 minutes because I had my /home directory as a seperate partition.  So, I do not have the problem anymore, but I *need* to know the problem because it happens all the time to me.  To be super-specific, could it be this (C): [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by Bionic Apple on 2008-03-06
Help would be appreciated.

---

