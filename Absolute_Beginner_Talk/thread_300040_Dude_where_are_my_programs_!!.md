---
title: "Dude where are my programs !!"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by AlainB on 2006-11-15
Hi there,

According to my computer, Bit Torrent and Httrack are installed on my computer but I can't find any icon. Is there  some command am I suppose to type ?

Thanks in advance

NewBuntu

---

### Post by xpod on 2006-11-15
right click your app menu and then choose "edit menu".
Have a look through the menu editor to see if they need enabled.
Sometimes i`ve found even if something is checked as enabled i`ve had to un-check and re-check it`s box to have it show up.

Failing that i use the "debian menu" which shows everything installed

---

### Post by zenbuntu on 2006-11-15
The bittorrent package has fairly basic features. You need to install the gui for it:

```
sudo apt-get install bittorrent-gui
``` 

But alternatively I prefer to use Azureus - [how to install azureus]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29").

As for httrack you could try installing "webhttrack":

```
sudo apt-get install webhttrack
```

Good luck.

---

