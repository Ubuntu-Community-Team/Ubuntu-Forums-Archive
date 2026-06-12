---
title: "Can not update Firefox"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by ChuckBooty on 2007-11-13
Currently running Firefox/2.0.0.8 and I want to upgrade to Firefox/2.0.0.9. I open the browser and go to help>check for updates and the option is greyed out. I then go to edit>preferences>advanced>update and the option to automatically check for updates for firefox is greyed out. So Firefox is automatically updating all plugins (such as the Adobe Flash plugin) but not updating the browser itself. 

I have tried downloading the browser directly from the firefox website, but for some reason get errors when I try to use checkinstall (yes I have installed build-essential).

I can not view certain sites, such as credit card sites, unless I delete the latest Adobe Flash plugin. 

Thanks in advance for your help!

---

### Post by carlosjuero on 2007-11-13
It seems that Firefox is tied to Ubuntu, and relies on Ubuntu repository updates for itself to be updated. I have 2.0.0.8 also and just checked the update options only to see them grayed out like you have noticed.

---

### Post by FuturePilot on 2007-11-13
Yes, Ubuntu will take care of the Firefox updates.

---

### Post by zvacet on 2007-11-13
[http://ubuntuzilla.wiki.sourceforge.net/#tochome9]("http://ubuntuzilla.wiki.sourceforge.net/#tochome9")

and on this forums 

[http://ubuntuforums.org/forumdisplay.php?f=251]("http://ubuntuforums.org/forumdisplay.php?f=251")

---

### Post by philinux on 2007-11-13
The firefox from the repo's is tweaked for ubuntu.

So 2.0.0.9 will turn up in a few days as an auto update.

---

### Post by g2g591 on 2007-11-13
if you really want, you can download the tar.gz of mozillas site and unzip into your home folder and run from there (thats what I'm doing with firefox 3 nightly builds) and copy your /usr/lib/firefox/plugins to the plugins folder ~/firefox (created by unzipping the tar.gz)

---

### Post by mivo on 2007-11-13
2.0.0.9 fixes mostly Vista issues that are not relevant to Linux/Ubuntu, so we may not actually get this one at all (because it doesn't do anything for Linux). 2.0.0.7 had been skipped for the same reason.

---

### Post by stchman on 2007-11-13
> **ChuckBooty said:**
> Currently running Firefox/2.0.0.8 and I want to upgrade to Firefox/2.0.0.9. I open the browser and go to help>check for updates and the option is greyed out. I then go to edit>preferences>advanced>update and the option to automatically check for updates for firefox is greyed out. So Firefox is automatically updating all plugins (such as the Adobe Flash plugin) but not updating the browser itself. 

I have tried downloading the browser directly from the firefox website, but for some reason get errors when I try to use checkinstall (yes I have installed build-essential).

I can not view certain sites, such as credit card sites, unless I delete the latest Adobe Flash plugin. 

Thanks in advance for your help!

You don't need to do anything Ubuntu will take care of Firefox updates.  2.0.0.9 is probably a Windows only update so Ubuntu won't do anything.

The Firefox you download from Mozilla is a pre-compile binary so no compiling is necessary.  Just untar it to an appropriate directory.

Firefox is open source so you can download the source code if you wish in the developers section of their website.




If you must install 2.0.0.9 then do the following:

download the .tar.gz archive to your ~/ folder (home folder)

Remove the currently installed firefox
```
sudo apt-get -y autoremove firefox
```

Remove any residual config from synaptic before proceeding.

Delete your firefox folder.  Remember to save your bookmark.html file.
```
rm -r -f ~/.mozilla/firefox/
```

Unpack the archive to the /opt folder
```
sudo tar -C /opt -zxvf ~/firefox-*
```

Create a symbolic link
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

Remove the archive as it is no longer needed
```
rm -f ~/firefox-*
```

You can add a menu entry using the following
Exec = /usr/bin/firefox
Icon = /opt/firefox/icons/mozicon16.xpm

You should now have Firefox 2.0.0.9.

When you run Firefox it will create a new ~/.mozilla/firefox folder

---

### Post by xkendrax on 2007-12-06
I'm still with version 2.0.0.6 since i installed gutsy and got no update notification. Is that normal?

---

