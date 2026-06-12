---
title: "Wireless Crashes my Ubuntu"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by A G I on 2006-12-17
hi I am a new user who has just installed ubuntu 6.06 onto my old compaq evo N600c.
I am using a PCMCIA Netgear WG511v2 wifi card.

After searching these forums I eventually managed to get the wireless card to start responding but ever time it comes online and connects to my router Ubuntu crashes.

I used ndiswrapper with the XP inf and sys files - adapter wasn't doing anything so I tried,

#sudo depmod -a  
followed by:
#sudo modprobe ndiswrapper

I'm not to sure what those last two commands are (found them in this forum) but after modprobe the card starts blinking (good).  I select my wireless network, the card locks on then the screen freezes.  The mouse will still responds but I am unable to get anything to respond.  If anyone can please help it would be much appreciated.  
Also when ubuntu crashes is there a way to flick to a terminal/another session to kill the adapter????

---

### Post by A G I on 2006-12-17
Fixed it!
Wht WG511 v2 drivers for XP seemed to be causing the crash.
Used the WG311v3 and it works really well.

Now I need to get the DNS servers to stick and figure out why the close buttons sometime's has lines going through it....

---

### Post by A G I on 2006-12-17
Ubuntu was working great but here I am back in XP.

After updating from 6.06 to 6.10 my wireless adapter stopped working!

It appeared ndiswrapper was uninstalled so I reinstalled via apt-get install ndiswrapper-utils.  Afterwards all the same settings/drivers where configured in ndiswrapper so I tried modprobe but it just quickly returned to the next line making no difference.  I'm guessing modprobe doesn't do anything as I have added an alias? (I don't know what I'm talking about linux newbie) ndiswrapper -m but still that doesn't help.

As the method metioned above is how I got it to work the first time and now it isn't responding at all again I don't know what to try, all the same hardware and drivers just an upgrade to 6.10. 

I tried removing and adding the drivers again... still nothin

Do I need to change the driver I 'm using or remove something from 6.10?

Please Help!!!

---

