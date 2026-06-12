---
title: "Seperate workspace backgrounds"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-19
I did it in Xandros... but how do I have a different background for each workspace in Ubuntu?

background - desktop wallpaper or colours?

---

### Post by m.musashi on 2006-03-19
At the top of the configure background interface there is a drop down that says all desktops or desktop 1, 2, etc. When set to all, they all get the same background. Choose each one and configure as you like.

EDIT: oops, right click the desktop and select configure background to get started.

---

### Post by Gallows on 2006-03-19
Did you do it Xandros under KDE or Gnome?

---

### Post by Kersus on 2006-03-19
I don't have a configure background option.
When i rt. click on the empty desktop I get:

Open Terminal
Create Folder
Create Launcher
Create Document >
Cleanup By name
Keep Aligned
Change Desktop background


There's nothing in change desktop background besides the colours and a selection of wlalpapers (add/remove/stretch/etc.).

I can't find the configure background interface.

---

### Post by m.musashi on 2006-03-19
Sorry, my bad. I'm not on ubuntu at the moment. You want the change desktop background option. Configure desktop might be the kde language.

Hold on, let me get ubuntu up before I give any more bad advice.

EDIT: okay, it sounds like you are using gnome. I have been playing with kde for a while and the configure desktop is for kde. At the moment, I'm not finding a way to do this in gnome. Perhaps it's not quite as easy in gnome. I'll keep looking and maybe someone else can answer. Sorry for the bad advice.

---

### Post by Kersus on 2006-03-19
No worries, I hope this can be done in gnome. Ubuntu is gnome and kubuntu is KDE right?

Well if I had the choice, I'd have started with Kubuntu, but I've invested some time in Ubuntu now and its probably worthwhile to learn gnome for now.  

Anyhow, if anyone knows how to have different desktop backgrounds in each workspace, please let me know!  You would have my gratitude.

---

### Post by m.musashi on 2006-03-19
Actually, it's very easy to do kde in ubuntu (kubuntu is the kde version). If you open a terminal and type ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` you will be able to choose gnome or kde at login via the options (dapper) or session (breezy) menu on the login screen. That is the setup I have. I use whichever suits my whim.

I'm not having any luck seeing how to do this in gnome. Even the configuration editor doesn't seem to have an option.

---

### Post by Kersus on 2006-03-19
Didn't work for me...

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

---

### Post by m.musashi on 2006-03-19
It's probably in a repository other than the default ones. At least that's my guess.

open the sources.list file ```
sudo gedit /etc/apt/sources.list
``` and uncomment (remove the # from infront of) the lines starting with "deb". I'm not sure which repository has the kubuntu desktop but there shouldn't be any harm in uncommenting them all. Just don't remove the # signs from lines with 2. The ones you want to uncomment all look like URLs.

---

### Post by ice.man on 2006-03-19
when u use ssh is there away to run a program is a new terminal

---

### Post by Kersus on 2006-03-19
EDIT: Wait - I didn't update again... will and let you know what happens...

---

### Post by m.musashi on 2006-03-19
It sounds like you don't have an active internet connection but since you are posting here that doesn't make sense. Are you using the ubuntu machine to post here? If not, does that machine have a working network?

I get that or similar error when I've lost networking for some reason.

I also noticed that the repositories in the list refer to "hoary" which was the released verion prior to breezy. The newest, dapper drake, will be release in April or May. No reason you can't use hoary but if you didn't intend to you might think about upgrading.

The more I think about it, you shouldn't have to change your sources list. Kubuntu should be in the main repository. Your earlier error about kubuntu-desktop not being found is probably related to the problem above - not finding the repositories.

---

