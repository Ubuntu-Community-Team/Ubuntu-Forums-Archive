---
title: "weirdest thing causing lock ups"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-13
i noticed today that my computer is freezing up in ubuntu at any disk activiy.

atm im copying 5GB from Windows to ubuntu, its going at around 20-40mb/s

Right now my computer has frozen, not even my mouse moves.

my computer isnt gutless, so wtf is going on!?

i compiled a kernel earlier, frozen solid.

i have 300mb ram usage and 0bytes swap, cpu is around 30%

but random lockups of up to 1minute, no control of anything.

ideas why?

---

### Post by skymera on 2007-11-13
small update:

computer nothing runnimg, just idling.
suddenly extreme high disk ativity, system froze, solid.
so sys req REISUB out of it, and downloading AVG Linux now,
i know viruses are rare but things dont lock up on their own =S

---

### Post by FuturePilot on 2007-11-13
Intel Core 2
nVidia GeForce 7900GT
I'm thinking this might be why. There's a known regression in the current Nvidia driver that seems to only affect setups with a dual core CPU and a GeForce 7xxx card. The work around is to install the 100.14.09 driver.

---

### Post by HermanAB on 2007-11-13
Most freeze-ups are caused either by a bad ethernet driver, or a bad display driver.  So maybe you need to go to the project web site for your video adaptor and get a newer (or older) driver.

Otherwise, cranking the clock speed down a little bit (5%) may breathe new life into dodgy hardware.

---

### Post by skymera on 2007-11-14
hmm
i have the 100.14.11 driver at the moment

the driver was instaled by envy, but i will uninstall it now 

ad try the 100.14.09 driver

tahnks for replies.

also not sure whether its relevant.
but whenever i cllick a program, usually swiftfox
they create a lot of disk activiy, which i thin is wrong :(

---

