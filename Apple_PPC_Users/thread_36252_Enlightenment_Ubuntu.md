---
title: "Enlightenment Ubuntu"
date: 2005-05-22
forum: Apple PPC Users
---

### Post by Xbot on 2005-05-22
I have tried every tutorial I could find online - none have worked.

I am trying to install Enlightenment on Ubuntu. I've tried using Synaptic, but with no joy - it never enters the session list. What am I doing wrong and how can I fix it?

I'm no Linux Guru, but I figure I can install a session (after all my attempts with Fluxbox and XFCE, I know my directories ;) ).

---

### Post by ola on 2005-05-22
A silly question, but have you restarted GDM after you installed enlightenment?
Otherwise it might not appear in the list..?

---

### Post by krusbjorn on 2005-05-22
Have you done step 2 and 3 in this guide?
[http://www.ubuntuforums.org/showthread.php?t=20216&highlight=e17](http://www.ubuntuforums.org/showthread.php?t=20216&highlight=e17)

---

### Post by Xbot on 2005-05-22
[QUOTE=ola]A silly question, but have you restarted GDM after you installed enlightenment?
Otherwise it might not appear in the list..?[/QUOTE]


Yes and yes. Except for the part of installing eutils, but that isn't in the Ubuntu list. It appears in the sessions list by the way, but it goes into Gnome.

---

### Post by Xbot on 2005-05-23
Bump

---

### Post by Xbot on 2005-05-24
Bump. Help, please.

---

### Post by supernaut on 2005-05-24
Did you follow the tutorial linked? If so, it doesn't work because there are no PPC packages. People REALLY need to start specifying the available architectures when writing tutorials. It's seriously annoying, and if this is the case I feel your pain.

Otherwise, type "enligtenment" at a terminal to check that E even exists on your computer. Your problem is most likely that it isn't there. You'll probably have to build from CVS. 
On that note, has anyone written a script for building e17? I want to install it, but there so many packages that you have to build in a specific order that I can't be bothered. ;)

---

### Post by ensenadaubuntulover on 2005-05-30
[QUOTE=Xbot]I have tried every tutorial I could find online - none have worked.

I am trying to install Enlightenment on Ubuntu. I've tried using Synaptic, but with no joy - it never enters the session list. What am I doing wrong and how can I fix it?

I'm no Linux Guru, but I figure I can install a session (after all my attempts with Fluxbox and XFCE, I know my directories ;) ).[/QUOTE]



go to

cd /usr/share/xsessions/

then 

sudo cp /usr/share/apps/kdm/sessions/enlightenment.desktop

somewhere here in ubuntuforums posted that and I havent thank him but it works!!!

---

### Post by Yggdrasil on 2005-12-29
Well folks, rather new to linux been using breezy for about a month now and getting used to it. I got enlightement installed, everything seemed to work.
I had no left clik menu so i edited one up and that works swell and all. I am not into manualy editing every single application that i want to put in the list so im wondering is there a way to automate  making the  file.menu using the existing gnome menus ?? Or a way to copy out the gnome menus and manualy insert them into e. It would also be nice if when i added a package it added it.
THanks.:KS

---

### Post by jakes on 2006-01-10
[QUOTE=Yggdrasil]Well folks, rather new to linux been using breezy for about a month now and getting used to it. I got enlightement installed, everything seemed to work.
I had no left clik menu so i edited one up and that works swell and all. I am not into manualy editing every single application that i want to put in the list so im wondering is there a way to automate  making the  file.menu using the existing gnome menus ?? Or a way to copy out the gnome menus and manualy insert them into e. It would also be nice if when i added a package it added it.
THanks.:KS[/QUOTE]

Well, I've just done this as well and I'm also missing a usable Gnome menu. I found this tool, which does what we need it to in E17: [http://sourceforge.net/projects/e17genmenu](http://sourceforge.net/projects/e17genmenu)
But I've been unable to find anything similar for E16 (assuming that's what others are using, as it's installable from universe (I think it's universe anyway).
So, if anyone does know how to auto-generate the gnome menus in enlightenment we'd be mighty pleased - manually editing every entry would be way too tedious, and you'd have to do it every time you installed something new.
Thanks,
jakes.

edit: sorry - only just realised that this wasp posted in the Macintosh/PowerPC forum - don't know if that makes the app linked to above useful here - I'm using an x86 version of Ubuntu.

---

### Post by chammi on 2006-02-01
Here's a *very* basic (some might even go so far as to say "silly") question: 

What happens when you install another Window manager like Enlightenment (or KDE for that matter)? Does it just replace GNOME, or do you have the option when you start up  to select your WM (in the way that you can select "failsafe" at the Ubuntu welcome screen)? I'm curious to try E., but am still pretty happy with GNOME and don't want to scrap it completely.

---

### Post by chammi on 2006-02-03
The answer is "yes," you still get the Ubuntu log-in screen--but you can choose to start an Enlightenment session from it. I also discovered that I didn't really like Enlightenment and am back in GNOME.

---

