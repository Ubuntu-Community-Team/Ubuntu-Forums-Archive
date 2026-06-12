---
title: "cant install flash"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-09-01
always says cant find package? any ideas?

---

### Post by Crafty Kisses on 2007-09-01
> **LiNuXxToOthEMaX said:**
> always says cant find package? any ideas?

First, you should try the following:
```
sudo apt-get remove flashplugin-nonfree
```

This will remove Flash 7 if you have that already installed using the package manager. If the terminal tells you Package flashplugin-nonfree is not installed, so not removed or E: Couldn't find package flashplugin-nonfree, that's fine. We just wanted to make sure it wasn't installed.

Then do this:
```
rm ~/.mozilla/plugins/*flash*
```

Then after that, you will have to reinstall the package:
```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

Then after all that, unzip it, then install it and then it should work, hopefully this helps. :)

---

### Post by meborc on 2007-09-01
you need to enable the multiverse/universe repositories... find more info here - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

scroll up and down the page to find more tips and tricks :)

EDIT: seems i was too late... although, since we suggested different methods, i will leave my post as it is :D

---

### Post by paradoc on 2007-09-01
OR.......you could try the 'blunderbus' approach-in Feisty- (installs flash,Java and a bit more besides)> Launch Add/Remove (from Applications)
Enter restricted in the search bar, choose 'All available applications', with 'All' highlighted, (top of left hand menu), if no tick on 'Ubuntu restricted extras', you will be downloading Java 6 runtime, Flash 9 player, and a few popular MS fonts, when you click on APPLY.

If APPLY is greyed out, it means you already have it installed, and 'OK' simply removes the app window leaving you possibly wondering why it didn't work!.

good Ubunting!

---

