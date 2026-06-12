---
title: "Problem with installation"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by tkafik on 2007-03-09
I have a serious problem with the installation.
When I installed the ubuntu 6.10 my windows was destroyed. My computer continued to up but the network card didnt work and the cd rom too.
I think that the reason to this is that when i finished to install the ubuntu i forgot to eject the disc and I press enter when the disc was inside.
Perhaps that this the reason? if yes I will install the ubuntu again and I will eject the disc but if no what i need to do with the ubuntu? mybe download another version or 64 bit?

thx.

---

### Post by PartisanEntity on 2007-03-09
If your windows was destroyed, did you try booting from the windows CD and choosing the repair function?

---

### Post by Aberrix on 2007-03-09
> **tkafik said:**
> 
When I installed the ubuntu 6.10 my windows was destroyed..

did you format the whole disk instead of partitioning?

> **tkafik said:**
> My computer continued to up but the network card didnt work and the cd rom too.

what happened during the network configuration part of your installation? any problems there? what did you choose?

---

### Post by chewearn on 2007-03-09
> **tkafik said:**
> I have a serious problem with the installation.
When I installed the ubuntu 6.10 my windows was destroyed. My computer continued to up but the network card didnt work and the cd rom too.

Open a terminal, type in:
```
ifconfig
```

If you see eth0, then your network card should be ok.

Put in a CD or DVD into your drive, did you see a disc icon on the desktop?

> 
I think that the reason to this is that when i finished to install the ubuntu i forgot to eject the disc and I press enter when the disc was inside.  
Perhaps that this the reason?

If you forgot to remove the CD, and then did not change the boot order in your BIOS, you will only boot back into the LiveCD.  It will not mess up your installation.

>  if yes I will install the ubuntu again and I will eject the disc but if no what i need to do with the ubuntu? mybe download another version or 64 bit?


There is probably no need for a re-installation.

---

### Post by tkafik on 2007-03-09
well, I format my pratation of the windows and now all work good.
So you say that i can to install again, eject the cd and now the ubuntu will work?

---

### Post by chewearn on 2007-03-10
> **tkafik said:**
> well, I format my pratation of the windows and now all work good.
So you say that i can to install again, eject the cd and now the ubuntu will work?

I suggest you boot up the LiveCD, check to make sure that your network card and CD-ROM is working.  If there is no problem, then you should be good to go.  If not, you have to decide if you want to install anyway (which mean you might need to fix those hardware later).

---

