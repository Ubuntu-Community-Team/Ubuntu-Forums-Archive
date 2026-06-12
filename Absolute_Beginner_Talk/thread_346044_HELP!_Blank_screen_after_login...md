---
title: "HELP! Blank screen after login.."
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by tyler_roach on 2007-01-25
Hi,
I've been using Ubuntu exclusively for about a week now, and I'm enjoying it a lot... However, I just had a huge problem today:
I logged out, and when I tried to log back in, after the GDM login screen, I get nothing. I can see my mouse cursor and the background but nothing else!

I can go into recovery mode, type "startx" and login as root, and everything comes up all right... (except the internet.)

I'm thinking maybe this has to do with some alterations I made to the theme... I also tried a while ago - unsuccessfully - to install Beryl and XGL... could that have anything to do with it, even though I haven't had any problems before?

I would greatly appreciate it if anyone has any advice... I'm writing now from Windows, which I hoped I wouldn't have to go back to...

Thanks

---

### Post by housam on 2007-01-25
Try to fix the internet connection and update the x-org files through the update manager . it may help solving the problem.

---

### Post by tyler_roach on 2007-01-25
Exactly how do I do that? Can it be done through a command line?

---

### Post by jamyskis on 2007-01-25
It may be worth going into recovery mode and renaming the GNOME config directories (at least temporarily) to see if that fixes your problem. Go into your home directory and type:

mv .gnome .gnome.bak
mv .gnome2 .gnome2.bak
mv .gnome2_private .gnome2_private.bak

I may have missed a couple of directories there, but try that, boot up normally and see how that goes.

---

### Post by housam on 2007-01-25
Open terminal in the recovery mode and type
```
nano -Bw /etc/X11/xorg.conf
```

Disable the Composite extension by adding the following lines to /etc/X11/Xorg.conf:

Section "Extensions"
Option "Composite" "false"
EndSection

This may help restoring Gnome

---

### Post by tyler_roach on 2007-01-25
I tried moving the .gnome files, but nothing happened.

In my xorg.conf file, it says "composite" "Disabled" instead of "false".. Does that make a difference?

I also tried changing my video card drivers - didn't work.

I can get online through a failsafe terminal; I did apt-get update, but that didn't work either..

I also installed ubuntu-desktop... didn't work.

Any other suggestions? Is there some way I could totally reload GNome without having to do a total reinstall?

Thanks for the help.

---

### Post by housam on 2007-01-25
try this code from the recovery mode:
```
dpkg-reconfigure xserver-xorg
```

---

### Post by tyler_roach on 2007-01-25
Thanks..

I already tried:

sudo dpkg-reconfigure -phigh xserver-xorg

And it didn't work.. If I do it without the "-phigh" option, what is the difference? I've done that before and I get a thousand different pages and I don't really know what I should change?

However, I was able to try 

startx

from a terminal and I got the following error message:

xinit: connection to X server lost
xauth: error in locking authority file /home/ali/.Xauthority

Hopefully that makes sense to somebody?

Thanks

---

### Post by tyler_roach on 2007-01-25
Is there any way I can either a) change the Gnome theme settings back to default from the command line or

b) create a new user account (with sudo powers) from the command line? (when I try to create one from the root account it says i dont have permission.)

---

### Post by jd65pl on 2007-01-25
> If I do it without the "-phigh" option, what is the difference

The -phigh option just configures the graphical aspect of xorg by omitting the option you will pass through a series of screens configuring all aspects of xorg.

---

### Post by tyler_roach on 2007-01-25
I did it without the -phigh option, and still nothing.

---

### Post by tyler_roach on 2007-01-27
I found a (sort of) solution. I just purged my system of Gnome using the instructions found here:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

But adding "--purge" after the "remove" command.

Then I installed KDE:

sudo aptitude install kubuntu-desktop 

And that's working for me now. So although I had to get rid of Gnome, at least I didn't have to do a fresh install... I wish there had been a less drastic way of doing this.. I'm also not sure that if I did a

sudo aptitude install ubuntu-desktop

Gnome would work again.

---

