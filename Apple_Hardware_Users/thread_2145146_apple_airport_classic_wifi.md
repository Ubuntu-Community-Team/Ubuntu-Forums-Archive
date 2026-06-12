---
title: "apple airport classic wifi"
date: 2013-05-14
forum: Apple Hardware Users
---

### Post by imacg3ppc on 2013-05-14
Trying to get my wifi working on the g3 slot load. The "radio" is working from the net manager applet, in other words, i can see all the networks. I have a problem with a weak signal, so im trying to trouble shoot if this is an apple card>non-apple router issue.. or if i just need to boost my signal.

I am going to try to access router settings and change to work with 802.11 b and g, as i have read the known issues page regarding this. But maybe someone who has an ap classic card will have some info!

I see surrounding networks, all have 4 bars for signal stregnth, the bars are grey. My network that i have added to auto-connect does not show bars however, the icon is the wifi ")))" signal, if you catch my drift. When i click connect the tooltips balloon says 'configuring network <name>' and then drops out a minute later and says disconnected. I'm thinking its a language barrier issue but does anyone know any tweaks on the lubuntu end that might help??

Thanks all!

---

### Post by este.el.paz on 2013-05-18
imacppc:

I'm just punting here, I'm not booted in my Linux partition to check, but you didn't specifically mention that you added the wifi driver . . . probably some variation of b43, but in G3 it might be the "legacy" driver . . . it might be that the driver is close enough to give you some function, but not the exact one . . . there should be links to the wifi drivers from the PowerPPC FAQ . . . or Lubuntu should have the "Install drivers" application that finds them for you and install them . . . .  It sounds like maybe you did that, but just in case.  

I also saw in other threads when I was trying to get wifi working on my G4 & Intel units . . . the suggestion to move the computer within inches of the router to "show" the computer the signal.  It shouldn't matter if it's non-apple router, but sometimes in Linux you have to fiddle with the type of encryption, where you enter the passcode the dropdown menu may show different encryption choices and that might get you "in" . . . .

e.e.p.

---

### Post by imacg3ppc on 2013-05-23
Hey, thanks for the reply!

I've been researching this more and came across the original copy of the imac's manual. It says there's an integrated antenna in the case that you need to unclip to install ap card. So i am going to see if the antenna is present because i know it's not plugged in, as i looked for the antenna previously. I will definitely try to see if another driver makes a difference. So if all of that fails... I'm going to build a yagi antenna.

Any experience with airport express anyone? Wondering if i should add an express station, but OS X has the nice airport app... and i don't want to waste the money if ubuntu wont play nice and communicate optimally with an express base...

---

### Post by danield on 2013-05-24
The first generation Airport cards in G3s can't connect to WPA2 networks, only WPA and WEP.  For WPA connections I think you need to install linux-firmware-nonfree.  Also you could try wicd.  To use it, you have to first remove Network Manager, though.

---

