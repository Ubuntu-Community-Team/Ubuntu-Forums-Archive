---
title: "What does a Display Manager do? (GDM,KDM,etc)"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-03-13
I'm still a bit of a newbie in some things.
So what does a Display Manager (gdm, kdm, xdm, wdm) do? (please no answers like "it manages the display" :D)
Are they just there for logins? Then why not call them Login Managers?
How do they fit into the grand scheme of of graphical things? (X, *DM, Desktop Environment, etc).

Thanks for educating a newbie :D

---

### Post by question on 2006-03-13
It's the log in screen. If you have ubuntu, you have GDM. For Kubuntu, its KDM.

---

### Post by NeghVar on 2006-03-13
Its more than just the login,.

If im not mistaken, which i very well could be it is the front end for everything, so instead of seeing the old dos style you see a "windows like", I use that term loosely, screen. With Gnome (GDM) and KDE, not sure what it stands for you have native application that work better on that system.

Each one has a different look and feel to it, uses different resources, and has a different way of managing files and such. Sorry if I have confused the issue or am completely wrong, Im still learning all the details myself.

---

### Post by stuporglue on 2006-03-13
> If im not mistaken, which i very well could be it is the front end for everything, so instead of seeing the old dos style you see a "windows like", I use that term loosely, screen. With Gnome (GDM) and KDE, not sure what it stands for you have native application that work better on that system.

GDM == Gnome Display Manager. It is essentially just a log in manager. It does also let users log in and restart/shutdown/etc the computer.

XDM was the first, or one of the first,  display managers, so we'll check it's man page: 
> XDM...prompting for login name
       and password, authenticating the user, and running a &#8216;&#8216;session.&#8217;&#8217;

       A &#8216;&#8216;session&#8217;&#8217; is defined by the lifetime of a  particular  process;  in
       the  traditional character-based terminal world, it is the user&#8217;s login
       shell. 


Logging in to Gnome runs gnome-session. You could achieve the same effect that GDM has by putting a gnome-session in your .xinitrc file and running startx from the console. 

> Each one has a different look and feel to it, uses different resources, and has a different way of managing files and such. Sorry if I have confused the issue or am completely wrong, Im still learning all the details myself.

I think you're mixing Gnome and KDE with GDM and KDM. 

> It's the log in screen. If you have ubuntu, you have GDM. For Kubuntu, its KDM.

That's the default, but you can launch any type of session from any *DM. For example, I could log into an XFCE session, a Gnome session, or a KDE session from KDE OR GDM. There's a menu somewhere on them to choose the session type (if you have that session type installed). 

Happy Linux-ing!

---

### Post by NeghVar on 2006-03-13
Ya, I did a bit of research on it after the fact and realised just how mixed up I got things.

---

### Post by Jucato on 2006-03-13
@NeghVar: care to share some sites you did that research on? :D

So basically, all that a display manager does is to provide a graphical display to login/start a session? 
So it would be possible, for example if I had both ubuntu-desktop and kubuntu-desktop installed, to start Ubuntu through GDM, then go to a virtual terminal, and start a KDM session? (of course, I could just launch KDE through GDM, but I was wondering this was possible).

If I understand it correctly, this is what happens when I start GDM/KDM:
GDM -> starts X -> login -> start session -> start GNOME/KDE
right?

Thanks for the info guys! :D

---

### Post by NeghVar on 2006-03-13
Just Wikipedia:

[http://en.wikipedia.org/wiki/Display_manager](http://en.wikipedia.org/wiki/Display_manager)

[http://en.wikipedia.org/wiki/GNOME_Display_Manager](http://en.wikipedia.org/wiki/GNOME_Display_Manager)

[http://en.wikipedia.org/wiki/Kde](http://en.wikipedia.org/wiki/Kde)

---

### Post by Jucato on 2006-03-13
Oh, so I see we had the same references. :D
But I find stuporglue's explanation more understandable. :D

---

### Post by stuporglue on 2006-03-14
> So it would be possible, for example if I had both ubuntu-desktop and kubuntu-desktop installed, to start Ubuntu through GDM, then go to a virtual terminal, and start a KDM session? (of course, I could just launch KDE through GDM, but I was wondering this was possible).

You probably wouldn't want to run GDM and KDM at the same time. I don't think there'd be a problem, but there wouldn't be a real reason to do so. You can get to both KDE and Gnome from GDM (or from KDM). Theoretically though, I think that yes, you could have KDM and GDM running at the same time.

---

### Post by Jucato on 2006-03-14
oh I see. Of course I won't run GDM and KDM at the same time. Just wanted to know if it was possible. (Ok, maybe I "might", just for fun :D).

---

