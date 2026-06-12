---
title: "dpkg interrupted error i type configure command and it hangs"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by daduda on 2007-11-15
I have read several posts about this problem and am still stuck.  I just install ubuntu and this is the first time i have used it.  

I am getting the dpkg was interrupted error.

I have type in sudo dpkg --configure -a

when I type in configur code I get this 

thedudaman@thedudaman-laptop:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--12:38:14--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.114.70
Connecting to fpdownload.macromedia.com|72.246.114.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

    0K .......... .......... ...

Then it just hangs,

Please help I love this ubuntu so much better than windows already but i want to keep playing with it.


Thanks, micha

---

### Post by Nikitas350 on 2007-11-15
try to use synaptic in order to fix the problem. Go to system ---> administration ----> synaptic package manager. Select custom filters (left and down) and then go to broken packages. Select them all and mark them for removal. Then click to the apply button. Good luck....

---

