---
title: "Any hope of getting wireless working for me?"
date: 2007-02-25
forum: Apple PPC Users
---

### Post by jomny on 2007-02-25
I got a hold of an old g3 ibook from a friend recently, and since OS X was running so poorly on it I decided to give xubuntu a try and installed 6.06. It runs really well considering the hardware and I would love to use it as my regular laptop but there are are two problems. The first is that the battery is garbage so it needs a new one, however I only want to spend the money on a new battery if I can fix the second problem. That is that right now it cannot get online wirelessly.

I guess my friend somehow broke the internal antenna so airport card doesnt work. I tried putting in my netgear wireless usb adaptor not thinking I would get anything from it but it seemed to be detected when I booted it up. Under system -> network it showed a wireless device and I was quite suprised, so I installed wifi radar in hopes that I could connect to something but couldnt get it to connect. Ive never used wifi radar before so I dont know if I was doing something wrong but it did not automatically detect any networks and when I tried to enter some manually it got no signal and would not connect to any of them. Im thinking that the usb adapter isnt really working since the light that normally blinks when its connected to a windows machine only briefly blinked when it was first plugged in. From what I can see in the software it looks like its working correctly, I can deactivate and then reactivate it fine and the fact that it recognizes that its a wireless adapter must mean that its working on some level right?

Is there any hope for me getting my ibook online wirelessly? Is there any usb adapter I can get that might work? Thanks for any help you guys can give!

---

### Post by beanworks on 2007-02-26
What are the settings for the usb adapter?

Do you have the Wireless Networking tool installed, or just the radar?  I haven't used the radar, so I can't help you there, but if you have the networking tool, you can configure the usb for a network.  (Ubuntu doesn't automatically know what settings to use)

I'm currently using a linksys usb adaptor hooked up to this G4 powerbook, and it works fine, so I think there's hope for you! :)

---

### Post by sweli on 2007-03-03
> **beanworks said:**
> What are the settings for the usb adapter?

Do you have the Wireless Networking tool installed, or just the radar?  I haven't used the radar, so I can't help you there, but if you have the networking tool, you can configure the usb for a network.  (Ubuntu doesn't automatically know what settings to use)

I'm currently using a linksys usb adaptor hooked up to this G4 powerbook, and it works fine, so I think there's hope for you! :)

Hey beanworks,  what is the 'wireless networking tool' ?  

Ubuntu recognizes the chipset on my wireless card.  Seems to have the drivers installed.  I tried using the network manager (I think this is the one that Ubuntu typically installs), now I am trying network selector.  I also have WiFi radar installed.  It sees mine and other networks around me.  I have my wep key entered, and it even says it is acquiring an address and connects.  But Firefox cannot find the server.
Ideas?

---

### Post by jomny on 2007-03-04
> **sweli said:**
> Hey beanworks,  what is the 'wireless networking tool' ?  

Ubuntu recognizes the chipset on my wireless card.  Seems to have the drivers installed.  I tried using the network manager (I think this is the one that Ubuntu typically installs), now I am trying network selector.  I also have WiFi radar installed.  It sees mine and other networks around me.  I have my wep key entered, and it even says it is acquiring an address and connects.  But Firefox cannot find the server.
Ideas?

Id check first to see if you are getting an IP from your router (ifconfig in console).

Anyway I grabbed network selector from synaptic package manager and it installed fine, but when I fire it up it doesnt see any networks (there are networks it should pick up). Under networking should it say the model of my adapter or does it just say wireless adaptor for those of you who have this working? 

As I said before it seems like it is recognizing that there is a wireless adapter plugged in, and network selector shows it as being disabled when I take the adapter out, then looks ok when I plug it back in. In case it matter the adapter Im have is a netgear wg111 v2, and Im sure that it works as Ive tested it out on my windows machine. 

Any ideas of how to go forward would be appreciated.

---

