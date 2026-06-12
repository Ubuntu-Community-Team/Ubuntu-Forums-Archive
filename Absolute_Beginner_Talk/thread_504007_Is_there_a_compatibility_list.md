---
title: "Is there a compatibility list?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Nervouswreck on 2007-07-18
Is there an up-to-date list of all hardware and peripherals supported by the various versions of Ubuntu?
A good one would probably show which ones work with the pre-installed drivers and which require fixes and where to get said fixes. Does anyone know of such a list?

I am particularly interested in Maxtor Firewire400 drives and Samsung ML215 printers. Even if there's no list can someone give information about those 2 peripharals?

Thanks a lot.

---

### Post by wolfen69 on 2007-07-18
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)   but it seems to be down right now. check later.

---

### Post by oilchangeguy on 2007-07-18
> **Nervouswreck said:**
> Is there an up-to-date list of all hardware and peripherals supported by the various versions of Ubuntu?
A good one would probably show which ones work with the pre-installed drivers and which require fixes and where to get said fixes. Does anyone know of such a list?

I am particularly interested in Maxtor Firewire400 drives and Samsung ML215 printers. Even if there's no list can someone give information about those 2 peripharals?

Thanks a lot.

the best way to find out what works, and what doesn't on your computer. is to run the live cd. make note of any problems, and decide if you want to install ubuntu, and search the forum for previous threads on problems like yours.

---

### Post by Nervouswreck on 2007-07-19
I tried the wiki list, my printer isn't listed, and neither are any external drives. Does that mean they all wirk or theat they were omitted? Also, what does "works sometimes" mean?

---

### Post by DBStevens on 2007-07-19
....what does "works sometimes" mean? ....

Well sometimes when a printer is involved it might only print in b&w even though it is a color printer or it may only print text and not graphics. 

Also in the case of printers I'd consult the CUPS list of compatable printers since it is rather extensive and CUPS is availible on Ubuntu.   

Since the kernel and its drivers are in play it should really make no difference which of the Ubuntu flavors you are contemplating.

What would make a difference is which version of the kernel you are running.

I took a look on the Samsung site and can find a ML-2150 printer but not a ML-215 printer the 2150 printer has availible CUPS drivers directly from Samsung.

---

### Post by John.Michael.Kane on 2007-07-19
Looking over the Maxtor Firewire400 specifications it's dual interface: FireWire 400 and USB 2.0. In any case this device working though the firewire port would be based on the Chipset used to on your motherboard.

Regarding the Samsung ML215 printer. Looking over the info at openprinting.org shows the ML-200, and ML-210 as working perfectly. I'm not sure how much has changed from these two, and the ML215. 


With that your best bet would be to do as one of the posters said, and load up the livecd, and test these peripherals. 

Also it would help if we knew what your hard specs are eg: motherboard model ect.

---

### Post by laidback on 2007-07-19
I have a Samsung ML1610 which until recently didn't appear by default in the Install new printer list, I'm using 7.04 now where it does. So instead I used the closest I could get, ML1510 or 1710 which appeared to work for my needs. Before that I was using Mandriva and managed to install the Samsung driver myself (phew!). No such luck with Ubuntu 6.06 so I gave up and continued as above. As mentioned by SD-Plissken I too can see the ML 200 and 210 versions so give them a try, you may loose some of the functions the 215 has but then maybe you don't need them anyway. Don't be afraid, just try it.

---

### Post by misfitpierce on 2007-07-19
Yep liveCD is no install and can show what mainly works... Whatever does not auto work like wireless look up the card in your computer and find information on it... All broadcoms work and usually just need to run firmware cutter etc etc like that.

---

### Post by ubanchaos on 2007-07-19
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Nervouswreck on 2007-07-23
Thanks everybody. The project got delayed because someone still needs the machine (it's the same one from my thread on the G4 cube) but believe me, you'll be hearing if I have problems :lolflag:

---

