---
title: "power pc g3 display problem"
date: 2010-08-08
forum: Apple Hardware Users
---

### Post by hotballz87 on 2010-08-08
im not much of a mac person, so i need to ask this before i do anything.

im installing ubuntu onto a friends ibook, but am first running it live off the disk. it runs well, except for one thing, the display has a problem, i guess it seems like its tiled on the monitor, instead of fullscreen, it has a full desktop taking about 2/3 of the monitor, a sliver of the same desktop right below it, and a line of black to the right. 
anyone have any ideas? any help would be nice, before i kill mac osx on this computer

---

### Post by linuxopjemac on 2010-08-09
You need to adapt xorg.conf. Just install and we can fix it later.
[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)

---

### Post by hotballz87 on 2010-08-11
ok, so i installed the newest version of ubuntu onto the ibook, and ran all the updated. i went to the linked page, but dont know which xorg.conf file to use, or how to do it

edit: its an iBook from 2001, if that helps at all, :P

---

### Post by linuxopjemac on 2010-08-12
give me the link in everymac.com please

Do you have X at all or are you working in the console right now?

---

### Post by hotballz87 on 2010-08-12
[http://www.everymac.com/systems/apple/ibook/stats/ibook_600.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_600.html)

this is the mac here^^

i do have x up and running, here is a picture of what the desktop looks like right now

[IMG]http://pic40.picturetrail.com/VOL383/1952593/21777676/390758810.jpg[/IMG]

---

### Post by linuxopjemac on 2010-08-12
ok, do the following in a terminal:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If it complains that there is no such file, ignore it, that's ok. Then:

```
wget http://mac.linux.be/files/xorg/ibook1.txt
sudo mv ibook1.txt /etc/X11/xorg.conf
```

Then reboot and hopefully your X works fine. If not, let me know.

---

### Post by hotballz87 on 2010-08-12
yes, thanks so much, it works great now.

---

