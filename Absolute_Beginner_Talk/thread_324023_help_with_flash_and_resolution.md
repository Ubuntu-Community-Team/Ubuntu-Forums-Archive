---
title: "help with flash and resolution"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by 1fastredsc on 2006-12-23
I just got ubuntu 6.10 working smoothly, did the easy ubuntu installation. But then firefox would ask me to get flash on certain websites, then i went through the "average user install" for installation of proprietary stuff ( like flash ). So i figured things should work, but websites i go to still ask me to install flash, and i also can't adjust my resolution. My only two options are still 800x600 and 640x480.

---

### Post by Ecthelion on 2006-12-23
_For your resolution problem:_

> My only two options are still 800x600 and 640x480.


You will have to reconfigure your xserver:

Backup your old configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back
```
If something goes wrong and you have no x after this just do this to have your old configuration back:
```
sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf
```

After backing up, reconfigure:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions you know, leave the other on the default answer
When you have to choose the resolutions, add those you know your screen can handle

After this, restart your xserver:
```
sudo /etc/init.d/gdm restart
```

_For flash_
I think I just used [automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38") to install these things.
Altough I wouldn't recommend it since my brother told me that it isn't a good idea.
Something about changing stuff I wouldn't want changed.
Everything just works fine though.

---

### Post by houstonbofh on 2006-12-23
Your video card did not detect properly.  What kind is it?

For flash, you need to enable the other repositories, and install the flash plugin non-free.  Or you can use automatix, or easy-ubuntu.  I find easyubuntu a little cleaner, but without as many features as automatix.  (But it leaves your systems files alone...)

---

### Post by 1fastredsc on 2006-12-23
My motherboard has a built in ati express i believe. As far as repositories go, which ones are recommended for ubuntu?

---

### Post by raul_ on 2006-12-23
For Flash:

go to this site [http://labs.adobe.com/technologies/flashplayer9/]("http://labs.adobe.com/technologies/flashplayer9/") download, then copy the files to your firefox/plugins folder and restart firefox

---

### Post by 1fastredsc on 2006-12-23
Ok, fifth time around was a charm i guess, it finally decided to behave and work. -thanks

---

