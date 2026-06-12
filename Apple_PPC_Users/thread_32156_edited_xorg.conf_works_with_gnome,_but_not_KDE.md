---
title: "edited xorg.conf works with gnome, but not KDE"
date: 2005-05-06
forum: Apple PPC Users
---

### Post by muzza on 2005-05-06
I recently installed ubuntu on my PowerBook 550 and had trouble with the screen resolution.  I fixed the problem as seen [in this thread.](http://ubuntuforums.org/showthread.php?t=28586&highlight=horizsync) To summarise, I added these lines
HorizSync 30-70
VertRefresh 50-160 
and also commented out the UseFBDev line (Why?  Cause the man on the 'net told me too!) and Ubuntu let me set the proper resolution.

So I thought I'd give Kubuntu a go as I'm a sucker for eye candy, and I've had more success with K3B on the x86 machine with Kubuntu.

Here's where the trouble begins.  Only 640x480 resolution again.  Hey, I know this one.  Edit my xorg.conf.

But there's no 'gedit'.  I don't know how to edit xorg.conf without root priveleges outside the console.  Tried replacing 'gedit' with 'kate', but no go.

So I apt-got 'gedit'.  Edited xorg.conf, didn't copy the original 'cause I already knew it worked, logged out, logged in, still only 640x480.

Reboot.

Can't remember what it said but basically the display was unable to display, and I got a black screen.

I know, should've done sudo cp blah, blah, but I didn't, cause I knew it would work.

But it didn't work and my slowly improving confidence with Linux is shattered and I feel really at home typing this booted in OSX.  But I don't want to give up on Linux.  And I'm determined to get Kubuntu happening.  (stubborn old fool)

Here's the questions;

How do you edit xorg.conf with root priveleges in KDE?
Why does the edited xorg.conf file fix the resolution in Gnome, but screws KDE?
Has anybody got a titanium pbook 550 and got Kubuntu running on it?  Can I see your xorg.conf?

BTW, I tried installing Ubuntu-desktop over Kubuntu earlier today and got the resolution right in Gnome, but the same black screen when I tried to start KDE.

And the dual system was SSOOOO SSLOOOOOOOOWWW!  I've decided to just use Kubuntu, and apt-get synaptic and firefox.

---

### Post by Pineault on 2005-05-06
One answer, 
you can open sudo console and from there launch gedit or kate or whichever editor you want with root privileges, and then find, open, edit, save your file.

This doesn't answer the other question concerning kde vs gnome.

---

### Post by pvz on 2005-05-06
[QUOTE=muzza]I recently installed ubuntu on my PowerBook 550 and had trouble with the screen resolution.  I fixed the problem as seen [in this thread.](http://ubuntuforums.org/showthread.php?t=28586&highlight=horizsync) To summarise, I added these lines
HorizSync 30-70
VertRefresh 50-160 
and also commented out the UseFBDev line (Why?  Cause the man on the 'net told me too!) and Ubuntu let me set the proper resolution.

So I thought I'd give Kubuntu a go as I'm a sucker for eye candy, and I've had more success with K3B on the x86 machine with Kubuntu.

Here's where the trouble begins.  Only 640x480 resolution again.  Hey, I know this one.  Edit my xorg.conf.

But there's no 'gedit'.  I don't know how to edit xorg.conf without root priveleges outside the console.  Tried replacing 'gedit' with 'kate', but no go.

So I apt-got 'gedit'.  Edited xorg.conf, didn't copy the original 'cause I already knew it worked, logged out, logged in, still only 640x480.

Reboot.

Can't remember what it said but basically the display was unable to display, and I got a black screen.

I know, should've done sudo cp blah, blah, but I didn't, cause I knew it would work.

But it didn't work and my slowly improving confidence with Linux is shattered and I feel really at home typing this booted in OSX.  But I don't want to give up on Linux.  And I'm determined to get Kubuntu happening.  (stubborn old fool)

Here's the questions;

How do you edit xorg.conf with root priveleges in KDE?
Why does the edited xorg.conf file fix the resolution in Gnome, but screws KDE?
Has anybody got a titanium pbook 550 and got Kubuntu running on it?  Can I see your xorg.conf?

BTW, I tried installing Ubuntu-desktop over Kubuntu earlier today and got the resolution right in Gnome, but the same black screen when I tried to start KDE.

And the dual system was SSOOOO SSLOOOOOOOOWWW!  I've decided to just use Kubuntu, and apt-get synaptic and firefox.[/QUOTE]
 Or try
sudo nano /etc/X11/xorg.conf
from a console, or from another computer over ssh. This will also work if you have no graphical environment working.

---

### Post by pvz on 2005-05-06
Or try
sudo nano /etc/X11/xorg.conf
from a console, or from another computer over ssh. This will also work if you have no graphical environment working.

---

