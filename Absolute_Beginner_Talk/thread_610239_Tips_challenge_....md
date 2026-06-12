---
title: "Tips challenge ..."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-11-11
In order to help all of us learn of interesting tips and add-on enhancements, 
lets post our favorite discoveries.



I'll start with one:

Add "Open in Terminal" as a right-click menu selection in Nautilus file browser - useful when you need to access the command prompt at the current directory:

sudo  apt-get  install  nautilus-open-terminal

 
Carl

---

### Post by Iceni on 2007-11-11
Press and hold the "alt" button to move a window.

---

### Post by SOULRiDER on 2007-11-11
+1 on the "Open Terminal Here" dialogue.

My contribution: netspeed-applet. It shows your curresnt download/upload speed in your gnome bar. KNetLoad is similar but for KDE.

---

### Post by gn2 on 2007-11-11
sudo apt-get install ubuntu-restricted-extras

---

### Post by Pumalite on 2007-11-11
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by benerivo on 2007-11-11
If you've got lots of ram, then add```
vm.vfs_cache_pressure=10
```to /etc/sysctl.conf (and reboot). Open a big app such as OpenOffice, Amarok or Google Earth for a second time and it will load from ram rather than from the hard drive.

---

### Post by TadH on 2007-11-11
if you have compiz enabled with my mouse i can press mous key 3 and hold it and the cube zooms out by itself, better then using ctrl+alt+click

---

### Post by oldos2er on 2007-11-11
Another Nautilus gotta-have is 'Open as Administrator.'

 sudo aptitude install nautilus-gksu

 Oh, and localepurge.

---

### Post by cwmoser on 2007-11-12
YouTube download tool:

sudo  apt-get  install  youtube-dl

Usage example:

$  youtube-dl    -o “name of file.flv”    [http://youtube.com/123tyg](http://youtube.com/123tyg)


Carl

---

### Post by gn2 on 2007-11-12
> **cwmoser said:**
> YouTube download tool:

sudo  apt-get  install  youtube-dl

Usage example:

$  youtube-dl    -o “name of file.flv”    [http://youtube.com/123tyg](http://youtube.com/123tyg)


Carl

Perhaps a simpler option is to drag the tool on [[COLOR="SandyBrown"]this page[/COLOR]]("http://www.keepvid.com") into your Firefox bookmarks, click on this bookmark when viewing YouTube and it will generate a download link.

---

### Post by jharbert on 2007-11-12
Highlight to Copy.  Middle Click to Paste.

---

### Post by cwmoser on 2007-11-13
Speedier menus:
--------------------

Put the following at the end of your .gtkrc-2.0 file:

gtk-menu-popup-delay = 0



Cut down on amount of swapping:
----------------------
If you have the ram:

In file:  **/etc/sysctl.conf** enter:

# PERFORMANCE:  cut down on swapping 
vm.swappiness=5 


.. or you can test from the command line:
sudo  sysctl  -w  vm.swappiness=0


Carl

---

### Post by acl123 on 2007-12-07
A good one off lifehacker today:
With the desktop showing, press forward slash ("/")

---

### Post by Teknyk on 2007-12-07
> **gn2 said:**
> Perhaps a simpler option is to drag the tool on [[COLOR="SandyBrown"]this page[/COLOR]]("http://www.keepvid.com") into your Firefox bookmarks, click on this bookmark when viewing YouTube and it will generate a download link.

You don't need any app for getting vids from youtube.
just let it completely cache and then drag it from /tmp to your desktop (or where ever)

*EDIT*
Oh yeah, my fav so far is sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
Credit for that is not mine. I found it here on the forums but forget who to give credit to. Sorry whoever that was

---

