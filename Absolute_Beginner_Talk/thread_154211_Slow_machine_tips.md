---
title: "Slow machine tips"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by hammers on 2006-04-02
Hi folks, 

I've installed 5.10 on an old PC which was running windows 98. It's quite an old pc, I can't remember the RAM or processor speed (and i'm new to linux and havent yet discovered where to find that stuff) but it's certainly less than 256MB RAM. The system is v slow ](*,) and i was wondering whether there might be some applications i can safely remove to try to speed it up a little? I'm only going to be using it for web and email. If there are any other tips for speeding it up i'd also love to hear them.

Cheers,

Hammers

---

### Post by localzuk on 2006-04-02
I would recommend using 'xubuntu'. To install this, open synaptic and select 'xubuntu-desktop' from the list. When you come to log in again, select 'XFCE' from the 'session' menu on the login screen. From here your desktop will be different but a lot faster.

---

### Post by Azrael on 2006-04-02
Install a light weight window manager (XFCE is popular, IceWM would be my choice, search/google for more) and use it instead of Gnome.

---

### Post by aysiu on 2006-04-02
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by IYY on 2006-04-02
Epiphany is a bit faster than Firefox. Dillo is a lot faster, but doesn't have as many features. Use XMMS to play music. XFCE or IceWM as the window manager.

---

### Post by R3linquish3r on 2006-04-02
Fluxbox/Blackbox are the faster window managers I've used, even if they are a pain to setup. I also recommend Swiftfox instead of Firefox along with the Fasterfox Extension. This will boost your net speed ALOT. There is a how-to on how to install Swiftfox in the How-to section.

---

### Post by barbarian on 2006-04-03
If your computer 24/7 online, prelink would help alot..
[http://www.ubuntuforums.org/showthread.php?t=74197&highlight=prelink](http://www.ubuntuforums.org/showthread.php?t=74197&highlight=prelink)

---

### Post by meborc on 2006-04-03
check out the wiki: [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

some good pointers for your slow box ;)

---

### Post by missmoondog on 2006-04-03
[QUOTE=localzuk]I would recommend using 'xubuntu'. To install this, open synaptic and select 'xubuntu-desktop' from the list. When you come to log in again, select 'XFCE' from the 'session' menu on the login screen. From here your desktop will be different but a lot faster.[/QUOTE]

does this leave everything else intact still with just a different desktop?

what i'm getting at is, will EVERYTHING be the same except for the desktop? i have a fully functional ubuntu with gnome desktop install on an old hp pavilion. it is relatively slow, but useable. will simply installing the xfce desktop help me out any or should i do a complete server type install of xubuntu? please respond ASAP.

thank you

---

### Post by localzuk on 2006-04-03
All the other apps will still be there, plus a few new ones (such as abiword for word processing which is much lighter than O.O.o2).

---

### Post by missmoondog on 2006-04-03
thank you. here's hoping. so, after that, what can/should i remove from gnome?

i was just waiting for 1 reply to go for this!

edit:
xfce is installed and running. :)

edit #2:
i think i'm confusing myself now. xubuntu is a complete os, just like ubuntu, kubuntu, edubuntu, etc., correct? it just uses the xfce desktop by default? if i did the server install of xubuntu, would/could that wipe my stuff clean and do a full install of xubuntu? what i'm saying again is, xubuntu and xfce are 2 different things, so to REALLY gain anything much on an older system, i need to install xubuntu and not just install xfce on ubuntu? right?

are you as confused as i am now? :)

edit #3:
just a little fyi,
ok, so i started all over wiping out my breezy 5.10 and installing ubuntu server, then xubuntu with the xfce4 desktop. definitely WAS NOT worth the effort in an attempt to gain any performance increase. i'll leave it as is though, as this box isn't used very often anyway.

---

### Post by hammers on 2006-04-15
Thanks for all the suggestions folks. 
I've installed XFCE and this seems to be much quicker. Unfortunately I don't seem to be able to allow remote connections, does anyone know how i can do this? Also, i'd like to get rid of the monitor and keyboard, is there anyway i can make the machine boot up straight into a session rather than asking for a username and then password?

---

### Post by aysiu on 2006-04-15
[QUOTE=hammers]Thanks for all the suggestions folks. 
I've installed XFCE and this seems to be much quicker. Unfortunately I don't seem to be able to allow remote connections, does anyone know how i can do this?[/quote] Like VNC, you mean? You can install and use the rdesktop package or grdesktop or krdc. You can also look into tightvncserver > Also, i'd like to get rid of the monitor and keyboard, is there anyway i can make the machine boot up straight into a session rather than asking for a username and then password? If you're using GDM, run ```
gksudo gdmsetup
``` There should be an auto-login option there.

---

### Post by hammers on 2006-04-15
Apparently rdesktop is already installed but i can't find how to enable remote connections. In gnome it was *System->Preferences->Remote* but there isnt *Preferences* in xcfe. In the login screen set up i noticed *Remote* is disabled but the dropdown is greyed out so i can't enable it. Any ideas?

---

