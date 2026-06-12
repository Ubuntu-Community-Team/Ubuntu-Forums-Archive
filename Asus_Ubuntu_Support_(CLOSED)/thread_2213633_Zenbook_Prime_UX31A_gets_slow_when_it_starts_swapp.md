---
title: "Zenbook Prime UX31A gets slow when it starts swapping"
date: 2014-03-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Andreas_Auer on 2014-03-27
Hello,

I have a Asus Zenbook Prime UX31A and I'm using it with Linux. The problem I have is that the notebook gets very slow (almost freezing) sometimes. I'm not totally sure, but it seems it is when it starts swapping. If I check the load average it can be >100. IMHO this is horrible.
It happens when I have a number of tabs open in Chromium and/or when I edit some images with Gimp. Has anybody else seen this behavior? Could it be a problem with the RAM or with the SSD? I already checked the SSD with smartmontools. But this looks ok for me.

I hope someone could help.

Thanks and best regards,
Andreas

---

### Post by Double.J on 2014-04-08
Hi there! Welcome to the forums!

It does sound strange. However if RAM becomes full AND swap begins to run out of space, this would be expected behaviour as the computer must continuously seek the disk for what it wants and swap out the ram pages into a virtually full swap partition to be able to copy into the ram. 

Looks like your machine has 4gb RAM. It is entirely possible to use that up with advanced/intensive gimp use however, if this is happening only using a web browser, it's probably get a good look at what's using all these resources.

try installing htop and running it from a terminal?

Jj

---

