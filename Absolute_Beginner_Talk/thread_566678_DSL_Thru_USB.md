---
title: "DSL Thru USB"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Drevix on 2007-10-03
How do I get Linux to recognize that my internet connection is now thru the USB port and not an ethernet card?

The USB ports are there, my DSL modem (Westell 6100) is there. No connection. What things I've found to do with internet/network connection just calls up a dialog window with dial-up nonsense.

---

### Post by yabbadabbadont on 2007-10-03
USB networking support is, at best, incomplete in linux.  If possible, stick to using an ethernet connection to your DSL modem.

---

### Post by Drevix on 2007-10-03
> USB networking support is, at best, incomplete in linux. If possible, stick to using an ethernet connection to your DSL modem.


My network card is an old Realtek 10/100, basically junk that throws off a lot of heat. I pulled it out but if there's no other way to get Linux to work with the USB I guess I'll just have to put it back in.

I don't understand why Linux has to be easy with some things and so difficult with others, USB networking/internet connection has been around a long time. I was doing that stuff way back on my old P-II.

---

### Post by yabbadabbadont on 2007-10-03
Just because it has been around, doesn't mean that the hardware manufacturers have released drivers or specifications for their chipsets...  put the blame where it belongs.  ;)

Anyway, I did a little searching around (you did that too didn't you?) and you might try running, in a terminal window: ```
sudo adsl-setup
```

---

### Post by Drevix on 2007-10-03
As always, I search the forums and/or do a google search first. Often until my head starts spinning and my eyes go square. :-)

Tried the sudo adsl-setup and got a "Command Not Found".

My DSL modem is recognized as being on the USB port in Linux. There just doesn't seem to be an interface between them, at least that I can find, that says "Hey! This is an internet connection".

---

### Post by str8line on 2007-10-04
Even in Windows using USB networking is not the greatest and far from the best solution.  I did find this reference in the forums though:

[DSL Thru USB]("http://ubuntuforums.org/showthread.php?p=3471316")

---

### Post by Drevix on 2007-10-04
> Even in Windows using USB networking is not the greatest and far from the best solution. I did find this reference in the forums though:


Well, my network card is old. It's barely PCI. :-) The only reason it's even in my computer is for an internet connection. My connection speed is much better using the USB port instead of my network card, at least in Windows.


> DSL Thru USB

Wrong link?

---

### Post by n3tfury on 2007-10-04
> **str8line said:**
> Even in Windows using USB networking is not the greatest and far from the best solution.  I did find this reference in the forums though:

[DSL Thru USB]("http://ubuntuforums.org/showthread.php?p=3471316")

lol

---

