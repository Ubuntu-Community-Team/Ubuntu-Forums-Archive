---
title: "Safely removing PCMCIA card"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by dreaswar on 2007-07-30
hi,

i run ubuntu 7.04 on a laptop (32 bit). i use a wireless adapter a Dlink DWL G 630. 

i also have a PCMCIA card USB 2.0 adapter which i use for external DVD writing. 

How do i 

             1)safely switch off my net connection,
 
              2)safely eject the PCMCIA net card and
 
             3)insert the USB adapter. 

             4)After writing the DVD i want my net card back on and connection enabled.

i dont want to spoil my net connection because i had lot of diffculty wth tis card and had to finally use ndiswrapper to get connection enabled, so i dont want to lose anything by just taking out the card te wrong way. 

i read on some post that there is a command called "pccardctl"

how to go about it safely?? 

i am a new bie.... so any command line.. please be clear and dont assume i know...:(

thanks...

---

### Post by shearn89 on 2007-07-31
Open a terminal (applications -> accesories (i think) -> Terminal) (there may be a shortcut somewhere on the desktop).

Then type:```
pccardctl eject
``` which should stop you're card. You can do the same thing to stop the usb adapter.

---

