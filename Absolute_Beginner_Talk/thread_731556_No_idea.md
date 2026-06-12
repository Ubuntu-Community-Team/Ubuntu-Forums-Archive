---
title: "No idea"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by shleusink on 2008-03-22
Ok I just downloaded the install_flash_player_9.tar.gz, but now what.  How do I install it or whatever?  

g.

---

### Post by wormser on 2008-03-22
It is best to install software from the repositories.  I am guessing that you have not enabled all of them.  System> Administration> Software Sources.  Check Main, Universe, Multiverse and uncheck CD-rom.  Now go to System> Administration> Synaptic Package Manager and search for flashplugin-nonfree.

---

### Post by Sinkingships7 on 2008-03-22
> **shleusink said:**
> Ok I just downloaded the install_flash_player_9.tar.gz, but now what.  How do I install it or whatever?  

g.

right click, extract here.

assuming you downloaded it to your desktop (if you didn't, move the extracted folder there), open a terminal and paste this command, substituting NAME for your user name: 
```
cd /home/NAME/Desktop/install_flash_player_9_linux
```

then run this command:
```
./flashplayer-installer
```

agree to the prompts, be sure firefox is closed, and that should do it for you.
when that's done, you can delete the tar.gz and folder from your desktop.

---

### Post by wolfen69 on 2008-03-22
> **Sinkingships7 said:**
> right click, extract here.

assuming you downloaded it to your desktop (if you didn't, move the extracted folder there), open a terminal and paste this command, substituting NAME for your user name: 
```
cd /home/NAME/Desktop/install_flash_player_9_linux
```

then run this command:
```
./flashplayer-installer
```

agree to the prompts, be sure firefox is closed, and that should do it for you.
when that's done, you can delete the tar.gz and folder from your desktop.

no need for that. :(

---

### Post by wolfen69 on 2008-03-22
yeah it's cool that WE know commands, but i dont always assume everyone is receptive to terminal commands.

sorry for getting off topic.

---

