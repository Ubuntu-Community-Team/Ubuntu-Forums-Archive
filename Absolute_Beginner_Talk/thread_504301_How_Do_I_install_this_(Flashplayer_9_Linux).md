---
title: "How Do I install this??? (Flashplayer 9 Linux)"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-19
I just downloaded the file from the adobe website.... Now how do I install it? I looked around at a couple posts but they were a little confusing...

one said kubuntu is for macs??? Im running it on a compaq!

---

### Post by borris.morris on 2007-07-19
Alright, what file extension is it?

If it's a .deb then do "sudo dpkg -i ~/Desktop/name-of-file.deb"

If it's a .bin or .run then do "chmod +x ~/Desktop/name-of-file.bin" and then "~/Desktop/name-of-file.bin"

---

### Post by macogw on 2007-07-19
Don't bother with it.  Just go to YouTube and when it wants to install the plugin, click for it to get the plugin itself and it should work fine.  Or, you can do this in the terminal:
```
sudo aptitude install flashplugin-nonfree
```
and it'll install from the repositories (also can be done with the mouse using Add/Remove or Synaptic or Adept)

Kubuntu isn't for Macs.  Kubuntu is just Ubuntu with KDE instead of GNOME.  Kubuntu or Xubuntu or Ubuntu of Fluxbuntu or Debian or Fedora or any other distro which has a PPC build can be used on PowerPC Macs.  Most any distro can be used on Intel Macs.

---

### Post by RomeReactor on 2007-07-19
Hi. Double-click the .tar.gz file to extract it (it should extract as a folder named **install_flash_player_9_linux**); move that folder to your home folder (if it isn't there already), open a terminal (Applications->Accessories->Terminal) and enter the following:
```
cd install_flash_player_9_linux
```
then
```
sudo ./flashplayer-installer
```

---

### Post by ukulele_ninja on 2007-07-19
after i unzipped the file.... the available files are: flashplayer-installer, flashplayer.xpt and libflashplayer.so

---

### Post by macogw on 2007-07-19
Just get it through Adept.  It's called "flashplugin-nonfree"  You don't need Adobe's installer.

---

### Post by ukulele_ninja on 2007-07-19
> **RomeReactor said:**
> Hi. Double-click the .tar.gz file to extract it (it should extract as a folder named **install_flash_player_9_linux**); move that folder to your home folder (if it isn't there already), open a terminal (Applications->Accessories->Terminal) and enter the following:
```
cd install_flash_player_9_linux
```
then
```
sudo ./flashplayer-installer
```


ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
 is what I got. :(

---

### Post by ukulele_ninja on 2007-07-19
> **macogw said:**
> Just get it through Adept.  It's called "flashplugin-nonfree"  You don't need Adobe's installer.

I looked in adept but did not see it

---

### Post by macogw on 2007-07-19
OH you're using 64bit?  It's only for 32bit.  You need nspluginwrapper [http://ubuntuforums.org/showthread.php?t=425672](http://ubuntuforums.org/showthread.php?t=425672)

EDIT: direct link instead of Google's redirect

---

### Post by RomeReactor on 2007-07-19
Unfortunately there's no flash for 64 bit yet; you can get the 32 bit version working [here]("https://help.ubuntu.com/community/RestrictedFormats/Flash#amd64andppc").

---

### Post by ukulele_ninja on 2007-07-19
Do I need firefox to do this?

---

### Post by macogw on 2007-07-19
As opposed to Konqueror?  No, should be fine.  Konqueror has a plugin wrapper when you install flashplugin-nonfree.  Did you try it from the terminal, by any chance?  It may have just been hidden in Adept (I've never used Adept, but if it's like Add/Remove, not everything shows up)

---

### Post by ukulele_ninja on 2007-07-19
How do I do it from konsole?

---

### Post by macogw on 2007-07-19
sudo aptitude install flashplugin-nonfree

is how you would install that plugin. it should pull in konqueror-nsplugins (or something like that) to make konqueror handle it, i think, but i'm not a kde user, so i'm not 100% on that

---

