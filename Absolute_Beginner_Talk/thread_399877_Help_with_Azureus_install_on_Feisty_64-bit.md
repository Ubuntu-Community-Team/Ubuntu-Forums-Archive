---
title: "Help with Azureus install on Feisty 64-bit"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by mezcla on 2007-04-02
I installed Feisty 64-bit on Sunday after messing about in Dapper for a couple of months.  I was trying to get Azureus installed and used Synaptic but I got the version 2.5.0.0 instead of the latest 2.5.0.4.  I went to the website to try to do an install from the latest version and I can't get it to run except from terminal. Here are the steps I'm performing:

> Download Azureus_2.5.0.4_linux-x86_64.tar.bz2
Extract to Home Folder.
Open a terminal and execute
$ cd azureus
$ ./azureus

Azureus runs but only while I keep the terminal open and I don't get a Menu shortcut either so I have to open it using this method. I am quite the n00b and kind of jumped into linux with both feet by wiping Windows a couple of months ago.  I have picked up quite a bit but know very little about installing stuff through the terminal.  Also let me know if I should be extracting/installing to a different folder.  I just use home because it's easy but when I used Dapper Automatix installed Azureus to opt.

Thanks in advance for any help.

---

### Post by zvacet on 2007-04-03
If you installed correctly files goes to the place they should be.I belive you will find at least one file in usr/bin but to be sure where files are 
```
whereis file_name ls
```
To make shortcut go to the menu layer and on the left side pick internet and on the right new item.that will create launcher.it should look like this
1.name =azureus
2.command =you will find right path with upper command but for example let say it is usr/bin/azureus
3.icon =usr/share/pixmaps

---

### Post by mezcla on 2007-04-04
I guess I'm not installing correctly.  I don't have anything related to Azureus in usr/bin.  I just have the folder Home/Azureus from where I extracted the tar.bz2.  When I run

> $ cd azureus
$ ./azureus

the client opens and runs unless I close the terminal.  That shuts it down immediately.  I am wondering what I did wrong.
I wouldn't mind using Synaptic but it's installing the previous version and there is no option under Help to "Check for updates".

---

### Post by zvacet on 2007-04-04
Try this 
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29")

---

