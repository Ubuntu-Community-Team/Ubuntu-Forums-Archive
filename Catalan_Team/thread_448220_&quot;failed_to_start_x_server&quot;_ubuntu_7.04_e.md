---
title: "&quot;failed to start x server&quot; ubuntu 7.04 en laptop"
date: 2007-05-18
forum: Catalan Team
---

### Post by eddbaez on 2007-05-18
I'm a n00b , I install 6.02 and the update to 6.10 and then to 7.4
in the last update get the menssage "failed to start x server...."
I don not much about commands , but I use a one that shows hardware and I think that mi dosplay it's not been detected 

any sugestions ?? 
Thanks .

---

### Post by siralphred on 2007-05-18
you can try installing the correct driver for your video card, if its ATI this might help [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) and if its NVIDIA this might help [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) and next time back up ur xorg.conf file  with this command: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup     and you restore with command: sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf    good luck

---

### Post by CarlesOriol on 2007-05-19
executa 

sudo dpkg-reconfigure xserver-org

---

### Post by CarlesOriol on 2007-05-19
You've written this message to the Catalan Community Forum. And the feed back you will recive in english would be very limited because the language of our members and subscribers.

May be you should feel more confortable in english posting it to other categories like [http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135) (Hardware & laptops).

---

