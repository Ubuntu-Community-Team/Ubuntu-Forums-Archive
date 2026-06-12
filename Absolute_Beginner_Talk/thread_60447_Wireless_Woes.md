---
title: "Wireless Woes"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by _Syren on 2005-08-27
I'm kinda new to Linux, and I've never even tried Ubuntu before I heard about it tonight. I've been on other distributions before and they've ran quite pleasantly, but I'm quite stumped as to how to get my wireless router working with Ubuntu.

The router itself is a BT 1800HG, and I'm using a wireless adapter PCI card in the box I installed Ubuntu on. I know that Ubuntu's picked it up and installed it, but I'm confused as to how to configure it so that I can surf the 'net in linux. 

I don't have the specific model of the card with me right now, but if it's mandatory information then I can dig the box out if needed. Any help with this would be greatly appreciated. Thanks in advance.

~Syren

---

### Post by essexman on 2005-08-28
[QUOTE=_Syren]I'm kinda new to Linux, and I've never even tried Ubuntu before I heard about it tonight. I've been on other distributions before and they've ran quite pleasantly, but I'm quite stumped as to how to get my wireless router working with Ubuntu.

The router itself is a BT 1800HG, and I'm using a wireless adapter PCI card in the box I installed Ubuntu on. I know that Ubuntu's picked it up and installed it, but I'm confused as to how to configure it so that I can surf the 'net in linux. 

I don't have the specific model of the card with me right now, but if it's mandatory information then I can dig the box out if needed. Any help with this would be greatly appreciated. Thanks in advance.

~Syren[/QUOTE]
Try the instructions in the Ubuntu Guide @ [http://www.ubuntuguide.org/#networking](http://www.ubuntuguide.org/#networking)  I recommend doing the 'properties' before the 'activate' bit and then you can put in your WEP code if you are using one.  If your wireles connected to the internet before installing Ubuntu, then it should work immediatel after configuring and activating your card.

---

### Post by ThatWeirdGuy on 2005-08-28
I too am having troubles with this.

I've just used ndiswrapper to install it and all seems well, terminal just took my commands and went back to normal, but I still can't see how to configure it. I'd look at that link, Essexman, but it appears to be broken; every time I click it I get a 404. :P Does this happen to anyone else? Any help would be totally appreciated, I mean, without the internet, what else is there to be doing...?

---

### Post by Steve1961 on 2005-09-05
Once you've managed to get ubuntu to recognise your card go into system/administration/networking.  Highlight your card and press the properties button.  Enter the name of your essid, any encryption key, and set the connection to dhcp or static IP address, depending on what you use.  Press OK and then press activate.  That should be it.

---

