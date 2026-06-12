---
title: "Belkin Wireless problem"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by thewizz2009 on 2007-04-19
Hey

Im trying to setup my wireless, on feisty fawn live cd, if i put my adapter, F5D7050 prismaxp driver, everything goes very slowly and eventually stops, however i cant get any connection without my adapter, so how can i setup my wireless adapter,

i can see my windows drives, can i download what i need and then bring it across when in ubunutu.

What do i need ndiswrapper, any help is much appreciated

Thanks

---

### Post by rich.bradshaw on 2007-04-20
I used ndsiwrapper for similar card.

Basically you need the drivers which you would install in Windows.

if you 

sudo apt-get install ndiswrapper-utils ndisgtk

then on the system menu will be an entry called Windows Wireless Drivers. From here you select the Windows driver and it will try and make it work.

Mine was on my Windows partition in Program Files/Belkin/Belkin Network Manager/Drivers/PCI/ then an inf file...

---

