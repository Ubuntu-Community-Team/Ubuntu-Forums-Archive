---
title: "Problem with Mouse/Video"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by Hellsadvocate on 2008-04-27
Hi guys,
I'm new to the whole linux thing, I just decided to triple boot my new macbook pro with Ubuntu hardy heron, things went fine in the beginning. The video was perfect (the res), the sound worked, the only thing that didn't was the wifi and the mouse. For wifi, i installed madwifi and though it picked up signal, every now and then, right after a few minutes of working the internet would just die. Which I thought was odd. 
I also changed the settings in xorg.conf for my mouse, and it worked splendidly, my big problem arose after I tried this. I tried to change the appearance into "normal" and Ubuntu couldn't do it. I guess i'm an idiot, so I decided to download Linux Drivers for the 8600GT from the nvidia website. In order to install the drivers, i had to shut off xserver and restart it. Once installed i restarted and noticed that my resolution went to the basic, and Ubuntu tells me It can't do anything above 800x600? I'm a bit lost now, and if i go to X Server Nvidia Settings, it tells me that "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file, and restart X server. 

That's great an' all, and I edit the X config file, and restart the X server (/etc/init.d/gdm restart) and go back into Ubuntu with the same problem. Nvidia X server settings keep giving me the same problems. Not sure what to do from here guys. You all seem really nice. And I would love to go further with my Ubuntu installation. 
Thankyou For everything.

Quick Edit: I've heard it's a common problem with Compiz and the easiest thing to do is just to disable it and then reenable? But I'm a total noob, I don't understand how to enable to disable compiz besides from "add/remove programs" Any help guys?

-After i uninstalled all nvidia drivers, and then reinstalled, it worked fine, I saw a Nvidia sign and everything started okay. As soon as i restart Ubuntu, it all goes to hell, and now I can't get the drivers to work anymore. What the hell. It's 4 Am and it's not fun.

---

