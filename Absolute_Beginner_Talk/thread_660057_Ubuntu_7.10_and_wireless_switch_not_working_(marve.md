---
title: "Ubuntu 7.10 and wireless switch not working (marvell libertas)"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by bjtk on 2008-01-06
hi there people,

right i am a complete newbie to this stuff after been on windows since the days of windows 95 

basically ive installed this ubuntu 7.10 after getting so p****d off with windows crashing and losing my data twice. (my own fault for not backing up often enough as well!)


im on an advent 7105 laptop and since i installed this my wireless button on the top of my laptop just wont switch on,just a simple press of it on windows would turn it on then i could happily look for my wireless network,i dunno if theres some settings i need to change in order for it to work but i would of thought it would still turn on but just not work? anyway im confused,massively.and i dont know how to use the technical side of this so please be nice to me 

oh and the wireless device on the laptop is marvell technologies 88w8335 (libertas) 802.11g wireless (PCI) if thats any help

so any help would be greatly appreciated

Thanks,

Ben

---

### Post by itsbradman on 2008-01-06
you prob need the drivers for the card.  have  you looked in the restricted driver manager to make sure you have the drivers installed?

---

### Post by eugenesan on 2008-01-06
Last time I've checked there several different drivers for Libertas for 2.6 kernel.
One is libertas on USB that resides in official kernel.
Second called 8k...something somewhere on then net.
Third is Marvell Commercial driver for older 2.6 kernels.
I was not able to use any of mentioned above.

But, there is another possibility to use this WiFi adapter,is to use windows driver using ndiswrapper.
There are even reports of people who succeeded.
Just google for it and will find how to use it.

P.S. In case I am wrong about usability of Native Linux drivers please correct me. I'll be very happy to know how to use them :-)

---

### Post by stevel05 on 2008-01-07
Hi I am a Linux newbie too using ubuntu on an advent 7105, and decided to go for the simple approach.  I downloaded ndisgtk and associated ndiswrappercommon and ndiswrapper-utils-1.9 from the synaptic package manager.

Ran the windows wireless driver utility from System - Administration, pointing it at the windows drivers I had salvaged before overwriting windows, and lo and behold the wireless worked, switch and all.

My 1 small remaining issue is that the wireless doesn't work on reboot unless I change something in the wireless driver setup, i.e. static IP to DCHP or back.  Does anyone know how to call this process from a startup script so that it works on boot up?

Steve

---

