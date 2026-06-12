---
title: "can't find executable"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by manishraichur on 2006-11-14
Hi
I have installed route planner software from the repositories,but i am not able to find the executable for it.I searched in /usr/bin..but was not able to locate it.

any help
manish

---

### Post by bulldog on 2006-11-14
Hit ALT->F2 and fill in the name of the app and see if it runs.

---

### Post by CatKiller on 2006-11-14
As bulldog says, it's normally just the name of the program. If you look at the Properties window in Synaptic for the package you installed, it will tell which files it installed.

It's possible that you will have a menu entry for it, but that the menu needs refreshing. **killall gnome-panel** may cause it to appear.

---

### Post by justplayin on 2006-11-14
I tried this myself and found, that you had to install the packages **routeplanner** and **routeplanner-gnome**. You could install them like this on the console
```
sudo apt-get install routeplanner routeplanner-gnome
```
You can run the programm by typing
```
grplan
```
in the console. It's not a very intuitive name after downloading a package called routeplanner.
I found this by searching the package routeplanner in the "ubuntu package search" in firefox [here.]("http://packages.ubuntu.com/edgy/gnome/routeplanner-gnome") There you can click on [list of files]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=routeplanner-gnome&version=edgy&arch=all") for the package routeplanner-gnome and you'll see, that it installs a file named "grplan" in "/usr/bin/", that's a path where links to executables or executables themselves get installed.

There's a project at sourceforge called [routeplanner.]("http://sourceforge.net/projects/routeplanner/")

The program doesn't look very intuitive to me.

---

### Post by manishraichur on 2006-11-14
Thanks a lot guys..
I was looking for file name starting with "route" or "planner" or something like that.

Thanks to your help i found it.
Is there any other alternative to routeplanner software ( something like Street and trips )

Manish

---

### Post by justplayin on 2006-11-16
Sorry, I can't help you on that one. I use online services like [Google Maps]("http://maps.google.com/") or [Map24]("http://www.map24.com/") for route planning.
I recently found a nice plugin for Firefox, that shows you the best route to an address that you copy from website via Google Maps. It's called [Map This]("https://addons.mozilla.org/firefox/1886/") and comes in very handy, if you have to measure the distance from your location to any other location you find on a website.

---

