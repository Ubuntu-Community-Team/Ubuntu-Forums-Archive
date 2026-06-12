---
title: "no video with flash"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Istonian on 2008-02-06
I have the flash plugin installed and mplayer, but for some reason when I go to youtube or another site it keeps telling me I need to install plugins to play the video. I have mplayer and flash installed.

---

### Post by jaytek13 on 2008-02-06
There is a bug with installation. You have to install it manually.

First uninstalled the plugin ```
sudo apt-get remove flashplugin-nonfree
```

Go here and download the tar.gz package [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Extract it, and then move the libflashplayer.so file to /usr/lib/firefox/plugins/ directory

---

### Post by jrib on 2008-02-06
How did you install it?

The flashplugin-nonfree package has been broken since adobe decided to upgrade and remove the old tar.gz from its site.  There is an upgraded package available in the -proposed repositories.

---

### Post by jan quark on 2008-02-06
see my small guide for installing the flash player from the adobe site

[http://laiconic.quotaless.com/tutorial3.html](http://laiconic.quotaless.com/tutorial3.html)

---

### Post by Istonian on 2008-02-06
> **jaytek13 said:**
> There is a bug with installation. You have to install it manually.

First uninstalled the plugin ```
sudo apt-get remove flashplugin-nonfree
```

Go here and download the tar.gz package [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Extract it, and then move the libflashplayer.so file to /usr/lib/firefox/plugins/ directory

How do I get permissions to move it to the folder?

---

### Post by warrior24 on 2008-02-06
do the sudo apt-get remove flash part command they mentioned earler then click on this and thats about it.

---

### Post by Istonian on 2008-02-06
I found out how to do the permissions thing. i did a chmod 777. jayteks solutions worked. Didnt try the others because this one worked. Thanks for all your input. The ubuntu community can't be beat.

---

### Post by jrib on 2008-02-06
chmod 777 is the wrong way to obtain permission to a directory outside of your HOME.  You should undo that

---

### Post by Braedley on 2008-02-06
Flash was, for the most part (like 99%), working this morning before I did the update.  Actually, it was a couple of days ago, but that's immaterial.  The point is that the update seemed to kill my ability to use flash.  Anyone know the reason for this, and how to fix it?

EDIT: Nevermind, reinstalling seems to have fixed it.

---

### Post by orbital on 2008-02-07
My Flash player didn't work after update either but sudo apt-get remove flashplugin-nonfree and sudo apt-get install flashplugin-nonfree fixed it.

---

