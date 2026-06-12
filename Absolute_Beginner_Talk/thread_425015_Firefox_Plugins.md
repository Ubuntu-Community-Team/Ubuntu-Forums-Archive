---
title: "Firefox Plugins"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-04-27
When viewing some websites with the Firefox browser I am asked to "Click here to download plugin".

When I select this the plugin finder service starts and says "no suitable plugins were found".
It offers an unknown plugin (application/x-shockwave-flash) with a manual install button.

Is it okay to install this even though the original find stated no suitable plugins were found? Would the application/x-shockwave-flash only be suitable in a windows environment?

Thanks

---

### Post by Kobalt on 2007-04-27
Did you install the flash plugin yet ?
If not, you can easily do this from the Add/Remove at the bottom the the Application menu. Search for *flash plugin*, install it and restart Firefox, you should be set.

---

### Post by OldDog11 on 2007-04-27
The only flash plugin I could find was the Macromedia Flash Plugin but it would not allow me to install this - restricted by copyright or requires special hardware features.

Any suggestions what I can do now?

---

### Post by Kobalt on 2007-04-27
You can try to open a Terminal (Applications > Accessories > Terminal) and then copy/paste the following command lines in order to install Flash 9 plugin for Firefox : 
```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
```

---

### Post by OldDog11 on 2007-04-27
As far as I can tell this downloaded and installed the file but the websites still say I require a plugin.

I closed firefox and re-opened it and also restarted my PC.

---

### Post by Sef on 2007-04-27
> The only flash plugin I could find was the Macromedia Flash Plugin but it would not allow me to install this - restricted by copyright or requires special hardware features.


What version of Ubuntu do you have?  The Add/Remove only works with Feisty Fawn 7.04.

---

### Post by OldDog11 on 2007-04-27
I have Feisty Fawn 7.04

---

### Post by Sef on 2007-04-27
> The only flash plugin I could find was the Macromedia Flash Plugin but it would not allow me to install this - restricted by copyright or requires special hardware features.

When the license agreeement came up, did you click yes?

---

### Post by OldDog11 on 2007-04-27
This is the description I get when I select it in the Add/Remove Applications section

Macromedia Flash plugin
The use, modification and distribution of Macromedia Flash plugin is restricted by copyright or by legal terms in some countries.
Macromedia Flash plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by Kobalt on 2007-04-27
> **OldDog11 said:**
> Macromedia Flash plugin cannot be installed on your computer type (amd64).
Did you install Ubuntu 7.04 64bit edition ?
If so, you need to follow another specific method to have flash plugin : [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

