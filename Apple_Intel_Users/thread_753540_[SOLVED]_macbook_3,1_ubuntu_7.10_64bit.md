---
title: "[SOLVED] macbook 3,1 ubuntu 7.10 64bit"
date: 2008-04-12
forum: Apple Intel Users
---

### Post by darksidedude on 2008-04-12
hey all, first all, this is a regular macbook not PRO, and i am running 64bit ubuntu, I need help getting the broadcom 4328 in my macbook working, i tried the info page, the one about the santa rosa macbook, I can get the card to work no matter how hard i try, Ndiswrapper dosent like me:( please help

---

### Post by vgrisham on 2008-04-12
> **darksidedude said:**
> hey all, first all, this is a regular macbook not PRO, and i am running 64bit ubuntu, I need help getting the broadcom 4328 in my macbook working, i tried the info page, the one about the santa rosa macbook, I can get the card to work no matter how hard i try, Ndiswrapper dosent like me:( please help

We have a laptop at my school with the 4328 and we've not been able to get it to work. Supposedly, [these]("http://ubuntuforums.org/showthread.php?t=572005&highlight=broadcom+4328") instructions should do the trick, but we've hit a brick wall. Good luck.

EDIT: You might try the new [Linuxant driver loader]("http://www.linuxant.com/driverloader/"). I used them for my conexant modem and it worked like a charm.

---

### Post by cyberdork33 on 2008-04-12
what is the output of 'ndiswrapper -l' (that's an L not an I)

also, if you are running hardy, there is a problem with ndiswrapper.

---

### Post by darksidedude on 2008-04-13
when i do ndiswraper -l   it says

bcmwl5 : driver loaded hardware present

---

### Post by cyberdork33 on 2008-04-13
> **darksidedude said:**
> when i do ndiswraper -l   it says

bcmwl5 : driver loaded hardware present
ok, what about 'ifconfig' you should have an entry that looks like wlan0

Also, you never said what version of Ubuntu you are on.

---

### Post by darksidedude on 2008-04-13
ok got an update here, i used that linuxant thing, to load the drivers for me, if works, ubuntu recognises the divise, and stuff, i connect to my wireless (unsecured) and firefox sits there telling me, looking up google.com, im on DDSl but it isnt so slow it takes 10 mins to look up google!!, I disabled Ipv6, since my isp doesn't use it. now firefox just said cant find the server... can't get updates or even use synaptic, 

im using ubuntu 7.10 desktop amd64

thanks

---

### Post by vgrisham on 2008-04-13
A couple of things need to be configured. First of all, go to System>Administration>Network. 

If you're running hardy, unlock network manager.

Select your device. Disable Roaming Mode and choose DHCP. Type in your wireless access point's SSID and hit OK.

Then try Firefox again.

---

### Post by darksidedude on 2008-04-13
when i go into the configureations. and select DHCP, above it where it asks for the ESSID there is no choice for no encription? do i just leave it as WEP?

---

### Post by darksidedude on 2008-04-14
installed a new favorite program, wifi-radar. so i can connect and browse this forum useing Ubuntu!!! now I need help getting the internet to go at a reasonable speed, it is unbearable slow, like the old saying every silver lineing has its cloud =P

---

### Post by vgrisham on 2008-04-14
> **darksidedude said:**
> when i go into the configureations. and select DHCP, above it where it asks for the ESSID there is no choice for no encription? do i just leave it as WEP?

If your network is unsecured, don't worry about it. Unless you enter a key, the security choice doesn't matter.

---

### Post by vgrisham on 2008-04-14
> **darksidedude said:**
> installed a new favorite program, wifi-radar. so i can connect and browse this forum useing Ubuntu!!! now I need help getting the internet to go at a reasonable speed, it is unbearable slow, like the old saying every silver lineing has its cloud =P

Well, wireless is definitely slower than dsl to ethernet. I get my Internet access free from our local university which broadcasts it wirelessly to the town in which I live. 

Check out [these instructions]("http://www.linuxjournal.com/article/8317") for speeding up Firefox.

You might want to mark this thread as resolved.

---

