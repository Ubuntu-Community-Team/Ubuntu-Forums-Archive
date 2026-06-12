---
title: "Questions related to my iBook G3"
date: 2009-07-01
forum: Apple Hardware Users
---

### Post by ppb7 on 2009-07-01
I have an iBook G3 with 128Mb RAM and running OS 9.2.2. after reading numerous threads from all over the place, I installed xubuntu Dapper and wanted to install the driver for the F5D8053 (I could only find version 3) Belkin wireless card. But my problem is that dapper doesn't seem to read the usb stick where the driver file is located or any other usb device for that matter. To be precise, i did manage to get it to read devices (a usb mouse and usb stick connected to a usb hub attached to the iBook, but the file manager crashed/froze after I'd unmounted a usb disk. Am I doing anything wrong? Or are there files that I should reconfigure? As a newbie, I don't where things are :(:?:

usb devices seem to be connected now, but applications open very slowly if at all. and the driver executable file won't execute.
BTW, the time alway reverts to January 1904 every time I switch the machine back on

---

### Post by MikeTheC on 2009-07-01
Well, I can't speak to most of what you've asked, but if the time keeps resetting then my guess is you've got a notebook battery issue. Unlike desktop computers, notebooks do NOT contain a CMOS backup battery. They use one or multiple capacitors which draw their power from the battery that runs the laptop.

Now, if what you're talking about *is* a dead laptop battery, you can search for them and probably find one. however, you also have to ask how much money you really want to invest vs. just buy a new laptop.

---

### Post by ppb7 on 2009-07-02
> **MikeTheC said:**
> Well, I can't speak to most of what you've asked, but if the time keeps resetting then my guess is you've got a notebook battery issue. Unlike desktop computers, notebooks do NOT contain a CMOS backup battery. They use one or multiple capacitors which draw their power from the battery that runs the laptop.

Now, if what you're talking about *is* a dead laptop battery, you can search for them and probably find one. however, you also have to ask how much money you really want to invest vs. just buy a new laptop.
no, the battery is not dead, and after running an update, I no longer have problems reading usb sticks and the hub.
My next challenge is that of getting the wireless dongle to work. I searched through forums for an answer but no luck. I am running xubuntu dapper (upgraded to efty i think) and, unlike [this thread]("http://ubuntuforums.org/showthread.php?t=638864") there is no GUI for me, so i will have to use the terminal (a prospect that frightens me a bit as i find it difficult to understand what i'm typing and I don't like that too much). is it even possible to set up a wireless connection befor gutsy?
Also, connecting to a network printer will be another task. again i found [here]("http://forum.xfce.org/index.php?topic=4813") a possible solution but I can't find the gnome print setup files referred to. any suggestion? BTW, I tried to set up the printer via a wired connection but, obviously, i would like to connect to the printer wirelessly.

---

### Post by urosg3 on 2009-07-02
> **MikeTheC said:**
> Well, I can't speak to most of what you've asked, but if the time keeps resetting then my guess is you've got a notebook battery issue. Unlike desktop computers, notebooks do NOT contain a CMOS backup battery. They use one or multiple capacitors which draw their power from the battery that runs the laptop.


Ibook an Powerbook do have a battery form CMOS its so called PRAM battery. On my PB G3 tnis battery is dead and i loose time every time i switch power off, cause i don't have battery in bay.

---

### Post by ppb7 on 2009-07-07
More surfing of the net took me to [http://blog.delgurth.com/2008/08/17/followup-on-the-belkin-f5d8053-and-ubuntu/]("http://blog.delgurth.com/2008/08/17/followup-on-the-belkin-f5d8053-and-ubuntu/") where i've been able to go as far as and including step 6. Step 7, when i try to edit /etc/modules (whether using mousepad or vim at the cli) I am told that it is read-only and can't be altered (at the cli, i have logged in as root). Any suggestion :?:

---

### Post by ppb7 on 2009-07-09
> **ppb7 said:**
> I have an iBook G3 with 128Mb RAM and running OS 9.2.2. after reading numerous threads from all over the place, I installed xubuntu Dapper and wanted to install the driver for the F5D8053 (I could only find version 3) Belkin wireless card. But my problem is that dapper doesn't seem to read the usb stick where the driver file is located or any other usb device for that matter. To be precise, i did manage to get it to read devices (a usb mouse and usb stick connected to a usb hub attached to the iBook, but the file manager crashed/froze after I'd unmounted a usb disk. Am I doing anything wrong? Or are there files that I should reconfigure? As a newbie, I don't where things are :(:?:

usb devices seem to be connected now, but applications open very slowly if at all. and the driver executable file won't execute.
BTW, the time alway reverts to January 1904 every time I switch the machine back on

I had to re-install dapper and now i can't even go beyond step 1 of [Delgurth's blog]("http://blog.delgurth.com/2008/08/17/followup-on-the-belkin-f5d8053-and-ubuntu/") post, i.e. the kernel won't be updated. do you think that means that it is only possible for me to install the drivers using ndiswrapper? :?:

---

