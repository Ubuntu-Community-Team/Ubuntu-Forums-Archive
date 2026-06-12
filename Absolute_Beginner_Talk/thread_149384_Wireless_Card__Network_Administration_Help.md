---
title: "Wireless Card / Network Administration Help"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by shutupchuck on 2006-03-23
I'm running 5.10 Breezy Badger on a dell laptop and I'm trying to get the wireless internet card to work. I've read many tutorials and other posts but it still doesn't seem to work. I think my main problem is that when I open up the Network Settings box (from Administration>Networking) I don't have an add or delete button under the connections tab. On the screenshots they have in the help menu there are two buttons that I simply am missing; all I have is Properties, Activate, and Deactivate. I don't know if it's a packagethat I'm missing from Synaptic or what but those buttons aren't there. 

This is what I have tried:
-installing the ndiswrapper and the ndisgtk
-installing the proper driver (using the chipset information about my card that I got from running [lspci -v | less]
-In the ndisgtk gui it said that the driver was installed and that the hardware was present but when I went into the Network Settings window all that would show up was the dialup modem connection.

Please help. I will reply promptly and wont waste your time.
-Chuck

---

### Post by neoginn on 2006-03-23
I am currently working on the same thing, could you please tell me what card you are using, and what Dell PC.

---

### Post by shutupchuck on 2006-03-23
I'm trying to use a Belkin F5D7010 54g wireless card with chipset Broadcom Corporation BCM4306

I think the laptop is an inspirion or something. It's not brand new but XP was running just fine on it. I think its got a pentium III with a little under 900 MHz and 128 MB RAM.

Let me know if you find anything that works. (also, does your network settings box also lack the add and delete connections buttons?)

---

### Post by Papa-san on 2006-03-23
I am running a Dell Lattitude C610 with a broadcomm truemobile 1300 wireless card. with the 43XX chipset.
This thing has been a pain in the butt for weeks now.
The three buttons have all you need, though. If you click on the properties tab, you will be able to put your IP and WEP, etc there.
 I am not surprised you are having issues though, and I feel your pain!

---

### Post by shutupchuck on 2006-03-23
the problem with having only three buttons is that the wlan0 doesn't even show up so i can't just click properties and do as you suggested (even though i would love to). The only connection visible is the modem connection which is useless. Did you do anything special to get your device to show up in that box other than install the drivers?

---

### Post by Papa-san on 2006-03-23
Once you hit the sudo modprobe ndiswrapper step in the aforementioned how-to, it will show up... (However, if you experience the same tingly sensations I have, when you re-boot, it will be gone again!)
](*,) 
Don't worry, it will come and go at will, for no apparent reason, and prolly won't work anyways when it is there and configured... If this isn't your experience, please let me know what you did...

BTW, which drivers are you using, and which card revision rev2 or 3, and where did you get the drivers?

---

### Post by shutupchuck on 2006-03-23
im using bcmwl5.inf and bcmwl5a.inf (I have them both installed but they don't recognize the hardware anymore). 

the card revision is revision 3

i got the drivers from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

which "aforementioned howto" are you talking about when you say the sudo modprobe step? I don't think I've done that yet because i've been working mostly with gui programs. I would also be interested to know where you got your drivers since they at least seem to be working some of the time :)

---

### Post by shutupchuck on 2006-03-23
It's working now. The problem was that when I downloaded the drivers (the .inf files and all the rest) I only kept the .inf file. I threw out all the rest. For anyone who is having the same problem I was, you need to keep the .sys file (of the same name) in the same directory as your .inf file.

So in my case, I was using the the bcmwl5.inf driver so i needed both bcmwl5.inf and bcmwl5.sys to be in the same directory when I installed the driver.

Hopefully it will continue to work. Good luck to everyone else.

---

### Post by snells on 2006-03-23
having the same problem with missing buttons, my belkin card is being shown under devices but can't add it under network settings

what's up?

---

### Post by shutupchuck on 2006-03-23
thats the same problem i was having and when i made sure the .sys file was in the same directory as the .inf file before installing the driver it worked

i dunno if you didn't read my last post or if that didn't work for you. If i'm just repeating myself i'm sorry. hope that helps.

---

