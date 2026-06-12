---
title: "ATI x1400 + resolution/3d accel. issue"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by morweni on 2007-10-14
Afternoon!

I have installed ultimate 1.3 which I believe is edgy eft 6.10, and will be upgrading in 4 days once 7.10 is out :D.. in the meantime though...

I installed my ati x1400 mobility radeon drivers (acer laptop) via Envy. Now I am having 2 issues.

1) Resolution only goes as high as 1024x768 when it can go much higher :(
2) I installed wow via wine walkthroughs, can run it but it's super super laggy (can only make it to EULA before I hit cancel because of it being slow). Now I am NOT going to play WoW but I'd love to get it to work on Ubuntu, then proceed with other games =). 

I tried adding -opengl to the exe on the desktop, gives me a failed to start 3d acceleration error. Something tells me the drivers are causing both of these issues.

Any suggestions? 
Please and thank you =)

---

### Post by Pumalite on 2007-10-14
Re: Feisty and Gutsy not working with ATI X1400
This is a solution from [http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/](http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/)
and is listed  on [http://kubuntuforums.net/forums/index.php?topic=3086249](http://kubuntuforums.net/forums/index.php?topic=3086249)

Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot
Ubuntu 7.04 should now boot into GDM/KDM.

---

### Post by morweni on 2007-10-14
Thank you for the info however the 1st link is not found and the 2nd didn't help too much?

Either way thank you, I tried my best being a noob to follow your other lines of suggestions but still on the same resolution/open gl issues.

Here is what I can give you for info:

```

adria@minime:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

Now I've installed different versions of ubuntu and played around and have had a few issues before but still never have gotten drivers to work proper.. yet! :)

Running Edgy Eft atm =) ty!

---

### Post by Pumalite on 2007-10-14
Sorry, that first link IS dead. Seems to be an old recipe. Nothing else to contribute here. Someone will chime in.

---

### Post by morweni on 2007-10-14
After following: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) I finally 
have the following!!


```

adria@minime:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

```


Able to run and patch WoW NP, no lag, opengl and the likes are working woohoo!

Still not getting max res I normally can use, any thoughts?

EDIT: boyfriend believes it could be the fact that ubuntu/drivers may not be detecting the native resolution on my acer aspire 5670 notebook?
EDIT: Starting new thread

---

