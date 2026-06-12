---
title: "Display, audio and airport problems with ibook G3"
date: 2008-07-18
forum: Apple Hardware Users
---

### Post by theojepsen on 2008-07-18
I have an ibook G3 with the following specifications:

powerpc G3 500MHz
587MB RAM
120GB HDD
ATI Rage 8MB VRAM

I managed to run Xubuntu on it without a problem, but after adding more ram I wanted to use Ubuntu. I installed 8.04 via the alternate install CD for powerpc twice, both times with the same result.

Display: The screen is divided into sections, the right side is black and the bottom is mirroring part of the desktop. Here is an image of it: [http://img385.imageshack.us/img385/8645/cimg0638tm5.jpg](http://img385.imageshack.us/img385/8645/cimg0638tm5.jpg)

Audio: When I click the audio applet it says "The volume control did not find any elements and/or devices to control." You can see more of it in this image: [http://img385.imageshack.us/img385/8645/cimg0638tm5.jpg](http://img385.imageshack.us/img385/8645/cimg0638tm5.jpg)

Airport: Although it connects to my wireless network, the applet does not show that it is using wireless for some reason. Is there a way to get the wireless strength and information their too?

How can I fix the display and audio problems? These are the only factors that are inhibiting me from using Ubuntu properly.

Ubuntu is my favorite linux distro, especially for its really helpful community. I would really appreciate it if someone could help me out here.

Thanks

---

### Post by chaosstorm on 2008-07-23
I have the same audio issue, but my display and wireless are fine. (as far as I can tell) 

It keeps saying no devices are found...

running a macbook 2,1

---

### Post by cyberdork33 on 2008-07-23
> **chaosstorm said:**
> I have the same audio issue, but my display and wireless are fine. (as far as I can tell) 

It keeps saying no devices are found...

running a macbook 2,1
You should start a different thread. He is using a powerpc-based Mac, you are using an Intel-Based Mac. They are entirely different beasts.

---

### Post by theojepsen on 2008-07-23
Yeah, its true. MacBooks have intel processors and different hardware compared to the iBooks and other powerpc based computers.

I have managed to resolve 2 of the 3 problems.

1. Display: I found a copy of someone's working xorg.conf and copied the screen section into mine.

2. Audio: I added "snd-powermac" to /etc/modules, which enabled the sound after a reboot.

I would still like to know how to browse for wireless networks. On my MacBook when I select the network applet I can see and connect to all the wifi networks around me. The applet shows the two black monitors even when its not connected.

Well, its working well on my ibook. Better than win XP would work on a 7 year old computer, maybe even better than win XP would work on a modern, virus infested computer.

Would appreciate it if someone could help me with the wifi problem.

Thanks

---

### Post by nkuvu on 2008-07-28
> **theojepsen said:**
> 1. Display: I found a copy of someone's working xorg.conf and copied the screen section into mine.
I'm having this exact problem on my Pismo with a new installation of Ubuntu. Could you point out where you found the modified xorg.conf, or just post the relevant section?

My own xorg.conf contains very little actual information:
```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```
Was there more in yours than this? (The iMac G3 that I was trying to get Ubuntu installed onto had a lot more detail)

---

### Post by theojepsen on 2008-07-28
OK. I searched a while to find what I used to "fix" my problem:

[http://lists.freedesktop.org/archives/xorg/2007-June/025114.html](http://lists.freedesktop.org/archives/xorg/2007-June/025114.html)

While searching for it I also came across this, which looks very useful:

[http://pierre.baudu.in/ibook/](http://pierre.baudu.in/ibook/)

I hope this solves your problems, as it did with some of mine.

I am still having problems with my airport. Yes, ubuntu detects it but it doesn't manage it very well. If I am near a open network it connects to it automatically. Since I recently secured my network with WEP 128bit (yes, I know its unsafe, but its all I got on this old router from ebay) I am unable to connect with ubuntu, but I have to boot OS X to use it. Since the applet is not working I think CLI is the only way to go about it. How would I connect to the network via CLI? How can I view all networks around me via CLI?

I would be grateful if anyone could help me.

---

