---
title: "CPU heating problem"
date: 2011-12-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by aminshayegh on 2011-12-06
Hello 
I have asus n55sf and installing Ubuntu 11.10 amd64  ; now as soon as i turn on laptop and boot Ubuntu its CPU fan starts and after a while my key board become hot due to CPU heat and during these time i only read PDF.
 its CPU is core i7 - 2630QM.

---

### Post by Lars Noodén on 2011-12-06
Are you sure that there are not two problems ? 1) the heat , 2) the fan not running.

Or is the fan running, too?

---

### Post by r_mano on 2011-12-06
Probably not related, but I have a 1005PE with a "nice" hardware bug... sometime the fan doesn't start, the laptop becomes really hot until I blow (really!) strongly into the fan output grid to "unblock" it... and then all is all right. :confused:

Just to say it, maybe can help some other user... :)

---

### Post by ariamir on 2011-12-12
I have the same laptop (n55sf) but the cpu is 2670qm.
I think your problem is not the cpu but the nvidia graphics card, you have to install bumblebee.

Follow this tutorial it worked for me: [http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)

for the calls i used:
cardoff:

\_SB.PCI0.PEG0.GFX0._DSM {0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47,0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0} 0x100 0x1A {0x1,0x0,0x0,0x3}

\_SB.PCI0.PEG0.GFX0._PS3 

cardon:

\_SB.PCI0.PEG0.GFX0._PS0 

I hope it helps.

---

