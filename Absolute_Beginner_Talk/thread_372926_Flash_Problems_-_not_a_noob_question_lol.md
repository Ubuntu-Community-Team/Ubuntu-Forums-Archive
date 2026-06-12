---
title: "Flash Problems - not a noob question lol"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Tag_yer_dead on 2007-02-28
hey guys,
i just reformatted my hdd and am settin up ubuntu again.  I had a problem installing flash the last time to, but i cant find where the old topic is.
i do the good ole'
sudo aptitude update
sudo aptitude install flashplugin-nonfree 
and i get

Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading...  done.
automatic installation failed due to network problems or upstream changes

i tried
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
and got the same thing

I tried in firefox about:plugins and flash doesnt show up

any ideas anyone?

---

### Post by r4ik on 2007-02-28
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Good luck !

---

### Post by userundefine on 2007-02-28
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by Patrick K on 2007-02-28
Go to a site that uses Flash and let Firefox install it. That's what I did and had no problems whatsoever.

---

### Post by alienexplorers on 2007-02-28
I used automatix2 to install flash.  I believe it loaded version 9.0, but not certain about that.  Either way it is working like a champ.

---

### Post by Maestro23 on 2007-02-28
I'll add my 2 cents. My method:

> sudo aptitude install flashplugin-nonfree


Works like a charm.

---

### Post by szf on 2007-02-28
> **alienexplorers said:**
> I used automatix2 to install flash.  I believe it loaded version 9.0, but not certain about that.  Either way it is working like a champ.
Open Firefox and type```
 about:plugins
``` into the location bar.

Installed flash 9.0-r31 by hand here... what a chore!

---

