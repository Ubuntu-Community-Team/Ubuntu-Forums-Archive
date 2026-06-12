---
title: "compiled game uninstall"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by viperskunk on 2008-04-06
hi a few days ago i downloaded the package for this game called LordsAwar. then i compiled it manually using make and then make install.
now i want to uninstall the program. trying sudo apt-get remove <program> did not work.
i tried "make uninstall". did not work.
then i deleted the package folder and emptied the trash. still it shows on the menu, and i can still play the game.
two questions:
1) where does the game run from if i have deleted the souce tar.bz2 pakage and the untarred folder?
2) how do i remove such a game?
i am using gutsy.
thanks in advance.

---

### Post by mick8985 on 2008-04-06
It will have installed to /usr/share have a poke about in there and delete the folder, to get rid of the menu entry have a look in /usr/share/menu.

---

### Post by Paqman on 2008-04-06
In future if you compile from source try using checkinstall (it's in the repos) Just install it and then replace the "make install" command with "checkinstall". It'll turn the source into a .deb package that can be uninstalled through Synaptic.

---

### Post by viperskunk on 2008-04-07
thanks a lot guys.

---

### Post by tommcd on 2008-04-07
A lot of games get installed to /usr/local/games with a symlink to /usr/local/bin. You can just delete the game files there and the ~/.some_game folder in your /home directory.
Usually the readme or install file will tell you where the game gets installed.

---

### Post by Perfect Storm on 2008-04-07
Compiled it again and it install it with checkinstall, thereafter remove the game via synaptic: [http://gaming.gwos.org/doku.php/guides:64bit:lordsawar](http://gaming.gwos.org/doku.php/guides:64bit:lordsawar)

---

