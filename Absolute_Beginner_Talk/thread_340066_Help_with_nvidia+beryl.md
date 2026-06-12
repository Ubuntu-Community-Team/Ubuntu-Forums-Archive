---
title: "Help with nvidia+beryl"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2007-01-16
I have convinced my friend to give Ubuntu a try in a seperate partition on his pc. 
So I installed it for him and everything went fine. Everything worked on his desktop and 
after (a really long) update his system was up to date. But then he cried for beryl.....

He has an nvidia 5900 vga. I myself have a 5200 and I use the 1.0-9746 drivers from alberto milones webpage. So I thought I 'd install the same for him.....Unfortunately it didn;t work and after the install glxinfo gave weird results. I then tried to install the drivers as it is described in the "How to: Beryl and latest nvidia drivers" that can be found in this forum but disaster struck. After restarting all he got was a black screen ...X was dead.....

Since he had no data I decided to go for a fresh install of Ubuntu and then I installed the nvidia drivers from the official repos of ubuntu. Everything went smooth and works now. The only problem is that he still wants beryl. 

So my question is should I follow the guide in the forums (How to beryl +latest nvidia)?Will it work this time?
Should I do something else?
I really dont want to break his machine again....I mean these  are his first impressions of Ubuntu and open source in general and I dont want them to be bad.......

---

### Post by mezer on 2007-01-16
I say follow the guide on the below link, but take out the nvidia part of the script.  

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)

That's what i did, as i already had the nvidia drivers in that i wanted.  Follow the instructions on the above page, but instead of using the script on the page, use the script below.  It's just the regular script, with 4-5 lines taken out (the nvidia install).

#!/bin/bash
if [ `whoami` != "root" ]; then
 echo "You must run this script as root.";
else
 cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script
  echo "deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main" >> /etc/apt/sources.list
 wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | apt-key add -
 aptitude -y update && aptitude -y dist-upgrade
 aptitude -y install beryl emerald emerald-themes
 sed -i -e '/Section "Device"/,/EndSection/ { s/EndSection/    Option "TripleBuffer" "True"\nEndSection/ }' -e '/Section "Screen"/,/EndSection/ { s/EndSection/    Option "AddARGBGLXVisuals" "True"\nEndSection/ }' /etc/X11/xorg.conf
 # ... ADD beryl-manager TO STARTUP PROGRAMS HERE IN THE FUTURE, IF POSSIBLE ...
 echo -e "\n\nBeryl is now installed.\n\nTo run Beryl on Ubuntu startup, please add beryl-manager to your\nstartup programs (System > Preferences > Settings, and click on\nthe \"startup programs\" tab). Afterwards, please reboot.\n\nBackups of /etc/apt/sources.list and /etc/X11/xorg.conf were made:\n    /etc/apt/sources.list.backup.beryl-script\n    /etc/X11/xorg.conf.backup.beryl-script"
fi;

---

### Post by Russty of Oz on 2007-01-16
I had some problems with a new machine following the usual method, so I found this other install page and it worked first time.  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia")

I don't know why the original one wouldn't work on the new machine, it worked fine on my old one.  They do the same thing in the end.

Give it a try,

Opps!  Looks like someone beat me to it, I got called away while writing it.

---

### Post by geokok1981 on 2007-01-16
Thanks for the reply guys. Just two more questions.
1. I do need more recent drivers than the ones I got from ubuntu restricted repos to run beryl right?
2. Before installung the drivers I will update his system. This will update restricted modules as well. Considering recent issues there were with that update recently, is there any chance I have to be prepered for any trouble after installing the drivers?

3. Oh and one more thing...I installed the current driver following this guide : [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) . 
At a point there was a command that said:
sudo nvidia-xconfig --no-composite
Can this be a prblem for beryl? What is it used for (the no composite part I mean)

---

### Post by Russty of Oz on 2007-01-16
> **geokok1981 said:**
> Thanks for the reply guys. Just two more questions.
1. I do need more recent drivers than the ones I got from ubuntu restricted repos to run beryl right?
2. Before installung the drivers I will update his system. This will update restricted modules as well. Considering recent issues there were with that update recently, is there any chance I have to be prepered for any trouble after installing the drivers?

3. Oh and one more thing...I installed the current driver following this guide : [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) . 
At a point there was a command that said:
sudo nvidia-xconfig --no-composite
Can this be a prblem for beryl? What is it used for (the no composite part I mean)

The link I used gives the latest drivers which seem to be necessary for beryl.

I had no problems at all with this method.  It just worked! :)   The other thread works fine on some computers but just didn't on my new one and obviously not on your friends.

Good luck!

---

### Post by geokok1981 on 2007-01-17
Any clue about the "nvidia-xconfig -no composite" command that I applied to my current driver? What is it and can it be a problem for beryl? Why even say no composite?

****It turns out that the --no composite option **IS** a problem cause beryl wont work. To fix that u need to edit xorg,conf and change composite from disabled to enabled. Perhaps someone should fix the guide I followed......****

---

