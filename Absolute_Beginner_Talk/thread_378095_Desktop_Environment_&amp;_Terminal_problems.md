---
title: "Desktop Environment &amp; Terminal problems"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Hishgraphics on 2007-03-06
I'm running Ubuntu 6.06 Dapper Drake. This morning upon startup of the computer, I discovered something strange about the desktop environment.

1. All windows have no title bar at the top, which prevents me from clicking off the window, move it around the desktop or resize it.

2. The Panel at the bottom has lost all of its features, such as Garbage Bin, windows switcher, and even the workspace switcher. Trying to put it back from the "Add To Panel" windows (which appears without the title bar too) doesn't seem to work.

3. I managed to drag and drop Windows Selector onto the panel, but upon clicking, it says "No Windows Open" even when this Firefox I'm using to write this post here is up and running.

4. I hit Terminal on the top panel to get to command line interface, but I got an error message which says : Could not launch application. Details: Failed to execute child process "gnome-terminal" (Input/output error) The icons on the top panel can still launch Firefox, Evolution, et. al. But Terminal is dead.

Anyone knows what is the matter with this computer?

Thanks.

---

### Post by Hishgraphics on 2007-03-06
Trying to reinstall Gnome panel, etc. I was told:

> E: /var/cache/apt/archives/gnome-session_2.14.3-0ubuntu1_i386.deb: unable to stat `./usr/bin/gnome-wm' (which I was about to install)
E: /var/cache/apt/archives/gnome-terminal_2.14.2-0ubuntu1_i386.deb: unable to stat `./usr/bin/gnome-terminal' (which I was about to install)

How can I [COLOR="Red"]sudo aptitude install ubuntu-desktop[/COLOR] without using terminal?

---

### Post by wesley_of_course on 2007-03-06
Wesley here ;

  Top left : System - Administration - Synaptic Package Manager .

   Have fun !

---

### Post by seshomaru samma on 2007-03-06
I dont know what's wrong with your computer , I'm sure other people can help you but if you want to reinstall Gnome and can't get into a terminal , you might want to try booting into rescue mode ( i think that what's it called , it's the second option on the grub menu that appears on boot , you might need to press Esc if your grub menu is hidden)
the rescue mood will take to a command line interface so any gnome problem you have will not affect it.

---

