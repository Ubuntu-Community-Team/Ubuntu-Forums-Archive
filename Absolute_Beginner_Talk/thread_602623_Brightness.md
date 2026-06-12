---
title: "Brightness?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-11-04
Hi, err, when I set the monitor brightness in gusty using sudo nvidia-settings, and save the new settings then they work until I reboot.  If I then type again sudo nvidia-settings then they take effect again straight away but not until I type that?  is this a bug or am I supposed to do it a different way in gusty??  A minor thing but it's bugging me?  any advice welcome cheers

---

### Post by bubbalouie on 2007-11-05
Perhaps make a script run at start to preset you brightness settings, my gf does this and she seems happy enough with it as a solution, beyond that I wouldn't kow sorry....

---

### Post by tony.morse on 2007-11-06
Ok that sounds like a good idea, err, ok I'm a newbee, how do I do that??

---

### Post by bubbalouie on 2007-11-07
Hmmm, in kde, you put a shortcut with the needed command in ~/.kde/Autostart and KDE will work its magic.

To make a script just make a text file with a **.sh** extension (using gedit, kate, nano or whatever your favorite editor is) with the command in it, then run the following command on the text file:

```
chmod 777 yourscript.sh
```

This script will now be runnable at any time by double clicking it (depending on your UI of course).

To make it run at start up in gnome though I have never done (devout user of KDE sorry), however, the following should help regardless of your environment:

[http://ubuntuforums.org/showthread.php?t=255587&highlight=run+script+at+boot](http://ubuntuforums.org/showthread.php?t=255587&highlight=run+script+at+boot)

Good luck :)

---

### Post by laidback on 2007-11-07
I have nvidia-settings as an icon on my desktop; in permissions I am the owner; my settings seem to be kept from session to session (reboot); although I'm not the owner of /usr/share/nvidia-settings, the actual utility. Somewhere there must be a file which holds my local settings. So I reckon what you want is possible.

---

