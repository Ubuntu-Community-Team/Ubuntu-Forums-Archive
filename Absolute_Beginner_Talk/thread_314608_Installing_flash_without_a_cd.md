---
title: "Installing flash without a cd"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Aoplayo on 2006-12-07
Ok I can't watch youtube videos or any videos just because I can't install flash. Well I tried installing automatix but wouldn't you know my cd reader won't read anything. I even tried reinstalling linux but it doesnt read the bootdisk. Is there away to install flash without the cd?

---

### Post by bodhi.zazen on 2006-12-07
flash is in the repositories, why not install it with synaptic ?

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by igknighted on 2006-12-07
If you want the newest flash 9 beta you can find it at labs.adobe.com, it is really easy to install.  Once you extract the file then you just need to place it in folder it needs it (see the readme).  Most things on the web (not youtube, however) are going flash8/9 so its a good idea to stay current.

---

### Post by Aoplayo on 2006-12-07
I tried to use synaptic but it prompted me to insert a disc. The cd reader doesn't read. So no go.


im trying igknighteds way

---

### Post by abarth on 2006-12-07
In order to use synaptic, you probably want to disable the use of the cdrom.

Type in a terminal:

sudo cp -i /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list

In gedit add a # in front of every line containing "cdrom".

Hope this helps,
Alex

---

### Post by aysiu on 2006-12-07
If you're in Synaptic anyway, you can also disable the CD-ROM repository by going to **Settings** > **Repositories** and then unchecking box next to the CD-ROM source.

For installing Flash 9, try [this](http://ubuntuforums.org/showthread.php?t=279990).

---

