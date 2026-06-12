---
title: "A few problems with Ubuntu server"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by plr4ever on 2007-12-02
Hi, I'm new to Ubuntu server, although i have been using desktop for ~6 months.

Anywho, i installed Gutsy server on a not-to-old computer, and got it running pretty well, with the exception of a few speed bumps, it's running OK. However, i keep running into a few re-occurring problems that really mess up the functionality. 

First of all, When i boot, the computer takes about 2 minutes on the "Load hardware drivers" command, before failing. It recognizes things like the CD drive, but it doesn't want to play nice with a desktop environment.

Second, when i log in, i get this error:
-bash: /dev/null: permission denied

And that shows from the top to the bottom of the screen, but i just get a command line up w/ ctrl + c.

Third: I cannot start x, xubuntu, or any thing related with a GUI. 

When i enter "startx" i get a list of lines starting with (EE) with errors in them, and then :
[B]
Fatal Server Error:
addscreen/screeninit failed for driver 0

XIO:  fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.
[/B]
Then it resets to the command line. 

When i try loading xfce4-session, i get this:
[/B]
(xfce4-session:3721): Gtk-warning **: cannot open display:
[/B]

I would really like to be able to load a GUI, as i am not nearly proficient enough to do EVERYTHING by command. I really would appreciate any amount of help, so share any ideas you may have!

---

### Post by m0biu5 on 2007-12-04
plr4ever:

Check :
[http://www.linuxquestions.org/questions/slackware-14/addscreenscreeninit-failed-for-driver-0-35019/](http://www.linuxquestions.org/questions/slackware-14/addscreenscreeninit-failed-for-driver-0-35019/)

Seems like your xorg.conf file might be incorrect. Also, I believe you should use startxfce, or something along those lines, for XFCE.

---

### Post by plr4ever on 2007-12-04
> **m0biu5 said:**
> plr4ever:

Check :
[http://www.linuxquestions.org/questions/slackware-14/addscreenscreeninit-failed-for-driver-0-35019/](http://www.linuxquestions.org/questions/slackware-14/addscreenscreeninit-failed-for-driver-0-35019/)

Seems like your xorg.conf file might be incorrect. Also, I believe you should use startxfce, or something along those lines, for XFCE.

Thanks but that didnt fix it. 

And startxfce is not a command. startx means start X11 server, not xfce.

---

### Post by m0biu5 on 2007-12-04
I know what startx does. I am not running ubuntu at the moment, so I can't check to see if they've changed XFCE at all, but from [http://wiki.xfce.org/faq:](http://wiki.xfce.org/faq:)

> There are three different ways to do this:
You can just login with the command startxfce4


Can you paste the screen section of your xorg.conf maybe?

---

### Post by plr4ever on 2007-12-05
I wish i could get the output of it, but it wont work as i am running the server thru SSH. I think i will be able to suffice with the command line for now, but if anyone can help on the other issues, that'd be great.

thanks!

---

