---
title: "Need to change the default run level of Xsession"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by seeker50 on 2008-01-11
Hi

I'm trying to make a MultiseatX and everything was OK until I found that I need to select a default run level of 3 for the Xsession when the computer boot; i've tried everything I found in the Ubuntu's help and in various forums and I still can't do that.

I found in another post that with the command telinit can do that, but I need to boot in level 3

I'm using the Ubuntu 7.10, Gutsy Gibbon version.

Does anybody can help me to change the default run level for the Xsession?

Thanks a lot for your help.

---

### Post by twright on 2008-01-11
"dpkg reconfigure xserver" or some variant might work

---

### Post by seeker50 on 2008-01-12
Thanks twright

I've study dpkg reconfigure xserveras you suggest, but it seems that doesn't work, today I'm going on trying to solve the problem or waiting for another posibilities.

Thanks anyway

---

### Post by twright on 2008-01-12
hi,

try " gksudo gedit /etc/inittab" :KS

the default runlevel should be stored in there

---

### Post by seeker50 on 2008-01-12
Hi

I tried "gksudo gedit /etc/inittab" and this was the message that appears:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gksudo:10339): Gtk-WARNING **: cannot open display:  

I'm going to go on looking for the way to do it

Thanks again for your help

---

### Post by oldos2er on 2008-01-12
Ubuntu doesn't use inittab, it uses upstart. See [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/) .

---

### Post by seeker50 on 2008-01-17
Thanks oldos2er for your interest

I tried with upstart, as you say and the system crash.

I reinstall ubuntu and I'm still searching for the solution to my problem.

Thanks anyway

:confused:

---

### Post by jeradaj on 2008-01-18
If you use the alternate install CD I'm pretty sure there is an option for CLI install. That should install and run CLI only. I don't know if that will help but you may want to try that.

---

### Post by Kulgan on 2008-01-18
just apropos
> Hi

I tried "gksudo gedit /etc/inittab" and this was the message that appears:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gksudo:10339): Gtk-WARNING **: cannot open display: 

I'm going to go on looking for the way to do it

Thanks again for your help

That won't work if you are working in the tty, or if it is a remote connection. Use nano instead: 
```
sudo nano /etc/inittab
```
Ctrl-X to exit (and save). 

Of course, it won't help with inittab, since ubuntu got rid of that in Gutsy, but at least you will be able to edit the right files when you find them.

---

### Post by seeker50 on 2008-01-19
Jeradaj, the CD I got to install Ubuntu is the Ultimate Ubuntu Edition and don't have any options for the installations.

Kulgan, I'm working with your idea, I hope there will be the solution.

Thanks a lot for your ideas and help, I'm working on it.

---

### Post by seeker50 on 2008-01-21
At least I find the file that needs to be adjusted.

When I was checking the upstart found it.

The file is: "/etc/event.d/rc-default"

Change the two lines where appears telinit from 2 to 3.

And it's done!

Thanks a lot all of you for your help and ideas.

:lolflag:

---

