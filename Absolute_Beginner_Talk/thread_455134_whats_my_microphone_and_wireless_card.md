---
title: "whats my microphone and wireless card?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-26
Can someone tell me what my microphone model is and my wireless card to?

---

### Post by meng on 2007-05-26
*invokes psychic powers*
nope, can't help you :)

Actually:
lspci
might help you

(if you get too much to look through, try:
lspci | grep ireless

---

### Post by drowner on 2007-05-26
this is a joke, right?

---

### Post by drowner on 2007-05-26
> **mojo123 said:**
> Can someone tell me what my microphone model is and my wireless card to?

Try this

sudo lookathefreakingmicrophone

read the side

repeat with wireless card.

---

### Post by mojo123 on 2007-05-26
no
And dont spam
Its a laptop all is built in


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by meng on 2007-05-26
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

What is the model number/code of this laptop?
The microphone is probably just part of an integrated sound card.

---

### Post by mojo123 on 2007-05-26
its a HP Pavilion DV6000

---

### Post by DJ Wings on 2007-05-26
Use the ipw3945 drivers to get your NIC working. Get them via AX2 which you can download... from... the Internet...
Dang! Catch-22'ed again!

---

### Post by meng on 2007-05-26
My wireless worked out of the box, with Feisty 7.04. Same wireless card!
Perhaps you could explain what problems you're having, and we can figure out whether it is drivers, configuration or something else.

---

### Post by mojo123 on 2007-05-26
can someone post a link for the wireless card drivers for **Windows**

---

### Post by DJ Wings on 2007-05-26
> **meng said:**
> My wireless worked out of the box, with Feisty 7.04. Same wireless card!
Perhaps you could explain what problems you're having, and we can figure out whether it is drivers, configuration or something else.

He didn't say that he had any problems with it. So Feisty comes with ipw3945 drivers? No wonder Dell uses that card for their Linux laptops (which I'm getting, hopefully! yay!).

---

### Post by mojo123 on 2007-05-26
i just installed vista for gaming, and now i need all my drivers

---

### Post by DJ Wings on 2007-05-26
Drivers for Ubuntu, or Fista? Your wireless should be supported in Ubuntu.

---

### Post by mojo123 on 2007-05-26
for vista

---

### Post by DJ Wings on 2007-05-26
These are the Ubuntu forums, not the Winblows Fista forums. All right?

---

### Post by Enverex on 2007-05-26
Anyone else find it ammusing his avatar says "Live Smart"?
;)

---

### Post by mojo123 on 2007-05-26
guys stop flaming just because im a noob

---

### Post by DJ Wings on 2007-05-26
> **Enverex said:**
> Anyone else find it ammusing his avatar says "Live Smart"?
;)

Word. :lolflag: Ask for Vista help on UbuntuForums.org and you won't be living at **all** for much longer anyways. 
This should be amusing...:popcorn:
EDIT: We're not flaming you because you're a n00b... Hint: It has to do with the forum you're posting on.

---

### Post by meng on 2007-05-26
Okay, so in other words, the hardware works fine with Ubuntu, but doesn't work with Vista, and it's easier to _identify_ the hardware in Ubuntu. I'd say that's Ubuntu 2, Vista 0.
By the way:
[http://feeds.downloadcenter.intel.com/rss/?p=2259&lang=eng](http://feeds.downloadcenter.intel.com/rss/?p=2259&lang=eng)

---

### Post by nonewmsgs on 2007-05-26
im sure dell.com has them.

---

### Post by meng on 2007-05-26
> **DJ Wings said:**
> Word. :lolflag: Ask for Vista help on UbuntuForums.org and you won't be living at **all** for much longer anyways. 
This should be amusing...:popcorn:
EDIT: We're not flaming you because you're a n00b... Hint: It has to do with the forum you're posting on.
Oh come on, just enjoy the irony that Ubuntu came to the rescue.

---

### Post by ugm6hr on 2007-05-26
> **nonewmsgs said:**
> im sure dell.com has them.

or possibly even HP website?

---

### Post by meng on 2007-05-26
Yeah or perhaps the link I already posted.

---

### Post by mojo123 on 2007-05-26
Thanks meng

---

### Post by drowner on 2007-05-26
LOL @ this thread.

Everyone's angry.

Just chill doodz. Chill.

---

### Post by meng on 2007-05-26
> **drowner said:**
> LOL @ this thread.

Everyone's angry.

Just chill doodz. Chill.

Sage advice.

---

### Post by drowner on 2007-05-26
> **meng said:**
> Sage advice.

Thanks, mate.

By the way, the My Computer icon has gone off the desktop, and i can't be bothered pressing start all the time.

How do I get it back?

---

### Post by meng on 2007-05-26
> **drowner said:**
> Thanks, mate.

By the way, the My Computer icon has gone off the desktop, and i can't be bothered pressing start all the time.

How do I get it back?
What, you're hijacking a thread now? :D
Honestly, I can't remember off the top of my head, and I don't have a Windows installation at home to check. BUT, have you tried dragging/right-clicking the Start Menu entry to add a shortcut to desktop? (Sigh. I know that works in GNOME, probably not in Windows.)

---

### Post by seshomaru samma on 2007-05-26
> **drowner said:**
> Thanks, mate.

By the way, the My Computer icon has gone off the desktop, and i can't be bothered pressing start all the time.

How do I get it back?



you mean in windows?
or is this just a joke?

press start
right click on 'my computer' and choose 'show on desktop'

---

### Post by drowner on 2007-05-26
> **seshomaru samma said:**
> you mean in windows?
or is this just a joke?

press start
right click on 'my computer' and choose 'show on desktop'

It was a joke

---

### Post by meng on 2007-05-26
> **drowner said:**
> It was a joke
Ah, good one ... I mean, I knew it was a joke, really I did. :redface:

---

