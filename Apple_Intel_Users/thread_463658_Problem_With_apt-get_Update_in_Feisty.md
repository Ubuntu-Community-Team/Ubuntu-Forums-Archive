---
title: "Problem With apt-get Update in Feisty"
date: 2007-06-03
forum: Apple Intel Users
---

### Post by infinitusagnitio on 2007-06-03
Hi guys.

I just finished installing (after 8 tries) Feisty Fawn on my Mac Book Pro.  I'm running an Intel Core Duo 2.16ghz with 2gb of RAM. 

After my initial install finally started working, I tried to get Beryl working.  I followed the guide on [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29) and at step 3 when I type sudo aptitude update, I get an error message saying:

E: The method driver /usr/lib/apt/methods/htpp could not be found.
E: The method driver /usr/lib/apt/methods/htpp could not be found.

When I went into my add/remove applications and typed sudo apt-get update, I get the same error.  I searched Google but I couldn't find anything.  Help please!?

---

### Post by infinitusagnitio on 2007-06-03
Also, I have a problem with my cd mounting.  Whenever I want to install something (see: Java) it asks me to insert the disk into the /cdrom/ directory.  I then insert the disk but nothing happens.  I tried going into properties on the cd rom itself and changing the mount point to /cdrom/ but now it won't mount at all due to an invalid mount point.  Is there any way I can change the mount point of this file?

---

### Post by eldepeche on 2007-06-09
Check your sources.list file, it looks like you may have entered the line wrong, judging by the "htpp" in the error message.

---

