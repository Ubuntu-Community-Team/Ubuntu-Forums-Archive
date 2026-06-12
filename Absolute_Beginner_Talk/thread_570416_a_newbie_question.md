---
title: "a newbie question"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by n364 on 2007-10-08
hello! just installed Ubuntu 7.04, Feisty Fawn and im glad it works fine on my amd athlon, dual core, 64bit. my problem is, i cant install adobe flash player on my firefox. tried to googled for it and search the forum but no use.

i got this problem eveytime i use this command:

ian@ian-desktop:~$ sudo apt-get install flashplayer-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-nonfree

where should i look for the package 'flashplayer-nonfree'? or i have no package of that name?
i have downloaded 'install_flash_player_9_linux.tar.gz' , extracted the content and got
flashplayer.xpt, flashplayer-installer, libflashplayer.so and follow the instruction on adobe.com but still i got this error:

ian@ian-desktop:~$ sudo apt-get install flashplayer-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-installer

should i place these files on certain directories?
i use synaptic package manager to install some built-in flash player but still it wont work.

what should i do now? please help. :confused::confused::confused::confused:

---

### Post by skymera on 2007-10-08
try

sudo apt-get update
sudo apt-get upgrade

do that then try your flash :wink:

---

### Post by por100pre1 on 2007-10-08
Please follow this [how-to]("http://ubuntuforums.org/showthread.php?t=413624"). It shows how to install it using Add/Remove.

---

### Post by El Cabrón on 2007-10-08
Ugh... I erased this post.

What does "For 100 Pre One" mean anyway?  "Por-100-Pre-Uno"

---

### Post by Kilz on 2007-10-09
> **n364 said:**
> hello! just installed Ubuntu 7.04, Feisty Fawn and im glad it works fine on my amd athlon, dual core, 64bit. my problem is, i cant install adobe flash player on my firefox. tried to googled for it and search the forum but no use.

i got this problem eveytime i use this command:

ian@ian-desktop:~$ sudo apt-get install flashplayer-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-nonfree

where should i look for the package 'flashplayer-nonfree'? or i have no package of that name?
i have downloaded 'install_flash_player_9_linux.tar.gz' , extracted the content and got
flashplayer.xpt, flashplayer-installer, libflashplayer.so and follow the instruction on adobe.com but still i got this error:

ian@ian-desktop:~$ sudo apt-get install flashplayer-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-installer

should i place these files on certain directories?
i use synaptic package manager to install some built-in flash player but still it wont work.

what should i do now? please help. :confused::confused::confused::confused:

If you are running the amd64 versuon of Feisty fawn you need to install a pluginwrapper for flash. [I wrote a handy little script]("http://ubuntuforums.org/showthread.php?t=476924") that does all the work in about 30 seconds.

---

### Post by dptxp on 2007-10-09
> **Kilz said:**
> If you are running the amd64 versuon of Feisty fawn you need to install a pluginwrapper for flash. [I wrote a handy little script]("http://ubuntuforums.org/showthread.php?t=476924") that does all the work in about 30 seconds.

Kilz, is there a single point where the special extra bit of support needed for 64-bit are summarized ?
With links to solutions ?
Is it going to be easier in Gutsy ?

---

### Post by Paqman on 2007-10-09
> **dptxp said:**
> 
Is it going to be easier in Gutsy ?

Yes. In Gutsy you can install Flash through Synaptic. It automatically installs the required wrapper. Woo! No more 32-bit Firefox!

---

