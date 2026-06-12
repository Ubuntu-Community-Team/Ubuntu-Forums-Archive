---
title: "Wifi Question for macbook"
date: 2007-11-07
forum: Apple Intel Users
---

### Post by Zaff on 2007-11-07
Hey everyone,
Okay I don't know if this is related to the macbook hardware, to gutsy or both or neither but here's my problem :
I use my macbook laptop at work, we had a wifi acces with  WPA2 Personal access. I used to get disconnected all the time (up to 7 or 8 times a day) and the thing was that after being disconnected I had to reboot my computer because no wifi would be detected (there are almost ten of them within range). It went like this : I would first notice that my internet acces is gone (pages don't reload). Then  if I tried going into network manager and select the network again it would try to connect for a few minutes then give up and if I go in the list again there is no wireless network detected. 
Is this making any sense ?
Anyway we read somewhere that sometimes WPA isn't really supported by some hardware so we changed it to WEP. It works better but I still get the same problem sometimes (once or twice in a day at most). I was using kopete and it seemed to make it crash more often so I'm now using Pidgin but maybe that's just a coincidence.
Anyway does anyone know anything about this kind of issues ? I have tried to connect at home and haven't had this problem so far but I rarely stay connected as long as I am at work.
I'll had that I don't seem to have the problem using MacOS but then again I don't use it half as much as I use Ubuntu.

So thanks to anyone for any insight on the matter.

---

### Post by cyberdork33 on 2007-11-07
There seems to be some bug in madwifi that causes the driver to fail after awhile. Have you tried ndiswrapper?

---

### Post by Zaff on 2007-11-07
> There seems to be some bug in madwifi that causes the driver to fail after awhile. Have you tried ndiswrapper?
No I haven't. Is it more stable ? I was under the impression madwifi had better support.

---

### Post by cyberdork33 on 2007-11-07
It is not really a matter of stability, although I can't vouch for how well it will work for you. Might as well try it if you are having an issue.

ndiswrapper uses a windows driver for your device and 'wraps' it so that it can be used by linux. I think the only limitation for this method is that there is not a 64bit windows driver for your hardware, so if you are on a 64bit version of Ubuntu, you are limited to madwifi.

---

### Post by Zaff on 2007-11-07
> There seems to be some bug in madwifi that causes the driver to fail after awhile. Have you tried ndiswrapper?
I'm using 32 bits ubuntu so that's not an issue.
Thanks for the info, I'll try tonight or in the next few days, I'll let you know if it changes anything.

---

### Post by bsantos on 2007-11-07
I stopped having issues with madwifi hanging after a while a few revisions ago. I had oopses before the proposed network-manager package. It was something related to supplicant clean up IIRC.

Try the latest svn version. It is stable here on a 2nd gen MB c2d.

---

### Post by cyberdork33 on 2007-11-07
> **bsantos said:**
> I stopped having issues with madwifi hanging after a while a few revisions ago. I had oopses before the proposed network-manager package. It was something related to supplicant clean up IIRC.

Try the latest svn version. It is stable here on a 2nd gen MB c2d.

See here if that doesn't work:
[http://ubuntuforums.org/showthread.php?t=587366](http://ubuntuforums.org/showthread.php?t=587366)

---

### Post by Zaff on 2007-11-12
So i'm still having problems with madwifi wometimes.
I looked at the ndiswrapper solution but I need the drivers and I can't do them with bootcamp anymore since my disk is full (bootcamp can't partition anything).
Anyone knows where I could download the driver ?
Thanks

---

### Post by Zaff on 2007-11-13
anyone ? (upping)

---

### Post by volanin on 2007-11-13
Here you go!
I also used madwifi (better power savings), but they are indeed a lot less stable.
So I switched to ndiswrapper, and things couldn't be better. Try it out!
:)

---

### Post by Zaff on 2007-11-13
Thanks
I tried the "stable" svn snapshot but it keeps screwin up. I'll try this tonight.
I really wish I didn't have to use ndiswrapper but if it's the only way I can be at peace with my wifi connection then i'll do it...
Again thanks

---

### Post by cyberdork33 on 2007-11-13
> **Zaff said:**
> So i'm still having problems with madwifi wometimes.
I looked at the ndiswrapper solution but I need the drivers and I can't do them with bootcamp anymore since my disk is full (bootcamp can't partition anything).
Anyone knows where I could download the driver ?
Thanks
You don't have to partition to get the Bootcamp driver CD:
[http://www.mactelchat.com/tips-n-tricks/229-install-bootcamp-mac-drivers-without-burning.html](http://www.mactelchat.com/tips-n-tricks/229-install-bootcamp-mac-drivers-without-burning.html)

---

### Post by RelativelyQuantum on 2007-12-31
How did you get Gutsy to interface with your wifi hardware in the first place? I haven't gotten past that yet.

---

