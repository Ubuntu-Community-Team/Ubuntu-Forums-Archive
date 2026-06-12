---
title: "Headache galore with my new G3 iMacs. PLEASE HELP."
date: 2008-01-20
forum: Apple PPC Users
---

### Post by TRSixxx on 2008-01-20
I'm to the point where I almost want to offer someone money to do this for me.


Okay, so I picked up two iMacs the other day, both are the 350mhz processors with the slot loading CD drives. Really good shape.

Anyway, one has Mac OS 9.2.2 on it and seems to work fine, but I have trouble navigating it its a real PITA. The other one doesn't have an OS on it, it just flashes a mac sign or something at startup.

So I thought, why not throw ubuntu on both of them and make them internet machines...

Here is where the problems started.


As you can see I didn't get too far. I found a website giving me a step by step way to install, but I'm either an idiot or these computers just REALLY don't want ubuntu on them.

Does there have to be an OS present to install?

These both have 256 megs of ram, is that good enough to install?

I want to just completely wipe everything from these and start fresh, whatever it takes.


When I put the PPC install disc in, NOTHING happens.

Maybe I am burning the disc wrong?


I have a MacBook with Leopard. I'm pretty sure I burned the iso properly though.


Please help me out, I'll paypal you for your time. 10 bucks to the lad who figures it out for me.
:lolflag:


Thank you!!!!

---

### Post by oswaldkelso on 2008-01-20
lots of info here 

[http://ubuntuforums.org/showthread.php?t=405934&highlight=imac+install](http://ubuntuforums.org/showthread.php?t=405934&highlight=imac+install)

dont use gusty use fiesty and alt install cd

see my how to for tips on a  lighter and faster debian install which may be better for your low end machines see link at the bottom of the page.

after your install send the $10 here :)

[https://www.fsf.org/associate/support_freedom](https://www.fsf.org/associate/support_freedom)

---

### Post by stream303 on 2008-01-20
With low memory system, I'd definitely recommend the Alternate text-based install rather than the live-cd, and Xubuntu instead of Ubuntu or Kubuntu, assuming you want some desktop-type machines.

Since both machines are identical, I'd be tempted to just max out the ram to 512mb in one box, and get it upand runnng first, and order up some more inexpensive memory in the meantime if successful.

When all is said and done, memory will be your best friend on these boxes.

Maybe some of this might help:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Be sure to read the PPC Faqs and Known Problems regarding the G3 installations.

Sounds like a great project and glad to see that the machines aren't going to the dump and being put to use instead.

---

### Post by GVCarroll on 2008-01-20
> **stream303 said:**
> 
With low memory system, I'd definitely recommend the Alternate text-based install rather than the live-cd, and Xubuntu instead of Ubuntu or Kubuntu, assuming you want some desktop-type machines.


Definitely consider going with Xubuntu, it has less fancy user interface candy but it runs well on low end machines. I'm using Ubuntu 7.04 (Feisty Fawn) on a 500Mhz PPC iBook, and it runs well, but I've tried Xubuntu and it's noticeably snappier. Especially if you're going to use the machines for low-end internet and general use, you don't need the extra eye candy (Xubuntu still has themes and such of course).

And definitely use the Alternate tex-based installer rather than the Live installer.It guides you the same way as the Live install, it's just text-based and you use Tab and Enter to highlight and select options, it's pretty easy.

---

### Post by tgs1952 on 2008-01-20
I too recommend xubuntu. Also, the issue is memory.I successfully installed xubuntu on the same model imac. But memory was a problem after the install. I had only 192mg and the machine was hopelessly slow.

Fortunately, the memory for imacs is cheap now - something like $50 per 512mg. I would recommend maxing out on the memory if you want usable machines.

---

### Post by Midwest-Linux on 2008-01-21
> **tgs1952 said:**
> I too recommend xubuntu. Also, the issue is memory.I successfully installed xubuntu on the same model imac. But memory was a problem after the install. I had only 192mg and the machine was hopelessly slow.

Fortunately, the memory for imacs is cheap now - something like $50 per 512mg. I would recommend maxing out on the memory if you want usable machines.

 Just be aware that that the non slot loaders I-Macs use SO-Dimms PC 100's, which is the same as a Windows laptop PC 100 memory. To add or replace RAM in the non slot loaders you must physically take apart the machine to get at the motherboard....and that is the easy part.

While the slot loaders I-Macs  use standard PC 100 SDRAM non ECC Ram, it is far easier to add/replace these at the bottom of the machine by just lifting a small hatch. 

 I tried two 512 MB Ram sticks in the slot loader I- Mac, I checked the specs after installing Ubuntu and all I got was 500 MB RAM. So just be aware that buying 512 MB Ram sticks might be too much for the machine. I believe two 256 MB Ram sticks would just work fine for the slot loader I-Macs, unless you have a newer version. 

(In some cases adding too much Ram can also be just as bad as too little RAM. Some older machines -esp PCs- might only have 256 MB total capability. So in those cases 512 MB ram sticks would not work. But feel free to experiment however....)

 I have always used the alternate text based installer for the Mac Machines ( I have three...two I-Macs and One B & W G3) 

One other tip, connect the machine up to the internet before you install Ubuntu so the OS can configure DHCP automatically.

---

