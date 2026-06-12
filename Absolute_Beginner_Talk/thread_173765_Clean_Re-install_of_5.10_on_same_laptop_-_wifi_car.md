---
title: "Clean Re-install of 5.10 on same laptop - wifi card not showing up this go round"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-05-10
My first install of Ubuntu 5.10 on my Dell Latitude D600 was a learning experience.  Enough so, that I decided to wipe it clean and start from scratch with all the knowledge I banked the first time around.  I made a lot of mistakes and screwed some things up and was hopeful this would be my clean install.

After installation, I noticed my Dell Broadcom 1470 b/g Wifi card wasnt showing up.  But I wasnt sure if it had showed up immediately the first time around or whether I had to do the ndiswrapper first, so...

I installed ndiswrapper and all the necessary packages that the wiki suggests.  I installed the correct driver using ndiswrapper -i.  And I ran **ndiswrapper -l**

to which it replies:

[COLOR="Blue"]bcmlw5 driver present, hardware present[/COLOR]

If I do a **ifconfig - a**, I see eth0, lo (localhost I assume) _and something called sit0_  But if I open the Networking control panel I see Eht0 and my internal modem.  But I don't see the WLAN0 as I did the first install.

Is sit0 my Wifi card and it just wasnt detected properly? If not, does anyone have a suggestion on how to get my card to make an appearance?

This wouldn't frustrate me so badly except it was detected just fine on the first install (on the same laptop, using the same install media).  And installing ndiswrapper was a breeze the first time.

Thanks,

Craig

---

### Post by macdo on 2006-05-10
Try running ```
sudo modprobe ndiswrapper
```

---

### Post by mybootorg on 2006-05-10
[QUOTE=macdo]Try running ```
sudo modprobe ndiswrapper
```[/QUOTE]

Thanks for the advice, but I have already done that and even tried it again at your suggestion.  BTW, I'm following the NDISwrapper tutorial on the Ubuntu Wiki [here]("http://https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto") and modprobe is one of the steps, along with setting up ndiswrapper to run at start up etc.  Incidentally, this is the same exact webpage and instructions I used the first time around.  I don't get it.

---

### Post by mybootorg on 2006-05-13
Ok, I found the solution ----> [here]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto#head-c1ebf95637d110c5f01b9a1383d137f79d8cbddb")

Essentially, if you run into this same problem you're going to need to purge your system of all files related to ndiswrapper, manually download and install the latest stable version of ndiswrapper from their project site. (This will be several versions beyond what's available through apt-get.)

Then you're going reinstall the driver and modprobe and you should be good to go.

Hope this helps someone.  It sure was a pain the arse for me.

---

