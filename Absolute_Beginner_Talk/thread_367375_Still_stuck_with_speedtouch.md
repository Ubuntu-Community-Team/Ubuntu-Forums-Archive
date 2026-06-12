---
title: "Still stuck with speedtouch"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by roylond on 2007-02-22
I've been trying for nearly a week to get the speedtouch modem to work but still nothing.
My setup is version 6.06 on a bare hard drive in a caddy and this slots into my pc. There is another hard drive which is also in a caddy with windows98 se. I can swap over each caddy which prevents me from damaging the windoze which is up to now my only access to the internet. My internet access is by  a speedtouch 330 revision 4 with a usb connection. I just cannot get it to work despite using serveral instructions from different sources and trying each one in turn. 
I have tried to use an ethernet card and router/modem but this worked with Linux would not work under Windoze.
Although I am new to Ubuntu I would like to get it work with a usb modem. 
Any other suggestions appreciated

---

### Post by arochester on 2007-02-22
I got a Speedtouch from Tiscali. After reading an article in "Micromart" magazine I did not use it and bought a wired (modem) router from Ebay instead - A "BT Voyager 205". It was easy and has performed faultlessly...

---

### Post by ^rooker on 2007-02-22
You've mentioned that you've tried using Ethernet - and it worked only in linux not windows. 
I don't believe that this is true, since Ethernet is default and USB the "new" way of doing it.

I assume you're talking about some DSL connection, so for connecting in windows, give your ethernet card the IP 10.0.0.140/255.255.255.0 and then create a new VPN connection (using some wizard), point it to the gateway "10.0.0.138" (your modem), provide username/password and you're online.


I'd recommend that you use ethernet anyway, because then you can simply forget about driver issues, etc... - you can also easily add an external router if you like (not possible with USB).


Sorry that I can't help you with USB...

---

### Post by roylond on 2007-02-22
When I installed the card and switched on windows dialogue came up with the usual New Hardware decteded trying to install the drivers routine.Requesting disks etc.  Eventually I finish up the card not being able to be used as there are no drivers loaded. The card was a Linksys 10/100.

---

### Post by laidback on 2007-02-22
Started with a speedtouch 330 myself, got it working in Mandriva but not Ubuntu. In any event it was a pain. Switched to a router/modem, soooooo much better. Have a similar rig to yourself even down to the caddies although I use 2 computers. XP and Ubuntu boxes are linked to the internet, I don't use the XP box anymore, the wife does.

The router is an eTEC and cost around £30. Install software had XP running over wired ethernet within 10 mins. Ubuntu took me a little longer but was quite straight forward. I use DNS (not DHCP) as my ISP provider supplies the addresses. I am very pleased with the setup.

Could it be that Win doesn't like being taken out. I seem to remember that when I tried this on my XP box (just for fun) the XP system complained when I put it back in. It seemed to believe that I'd moved it and was wanting to reregister itself, a knock on effect from the BIOS switching hdd definitions perhaps. Maybe your are inadvertantly disabling something. I've installed XP and Ubuntu in a friends machine, one disc for Win, the other for Ubuntu, dual booting. That works fine.

---

### Post by roylond on 2007-02-22
> **laidback said:**
> SNIP 

Could it be that Win doesn't like being taken out. I seem to remember that when I tried this on my XP box (just for fun) the XP system complained when I put it back in. It seemed to believe that I'd moved it and was wanting to reregister itself, a knock on effect from the BIOS switching hdd definitions perhaps. Maybe your are inadvertantly disabling something. I've installed XP and Ubuntu in a friends machine, one disc for Win, the other for Ubuntu, dual booting. That works fine.

My windows version is 98se and I power down before I take out the caddy and it hasen't complained up to now. Its just that with the Ethernet card I worked a couple of years ago when I looked at Suse but Windows would not accept it for some reason. I gave up trying to use any distro of Linux until I got hold of the 6.06 CD. There is a Howto in the forum but it written for 5.10 and it doesn't seem to work in 6.06. I've tried several versions to try to get the Speedtouch to work but failed up to now. :(

---

### Post by laidback on 2007-02-22
I think you'll find that the speedtouch doesn't work with Ubuntu.

---

### Post by Bert the Button on 2007-03-04
I'm using a Speedtouch 330 rev.4.00 with Ubuntu right now; no ethernet though, just the basic USB and line filter.  I used the following tut, and just needed to tweak the VPI/VCI settings afterwards.  All works fine now!  :) 

[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

Hope that helps  :)

---

