---
title: "Can anyone explain this"
date: 2010-02-28
forum: Apple Hardware Users
---

### Post by jazzlukejosh on 2010-02-28
Can someone tell me step by step how to get to edit the following in Xorg.conf? We've gotten to /etc/X11/xorg.conf file and nothing happens. Apparently we need to enter the following:




Section "Monitor"
        Option		"HorizSync"	"30-82"
        Option		"VertRefresh"	"56-76"
EndSection
 



Secondly how do you get to add a manual entry to the /etc/X11/xorg.conf file? Apparently I need to bring up a screen that starts with the words Section "Device" with the identifier etc.. under it in order to fix low resolution problems.

---

### Post by Arkitekt on 2010-02-28
Im still pretty much a noob so forgive me if this is wrong but.. couldnt you use open it up via gedit through terminal?

```
$ gksudo gedit /etc/x11/xorg.conf
```

---

### Post by jazzlukejosh on 2010-02-28
[_Arkitekt. Cheer_s]("http://ubuntuforums.org/member.php?u=193531")!

We are in Xorg.conf gedit, however no commands seen to work in here. What I'm trying to do is insert a manual setting into the /etc/X11/xorg.conf file that will help Xorg find the ATI (r128) driver so Xorg can use high resolution true colour mode.

I have the settings that work and they start with the heading:

Section "Device"

Identifier "Rage128PR"
Driver "R128"

etc..........

Can I bring up this Section of Xorg and find "Device" to change these settings or do I actually just enter the settings I've been given to find the R128 then just close gedit?

---

### Post by linuxopjemac on 2010-02-28
I use nano
```

sudo nano /etc/X11/Xorg.conf
```

after editing, CTRL-X and "y" to save

---

### Post by underquark on 2010-02-28
It would, perhaps, be more helpful if you tell us what you are trying to achieve rather than how you think you want to go about it.  Editing xorg.conf, for instance, might not solve your problem.  You might be better using xrandr as documented [here](https://wiki.ubuntu.com/X/Config/Resolution) or [here](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html).

---

### Post by jazzlukejosh on 2010-02-28
Hi and thanks. What we are trying to do is get true colour resolution. That's all. We had it on this iMac G3 PowerPC before when we were running OSX. But changed operating system to Ubuntu 9.10 and computer works better and faster but can't get true colour display resolution. We assumed that Xorg on boot up isn't locating the ATI r128 driver and just defaulting to the standard veso driver.

We just manually entered five sections of new settings that we got off a forum page ( device, monitor, Screen, Module and Server Layout ) using nano and pressed control X and Y to save but no difference when rebooted.

The settings we got were very specific and had spacing and indents which we didn't worry about. But everything was spelt right and quotation marks were observed.

Also can't install flash player but that's another thread.

---

### Post by jazzlukejosh on 2010-02-28
P.S. When we try to change display settings in desktop properties we get message "the composite extension is not available". Thanks

---

### Post by linuxopjemac on 2010-02-28
here are some nice imac Xorg.conf files:

[http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf](http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf)

you also need to have the ati drivers installed:
```

sudo apt-get install xserver-xorg-video-ati
```

---

### Post by jazzlukejosh on 2010-02-28
Thank you for the iMac Xorg.conf files my friend. But just one more question, do I have to copy and past each section of files into nano and then save or can I copy all three sections in at once.
 
Also do I type "sudo apt-get install xserver-xorg-video-ati" into the terminal or into nano as well.
 
Sorry I'm such a dummy, I've just come off years of Windows.
 
Thanks again

---

### Post by linuxopjemac on 2010-02-28
sudo apt-get install ... you do outside of nano. It's the command to install things. You can paste everything at once in nano.

---

### Post by jazzlukejosh on 2010-02-28
> **linuxopjemac said:**
> here are some nice imac Xorg.conf files:

[http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf](http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf)

you also need to have the ati drivers installed:
```

sudo apt-get install xserver-xorg-video-ati
```


After I pasted in and executed  "sudo apt-get install xserver-xorg-video-ati" in the terminal, I got this message below, does that mean the files that I pasted in nano didn't work?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-ati is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

---

### Post by linuxopjemac on 2010-02-28
It means that xserver-xorg-video-ati is already installed.

---

