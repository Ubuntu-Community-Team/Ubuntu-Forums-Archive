---
title: "Few Question"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by rtr86 on 2007-09-10
Hi all,

Ive been using Ubuntu for a few days and with thanks to you guys I am setup with my wireless internet card.

I still am very new to the platform though and have a few questions :)

Do I need to install Motherboard/chipset and processor drivers? (I am running Ubuntu on my second PC - XP2600)

I have not installed my Nvidia FX5200 256m Drivers. There seem to be quite a few ways to install them (manually and with Edge(sp?) software), any benefits with a manual install?

My linux install seems to be running a little slower compared to a windows install, is there anything else I should be doing to optimize my install? 

Any help appreciated!

Thanks

---

### Post by loell on 2007-09-10
just install the linux nvidia drivers, and you'll notice a speed difference

to install , got to **systems menu** -->  **administration** --> **restricted drivers manager**

input your password , then check to enable the driver, then restart.

---

### Post by mariarchi on 2007-09-10
Where do you find that in KDE?

---

### Post by hyper_ch on 2007-09-10
> **rtr86 said:**
> My linux install seems to be running a little slower compared to a windows install, is there anything else I should be doing to optimize my install? 
Install the same amount of apps on windows that you have with a native ubuntu or kubuntu and check again the speed ;)

---

### Post by rtr86 on 2007-09-10
Thanks for replys,

> **loell said:**
> just install the linux nvidia drivers, and you'll notice a speed difference

to install , got to **systems menu** -->  **administration** --> **restricted drivers manager**

input your password , then check to enable the driver, then restart.

Will do that. Why do so many people maually install the driver though if you can just unrestrict it? Is it possible to update to latest driver after selecting unrestricted and doing an software update?


> **hyper_ch said:**
> Install the same amount of apps on windows that you have with a native ubuntu or kubuntu and check again the speed ;)

Do you mean I need to install motherboard, chipst and processor drivers etc?

Thanks

---

### Post by loell on 2007-09-10
> **hyper_ch said:**
> Install the same amount of apps on windows that you have with a native ubuntu or kubuntu and check again the speed ;)

uhmm, how does this help?

---

### Post by loell on 2007-09-10
> **rtr86 said:**
> 


Do you mean I need to install motherboard, chipst and processor drivers etc?



depends on how you want to optimize your system,

you can optimize it by upgrading your hardware specs 

additionally you can optimize your system, by tweaking the desktop environment, and the kernel which is fairly advance for a beginner.

---

### Post by hyper_ch on 2007-09-10
> I have not installed my Nvidia FX5200 256m Drivers. There seem to be quite a few ways to install them (manually and with Edge(sp?) software), any benefits with a manual install?

Do you have Ubuntu Edgy Eft (6.10) installed?

loell: It helps in that matter, that the speed of windows xp varies very much depending on how software is installed ;)

Another speed improvement is to use an alternate Desktop Environment and not KDE.

---

### Post by aquavitae on 2007-09-10
> **rtr86 said:**
> 
Do I need to install Motherboard/chipset and processor drivers? (I am running Ubuntu on my second PC - XP2600)No. They are all built into the kernel.  Installing them manually (i.e. compiling the kernel manually is quite compilcated and produces such a marginal speed impovement that its not worth it. (I've tried it ;) )
> 
I have not installed my Nvidia FX5200 256m Drivers. There seem to be quite a few ways to install them (manually and with Edge(sp?) software), any benefits with a manual install?The other posts expain about the restricted drivers.  As far as I'm concerned, this is enough.  You can install manually if you want, but as with the kernel its probably more trouble than its worth.
> 
My linux install seems to be running a little slower compared to a windows install, is there anything else I should be doing to optimize my install? Are you using compiz (o.e. desktop effects)?  If you're using this without installing the graphics drivers, that would be why its slower.

---

