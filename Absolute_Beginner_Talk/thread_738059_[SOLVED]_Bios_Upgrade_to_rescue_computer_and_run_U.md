---
title: "[SOLVED] Bios Upgrade to rescue computer and run Ubuntu"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-28
I have a Acer TravelMate 230, Intel Celeron 2gig CPU 256mb ram, It uses PhoenixBios Setup Utility; System BIOS version RO1-A1D; VGA BIOS Version 2839; KBC Version 02.29.25 The internal HDD is FrieD and unreplaceable. The Bios only allows boot from cd rom, internal hdd and Removeable Devices - Legacy floppy drives. I already have a ext HDD with Ubuntu loaded on it including the grub. How do i upgrade my bios so that i can boot from external hdd and save the computer with LINUX!??????

---

### Post by Cypher on 2008-03-28
You already have the latest BIOS for that particular machine, so it doesn't look like they've added support for external HD. You might be out of luck and might want to consider an upgrade..

PS., Google can yield a wealth of information if you search first..;)

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **Cypher said:**
> You already have the latest BIOS for that particular machine, so it doesn't look like they've added support for external HD. You might be out of luck and might want to consider an upgrade..

PS., Google can yield a wealth of information if you search first..;)

Trust me I have done the google search - so the computer is a paperweight???

---

### Post by kesman on 2008-03-28
What do you mean "HD isn't replaceable"?
[http://www.eserviceinfo.com/download.php?fileid=10247](http://www.eserviceinfo.com/download.php?fileid=10247)
There you can download the service manual for your laptop and with it, you should be able to replace the HD, even with a bigger one.

---

### Post by philinux on 2008-03-28
Why is it not possible to replace the internal HD.

---

### Post by N1N31NCHN41L5 on 2008-03-28
The hard drive in it isnt available from manufacturer anymore - cant be found on ebay or any other used site.

---

### Post by Cypher on 2008-03-28
> **N1N31NCHN41L5 said:**
> Trust me I have done the google search - so the computer is a paperweight???
A quick Google search for "Acer TraveMale 230 Bios" yield this link ([http://www.acersupport.com/notebook/html/tm230_dl.html#BIOS](http://www.acersupport.com/notebook/html/tm230_dl.html#BIOS)) which shows the BIOS.

As the others have suggested if you can just physically replace the internal HDD then you should be back in business, but if somethings preventing that then it might be a paperweight..:)

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **Cypher said:**
> A quick Google search for "Acer TraveMale 230 Bios" yield this link ([http://www.acersupport.com/notebook/html/tm230_dl.html#BIOS](http://www.acersupport.com/notebook/html/tm230_dl.html#BIOS)) which shows the BIOS.

As the others have suggested if you can just physically replace the internal HDD then you should be back in business, but if somethings preventing that then it might be a paperweight..:)

Yes, i have found the bios for this system - i just dont know how to upgrade BIOS????

---

### Post by philinux on 2008-03-28
> **N1N31NCHN41L5 said:**
> The hard drive in it isnt available from manufacturer anymore - cant be found on ebay or any other used site.

This should not be a problem. Just get one similar.

---

### Post by N1N31NCHN41L5 on 2008-03-28
it does have usb ports but i dont have any floppys. can it be done without floppy

---

### Post by LowSky on 2008-03-28
you can boot from USB?

otherwise find a new internal find out what kind of connection it has and check a website like Newegg.com to get it to work.

---

### Post by Cypher on 2008-03-28
> **N1N31NCHN41L5 said:**
> it does have usb ports but i dont have any floppys. can it be done without floppy
Looks like the floppy is the way the BIOS updates wants to happen..the BIOS is old enough not to allow boot from USB.

I would think that any laptop HD would work in there..you don't need to worry too much about the manufacturer..

---

### Post by mips on 2008-03-28
1. I do not believe for one second that the hard drive cannot be replaced. It most likely uses a common 2.5" PATA drive which you can buy from places like newegg. I would recommend the Hitachi Travelstar brand for laptops.

2. If you can make a boot CD and use FreeDOS on it and at the same time load the required flash utilities and bios files onto it. Just google something like 'how to make bootable freedos cd'

I would honestly recommend just replacing the internal hard drive. There is nothing special about it and it can be bought off the shelf from most shops. If you need help with this I will assist you as it is REALLY easy to replace a hd on a laptop and does not require to much technical skills.

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **mips said:**
> 1. I do not believe for one second that the hard drive cannot be replaced. It most likely uses a common 2.5" PATA drive which you can buy from places like neweg. I would recommend the Hitachi Travelstar brand for laptops.

2. If you can make a boot CD and use FreeDOS on it and at the same time load the required flash utilities and bios files onto it. Just google something like 'how to make bootable freedos cd'

I would honestly recommend just replacing the internal hard drive. There is nothing special about it and it can be bought off the shelf from most shops. If you need help with this I will assist you as it is REALLY easy to replace a hd on a laptop and does not require to much technical skills.

The laptop just came from a friends who builds his own computers from scratch and he told me he did extensive research on the hdd and that it wasnt able to be replaced.

---

### Post by LowSky on 2008-03-28
Your friend is wrong, it can be replaced.

---

### Post by N1N31NCHN41L5 on 2008-03-28
i will check at Goodwill tomorrow. If any store here will have a HDD for it, it will be ther. They have the biggest selection of internal laptop hdd's on island. Where i bought a SATA HDD and the case to make it a ext hdd when it didnt work on the laptop we were trying to put (WIndows-yuckkk) on

---

### Post by mips on 2008-03-28
> **LowSky said:**
> Your friend is wrong, it can be replaced.

Have to agree 100%. Your friend is talking crap in all honesty. 

I just had a look at the service manual and it is a piece of cake to replace. The HD bracket is held in place with one screw to the laptop housing. Remove the screw, slide the bracket containing the HD out, remove HD from bracket, insert new HD into bracket, slide back into laptop and replace screw and voila you have a new HD installed.

So take it out yourself and post a picture of the actual hd, label & connectors and I will tell you exactly what to go and buy.

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **mips said:**
> Have to agree 100%. Your friend is talking crap in all honesty. 

I just had a look at the service manual and it is a piece of cake to replace. The HD bracket is held in place with one screw to the laptop housing. Remove the screw, slide the bracket containing the HD out, remove HD from bracket, insert new HD into bracket, slide back into laptop and replace screw and voila you have a new HD installed.

So take it out yourself and post a picture of the actual hd, label & connectors and I will tell you exactly what to go and buy.

would love to but i dont have any way to take a pic and post tonight. I will leave this post open and let you know tomorrow as soon as Goodwill opens. (Goodwill is a computer store in Okinawa)

---

### Post by mips on 2008-03-28
> **N1N31NCHN41L5 said:**
> would love to but i dont have any way to take a pic and post tonight. I will leave this post open and let you know tomorrow as soon as Goodwill opens. (Goodwill is a computer store in Okinawa)

No problem. Hope you come right. I would advise you to take the hd with you though. I would also advise you to replace it with a 7200rpm model and bigger size if you have a need for that. If you can get a Hitachi Travelstar as they are the best laptop drives available.

---

### Post by N1N31NCHN41L5 on 2008-03-28
thanks mips - i will post in about 15 hours

---

### Post by LowSky on 2008-03-28
goodwill is a computer store in Japan...thats funny... in the US Goodwill is Salvation Army type store

---

### Post by N1N31NCHN41L5 on 2008-03-28
i thought the same thing, thought thats what it was here to, till i was told by locals to go there for computer parts

---

### Post by mips on 2008-03-29
How did it go?

---

### Post by N1N31NCHN41L5 on 2008-03-29
> **mips said:**
> How did it go?

i tore a couple laptops apart for parts but nothing was transferable, i missed goodwoll by 5 minutes. So I will get it tomorrow morning as soon as i get up

---

### Post by mips on 2008-04-15
I was away for 2 weeks, what was the outcome?

---

