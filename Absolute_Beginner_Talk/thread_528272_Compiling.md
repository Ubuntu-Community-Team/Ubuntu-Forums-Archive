---
title: "Compiling"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by dedhandi on 2007-08-17
Hi!

Another post about compiling I'm afraid, checked out the other posts but they don't specifically answer my question. And this is really basic stuff I'm afraid!

When compiling apps, I manage to get ./configure to work but make always gives me the response "No targets specified and no makefile found" whatever it is I am trying to compile. Having read up a little bit, some people say that you need to get hold of other tools such as build-essential. So I tried "sudo apt-get build-essential" and got the response "E: Invalid operation build-essential".

I've installed various different flavours of Ubuntu over the last couple of months and whatever I do, I always seem to get the same result. It's obviously me but I'm always sure to copy code from websites/forums to make sure I don't mis-type things.

Please steer me straight, what the hell am I doing wrong?!?!?!

---

### Post by Steveway on 2007-08-17
What programs do you want to install?
And it is sudo apt-get install build-essential!

---

### Post by dedhandi on 2007-08-17
If that's right, how come I'm getting an error?!

All I'm trying to do is install a theme and to do that I'm trying to install the latest GTK. But whatever it is I try to compile I get the same error. So I figured that maybe I didn't have the right compiling tools, but surely Ubuntu comes with some basic ones for most purposes?

---

### Post by Steveway on 2007-08-17
Look at my post again.
sudo apt-get **install** build-essential
You typed that command wrong!
What theme is it?

---

### Post by dedhandi on 2007-08-17
Ha! What an iditot. I apologise! Shows what copying and pasting from website code can do eh? I'm just trying to install the Murrine engine but after ./configure I got the message "configure: error: GTK+-2.8 is required to compile murrine". So I'm attempting to install that now. And having to work my way backwards to just to get it to fit together!

---

### Post by Steveway on 2007-08-17
You don't need to compile anything!
sudo apt-get install gtk2-engines-murrine
That should install it for you.
You should better learn how to use Synaptic and apt-get.
If that command doesn't work, then enable the universe repo.

---

### Post by dedhandi on 2007-08-17
Yeah I did that too but it didn't seem to work. It probably did to be fair and the issue is elsewhere. Believe me I've been trying to glean some help from posts about Themes too but to no avail. Aside from the Theme issue (maybe I'll start another thread for that!!), make still isn't working for me. That's my main issue at the moment.

---

### Post by Steveway on 2007-08-17
So did that command work? sudo apt-get install gtk2-engines-murrine
And did you install a theme? [http://murrine.netsons.org/index.php?q=last_node/story](http://murrine.netsons.org/index.php?q=last_node/story)
You can just drag-and-drop the tar.gz files into that window where you change your gtk-themes.

---

### Post by dedhandi on 2007-08-17
I should probably point out I'm using Xfce and that method doesn't seem to work. Putting themes into /usr/share/themes doesn't seem to work either.

---

### Post by wirelessmonkey on 2007-08-17
Isn't murrine a GNOME theme engine? (KDE user here, so not sure)  If so, you probably aren't going to get it working in Xfce....

---

### Post by Bachstelze on 2007-08-17
It is a GTK engine, it is used in GTK applications, be that in Gnome, KDE, Fluxbox, fvwm or whichever WM you use.

---

