---
title: "How do I get to the GUI (GNOME?)?"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by sleepy127 on 2006-03-03
I installed ubuntu and then restarted my computer without the cd in, it went through the loading process and then asked for my login then password. After that it shows some disclaimers, version numbers etc. and says you have new mail. terrell@ubutu:~$    At this point I am guessing there is a command line to take me to the GUI but I have no idea what it is and don't know what to ask in the search engine to get the answer.
I am using distro 5.04, It did not auto config my network settings, and this computer will only be used for folding.

Thanks in advance for putting up with the noob. I am building a folding farm and this is the first linux computer that I have assembled. There will be 3 more to follow. That will have me folding on 10 computers all together.

---

### Post by aysiu on 2006-03-03
Try ```
sudo /etc/init.d/gdm restart
```

---

### Post by sleepy127 on 2006-03-03
I typed that and then was prompted for my password, entered that and then it said sudo: /etc/init.d/gdm: command not found

---

### Post by aysiu on 2006-03-03
GDM's not installed? That doesn't sound good. How about this, then? ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by sleepy127 on 2006-03-03
It seems to be installing now. Did I mess up by not doing a custom install from the cd? Did it just install the operating system without the desktop? I will report back if it installs right. My harddrive may be bad also. It was free so I don't know much about it.

---

### Post by aysiu on 2006-03-03
It seems as if you did a server install instead of a regular install.

That's an odd thing to do accidentally, as a normal install requires you to press **Enter**, but a server install requires you to type ```
server
``` and then **Enter**.

---

### Post by sleepy127 on 2006-03-03
I think that is what I did. Should I just reformat and do it over? Will I need to install every thing if I continue with it this way?

---

### Post by aysiu on 2006-03-03
[QUOTE=sleepy127]I think that is what I did. Should I just reformat and do it over? Will I need to install every thing if I continue with it this way?[/QUOTE] No, just do the ```
sudo apt-get install ubuntu-desktop
``` and when that's done do ```
sudo /etc/init.d/gdm restart
``` It should be good.

---

### Post by red_Marvin on 2006-03-03
Server installs just what is needed to get the computer running, to let the user
add on stuff he/she wants later, and that is what you're doing when "later on" adding
on ubuntu-desktop.

---

### Post by sleepy127 on 2006-03-03
I installed everything but was doing other stuff and when I came back to the pc the screen was blank. I left it alone thinking it was starting up opr something but after about 30 minutes nothing had happened so I reset and tried the sudo /etc/init.d/gdm restart but it still said command not found. I am reinstalling everything at the moment.

---

### Post by sleepy127 on 2006-03-03
Sorry for the double post but I want to say thanks for the help. Something went wrong during the 1st install when trying to install the desktop so I reformated and did a regular install (didn't type server) and after about a hour and a half it finished completely and is now up. Next I will try to set up my network and then install folding. Thanks again for the help, I will be on tommorow trying to do that stuff.

---

### Post by najames on 2006-04-13
aysiu,

Thanks for the info.  I did install server in Dapper on purpose, but I didn't realize it didn't install the desktop, CentOS 4.3 did install one.  I tried apt-get gnome, the ubuntu-desktop was the key.  It is apt-getting now.

Edit:

The cotton picking thing is asking me for Braille options.  I can see, don't need Braille, arrrgggg!  Uhh, do Braille screens have little bumps all over them?  If you press them too hard on an LCD screen to they pop like a zit?

Sorry, had to have some fun with this one.

---

