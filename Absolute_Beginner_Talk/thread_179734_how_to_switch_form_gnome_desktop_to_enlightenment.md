---
title: "how to switch form gnome desktop to enlightenment"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by wetumka_ok on 2006-05-20
Hi, I need some help I'd like to try enlightenment desktop I used synaptic and installed but I don't know how to switch, I'd also like to know how to switch back if i don't like it!

thanks

---

### Post by Cereus on 2006-05-26
Hello.

When you have your login screen go to Sessions and select enlightenment. You can choose to make it a default there or not and you can always go back to Gnome the same way.

Here's a question. When you use enlightenment can you use the left mouse button? You're supposed to be able to left click on the desktop to get access to all the programs etc via a menu. I installed Enlightenment using Synaptic and the left button on desktop doesn't work at all. (left click does work to close windows etc, it just doesn't open the menu).

---

### Post by Cereus on 2006-05-26
I found this thread about no left click.

[http://www.ubuntuforums.org/showthread.php?t=155959&highlight=enlightenment](http://www.ubuntuforums.org/showthread.php?t=155959&highlight=enlightenment)

---

### Post by Cereus on 2006-05-27
Continuing on with how I finally got the left click menu's to finally work with Ubuntu.

Initially I tried to install using synaptic, I installed enlightenment, enlightenment-data and epplets as well as a theme but while enlightenment showed up in the sessions menu at login I never had a left click menu.

Then I tried installing debian packages (.deb) from:
[http://packages.debian.org/unstable/x11/enlightenment](http://packages.debian.org/unstable/x11/enlightenment)

And following the instructions. You probably don't need to do this, from the package manager should be fine but here's the info in case it matters.

I first downlaoded and installed both the enlightenment package and the data package and a theme for fun. It installed fine but didn't show up in the sessions list at the login screen (installing from synaptic worked for this step).

To add enlightenment to session I followed instructions in this forum:
[http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightenment](http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightenment)

(relevant info: 
If you don't see the option, do this (thanks bored2k and bob mitch)

Quote:
sudo gedit /usr/share/xsessions/Enlightenment.desktop

Then put this in the new file:

Quote:
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application

Save the file as Enlightenment.desktop)

So that got me back to where I started, I could start enlightenment but left clicking on the desktop didn't open a menu.

There were lots of comments about the menu's not being built properly and to erase them and rebuild. From the E16 FAQ ([http://edevelop.org/node/92)](http://edevelop.org/node/92)), you need to delete the .menu files and then in enlightenment middle click and select rebuild menus. The .menu files didn't exist (these are in a subdirectory in your home directory: ~/.enlightenment   - the ~ is your home directory and the period in front of the word enlightenment means its a hidden directory). So I rebuilt the menus and they then appeared in my ~/.enlightenment directory but I still had no menu from my left click.

The solution: I'm not sure exactly how this works, enlightenment needs to figure out what to put in that left click menu and that's where the problem comes from. Anyway, the solution was to install a few more packages from synaptic: e16 menuedit2 (and at the same time I installed epplets but I don't think that's significant). Anyway, then when I logged into enlightenment I had a left click menu.

So sorry for the totally newb instructions and that I can't say exactly how things worked, but this is how I got it working for me.

---

