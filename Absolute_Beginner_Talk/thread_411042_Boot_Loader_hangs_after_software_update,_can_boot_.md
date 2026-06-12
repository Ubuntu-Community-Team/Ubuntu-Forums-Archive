---
title: "Boot Loader hangs after software update, can boot via Recovery Mode"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Nunnsby on 2007-04-16
Hey all, I had posted this in the Upgrades section, but got no answer, so hopefully someone here can help out. Any help appreciated! Really! :)

I am running Edgy on my Acer TravelMate 4600. Getting it to run on this laptop was no small feat, as it always hung after booting the live cd, well just sat there, but it had seemed to have loaded everything, so I had to use the "emergency shell" to get access to configure the Display Drivers, the ATI PCI Express card I have is the issue it appears. Anyway, I got it installed, and everything was running 100%. It was booting and loading and working great. 

All was working fine and my Grub boot line was: Ubuntu, kernel 2.6.17-10-generic.

I updated my software according to the software update that was recommended. I just accepted all 203 MBs of it. Haven't used Ubuntu in a few weeks since installing, hence the size of the updates.

Since the update, there were 2 new lines in Grub: "Ubuntu, kernel 2.6.17-11-generic" and "Ubuntu, kernel 2.6.17-11-generic (recovery mode)"

Upon selecting "2.6.7-11-generic" the Ubuntu Splash Screen starts up, and then hangs after about 5 secs, literally half a centimetre, after starting up. The Laptop just sits there and does nothing. No HD access, nothing.

If I then reboot into "2.6.17-11-generic (recovery mode)" it boots to a command line prompt. If I type "exit", it continues to boot fine and all works 100%. All drivers loaded and no worries with Display, wireless, etc.

Anyone have any ideas on this? Also, any ideas on how to disable the splash screen, so I can possibly see where it is breaking, and more information on this thread if need be?

Many thanks

Richard

---

### Post by NESFreak on 2007-04-16
can you post ```
cat /boot/grub/menu.lst
```

NESFreak

---

### Post by Nunnsby on 2007-04-16
Will do, am dual booting as the 3G card I'm on doesn't work under Ubuntu. Gimme a few mins.

---

### Post by Nunnsby on 2007-04-16
Hey there NESFreak

I have just sorted it out. You WERE the reason I managed to sort it out I must admit. 

Seems I had the addition : "break=bottom" at the end of my boot up in Grub. It must have copied from the original when I was having installation issues so many moons ago. 

Removed it, and all working fine now.

Thanks a stack!

Richard ;-)

---

