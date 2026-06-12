---
title: "Can't find my wireless network"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by siege911 on 2007-10-26
I put in a Linksys network adapter into my Gutsy box and it found and installed all of the drivers I needed. However I can't find my network or any other network in the vicinity. My Windows laptop right next to Gutsy finds the network quickly and sees 2 other wireless networks in the area. It also sees a unencrypted wireless network called "kiosk" which is what my Ubuntu box is named. I tried "Connecting to Other Wireless Network" and manually entering my encryption key but I'm getting nothing.

Is there something I am doing wrong? How do I connect to my wireless network?

---

### Post by n3tfury on 2007-10-26
is roaming enabled in network manager?

---

### Post by siege911 on 2007-10-29
> **n3tfury said:**
> is roaming enabled in network manager?
Yes it is.

---

### Post by mjitkop on 2007-10-29
Is your router broadcasting its SSID? I couldn't connect to my wireless network until I finally decided to broadcast my SSID.

It's probably not your problem because you said your Windows computer does see other networks in the neighborhood. I don't think all your neighbors have SSID broadcast disabled.

Anyway, it does not hurt to ask. ;)

---

### Post by Inxsible on 2007-10-29
> **mjitkop said:**
> Is your router broadcasting its SSID? I couldn't connect to my wireless network until I finally decided to broadcast my SSID.

It's probably not your problem because you said your Windows computer does see other networks in the neighborhood. I don't think all your neighbors have SSID broadcast disabled.

Anyway, it does not hurt to ask. ;)I had the same problem. In Feisty, even if I did not broadcast my SSID, it would connect since I put in the SSID manually while creating the account. 

But in Gutsy, it seems to have lost that ability. I had to broadcast my SSID to be able to connect. Looks like I am not alone and it might be a bug.

---

### Post by n3tfury on 2007-10-29
> **Inxsible said:**
> I had the same problem. In Feisty, even if I did not broadcast my SSID, it would connect since I put in the SSID manually while creating the account. 

But in Gutsy, it seems to have lost that ability. I had to broadcast my SSID to be able to connect. Looks like I am not alone and it might be a bug.

hm, i'll have to test that when i get home.

---

### Post by gbold on 2007-10-29
I added Gutsy to my work Dell Precision M90 laptop for a dual-boot XP/Ubuntu system and I had no problems with the wireless.  In fact, I've had no problems with anything with this OS.  My home SSID is not broadcast but once I set up a wireless account for it and enabled wireless networking, logged out and then back in, I was on the 'net.  I have to admit this is the best version of Ubuntu yet...  XP won't recognize my 8GB SD card in the built-in reader but Ubuntu does!  Now if I can only figure out how to set up VPN (we use Nortel in XP and there is no Linux version available) so I can connect to work...

I guess what I wanted to say is have you checked that wireless is enabled?

Greg

---

### Post by siege911 on 2007-10-29
I am broadcasting my SSID. I even tried adding a secondary Wireless Access point to my network with no security, just to see if it'd pick that one up but nothing. My Windows Laptop saw both of them instantly and with a strong signal.

I guess it could be my wireless card. I used to have it in a Windows box and it worked at the time, but I haven't used it in 3-4 months. I'll test that out a little more.

---

### Post by mistergq on 2007-10-29
my Gateway laptop did not automatically work when I installed Fiesty on it.  With gutsy, I had to use a restricted driver that was not freeware.  With my old gateway laptop, I have a PCMCIA wireless card because the built in one died.  That card automatically worked out of the box with Linux.  So it is a hit or miss type of thing.

Let us know the specs of the wireless card you are using so we can better help you.

---

### Post by narfster on 2007-10-31
well I have an interesting story too...
bought TL-WN321G a USB wireless adapter and it works grate with windows XP and the ubuntu live CD.
i see the other peoples networks too...
installed ubuntu and it worked but then after a while, like a day i lost the ability to find the networks around.

yes "roaming" is on, and the card is recognized by the OS. 
everything is still  working fine with the winXP....  so what happened?

i went crazy with this problem, so i reinstalled the OS, didn't help.  isn't strange?! and with the live CD i can surf! haaaaaaaaa! :P

---

### Post by Hilko on 2008-04-13
> **narfster said:**
> well I have an interesting story too...
bought TL-WN321G a USB wireless adapter and it works grate with windows XP and the ubuntu live CD.
i see the other peoples networks too...
installed ubuntu and it worked but then after a while, like a day i lost the ability to find the networks around.

yes "roaming" is on, and the card is recognized by the OS. 
everything is still  working fine with the winXP....  so what happened?

i went crazy with this problem, so i reinstalled the OS, didn't help.  isn't strange?! and with the live CD i can surf! haaaaaaaaa! :P

The same happened to me this afternoon. Wireless was working fine. I shutdown my laptop, then turned it on two hours later. Couldn't detect any wireless network anymore ! Entering the configuration manuallly didn't help. It just stopped working after I turned on my laptop again! For no reason !
How is this possible !? and more important: How do I get it working again ?

---

