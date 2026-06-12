---
title: "remove a installed bin program(realplayer)"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by the.phantom on 2007-06-08
i was trying to get realplayer to install and tried the way on the community forum which was
download realplayer to the desktop 

$ cd Desktop

 $ chmod a+x RealPlayer10GOLD.bin

 $ sudo ./RealPlayer10GOLD.bin

everything went well but it wanted a link for other programs (sorry forgot the exact words)
well i hit enter and it installed on the desktop 
so i have a folder called 
realplayer10.bin
and a locked file called "real player"

i checked synantic package manager and not listed
so can someone tell me a easy way to uninstall this mess i have created?
thanks
i think i will always be a newbie, but i am learning ;-D

---

### Post by Cypher on 2007-06-08
Don't bother looking in Synaptic/Add-Remove/Dpkg/Apt since you didn't use any of those to install the program, as such they won't know how to un-install it.

Can you not just safely remove the directories in your desktop?? Hit ALT-F2 and then run
```

gksu nautilus

```
this will bring up the file-manager with ROOT permissions. Go to your home directory and remove the "realplayer10.bin" directory and it's contents.

Once that's done, you can install Realplayer using [Automatix]("http://www.getautomatix.com") (though the website seems to be down right now).

---

### Post by the.phantom on 2007-06-08
well it was working but was on the desktop

your trick removed it,
but when i went on to install it with add/remove or synampic it would install but not work
looking around so far i have found part of it in user/lib
and another part in home
so there has to be something left over that kills a  install?

i have another identical system  6.10 and it works on it
oh well will go looking for more scraps on the system

that is what i was worried about was just deleting it and parts left elseware

---

