---
title: "gtk-gnash eats my CPU"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by GabrielWolff on 2008-04-16
I am running firefox and the System Monitor only on my machine right now and got 100% CPU usage.

The process gtk-gnash (which I got 4 or 5 times on the list of Processes) eats between 77%, 15%, and 12% of my CPU.

What is it and how can I kill it?

---

### Post by Gen2ly on 2008-04-16
Nash, oops gnash, it's very very late :) is a flash based player.  it doesn't come installed by default.  ru sure you don't know about it?? :)

---

### Post by farueulogy on 2008-04-16
It is the thing that lets you play youtube videos. You can replace it with the non-open source adobe plugin which I've found to run quicker and be less cpu intensive.

To remove it (You'll probably want to close firefox)
System>Administration>Synaptic package manager>Search for "gnash">Right click the "gnash" package and "mark for complete removal"

To install the adobe alternative
You might need to activate more sources as it's non-open
System>Administration>Software sources
I'm not sure exactely which you need to tick but if you tick all:
(main) (universe) (multiuniverse) and (restricted)
and click close it should autoupdate packages
then go to
System>Administration>Synaptic package manager>Search for "flashplugin-nonfree">Right click the "flashplugin-nonfree" package and "mark for installation"

and that should be everything :) After installing you can untick the boxes in software sources if you like.

---

### Post by GabrielWolff on 2008-04-16
uninstalled gnash, right, I **did** install it

tried to install the nonfree flash player.

I seemd to do that, and claimed to be successful, Only thing is: the last lines of the installation were:
```
Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

checksum failed?

What do I do?

---

### Post by gandaran on 2008-04-16
> **GabrielWolff said:**
> uninstalled gnash, right, I **did** install it

tried to install the nonfree flash player.

I seemd to do that, and claimed to be successful, Only thing is: the last lines of the installation were:
```
Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

checksum failed?

What do I do?
 
the flashplugin package is broken due to a adobe flash update, but you can still install flash by other ways.

1. download the tarball from the adobe site and run the installer ([http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/))

2. disable the ubufox firefox addon, go to a flash site, click install when you get the flash plugin missing message (this is the best way to install but uninstall first the broken flashplugin-nonfree package)

3. just unpack the adobe tarball and copy/paste the libflashplayer.so file to the appropriate folder

---

