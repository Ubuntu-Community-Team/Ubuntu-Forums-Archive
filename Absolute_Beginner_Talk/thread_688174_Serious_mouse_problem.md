---
title: "Serious mouse problem"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by sarum on 2008-02-05
Hi, I have an optical (PS2) mouse which has recently worked OK then stalls and won't move. Restart,  and back to the begining and it works; - 'till next time.
My '_Official Ubuntu Book'_ (page 226) says 'sudo dpkg-reconfigure xserver-xorg'  This I have done and in my ignorance have done badly because I now have no monitor. [COLOR="Red"]Black Screen of Nothing.[/COLOR]
I speak to you now through Puppy(a good, if not a best friend) Live CD on this machine - so it all works; but how, please,do I get back to my Ubuntu.

---

### Post by spiderbatdad on 2008-02-05
in the future ```
sudo dpkg-reconfigure -phigh xserver-xorg
```takes all that configuration out of your hands, so you are less likely to botch anything. Have you tried booting into safe graphics mode or recovery mode?

---

### Post by sarum on 2008-02-05
Thanks Spiderbatdad, I typed in your suggestion and got 'xserver-org is not installed' sounds serious. But what I have done is; inserted Ubuntu CD which I used to install 7.04 - so I'm now on live CD with monitor and internet working well. Is there anyway I can reinstall from this CD without wiping my files. I have not recently backed up anything (woe is me) Your help is very much appreciated.........sarum

---

### Post by jrothwell97 on 2008-02-05
'xserver-org is not installed' is quite serious - it means the basis for the GUI has gone.

Nevertheless, the system is still there and intact. Try running aptitude from the command line, and selecting xserver-org and all dependencies. You may need to reinstall GNOME afterwards, but you may not.

Good luck.

---

### Post by emarkd on 2008-02-05
xserver-org is a typo.  The package is called xserver-xorg.  The Ubuntu Live CD is not an update CD, so you'll wipe everything that you don't back up if you install from it again.  Before you do that, though, check /etc/X11/ for backups to your xorg.conf file.  There may be some with timestamps after them, like xorg.conf.20080122 or something.  You could cp one of those to xorg.conf and see if that fixes your problem.  Don't mv it or you lose your backup copy!!

---

### Post by sarum on 2008-02-05
Thankyou both for your help. I'm afraid it's all got a bit beyond me and I'm going for a clean install. May I add that I've been with Ubuntu since 4.1(I dont recall it's name) and have relied heavily on this site for  help. This is the first time I have felt unable to figure out 'HowTo'. I'm in my 70's so I'll not be losing anything of great importance. My nearby daughter's address book will be similar to mine and Bookmarks are on my Google account.
All is not wasted -  as soon as I'm up and running again I'll start a regular back-up.
Thanks again to you both and to those who have helped me in the past..........sarum

---

