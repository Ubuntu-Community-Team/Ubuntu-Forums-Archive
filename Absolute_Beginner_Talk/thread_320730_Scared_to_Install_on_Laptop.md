---
title: "Scared to Install on Laptop"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-12-17
Hey everyone,

I have been waiting since July to install Ubuntu on my laptop.  I have a Gateway MX3414 and there has been non-working hardware on the Laptop testing page since I bought the laptop.  Do these pages get updated as things are fixed, or are all of these things still broken?

[https://wiki.ubuntu.com/LaptopTestingTeam/GatewayMX3414](https://wiki.ubuntu.com/LaptopTestingTeam/GatewayMX3414)

Also, I have an AMD Turion 64x2 processor.  What are the advantages/disadvantages to using the 64bit version of Ubuntu?

---

### Post by Sef on 2006-12-17
> have been waiting since July to install Ubuntu on my laptop. I have a Gateway MX3414 and there has been non-working hardware on the Laptop testing page since I bought the laptop. Do these pages get updated as things are fixed, or are all of these things still broken?


Download Dapper Drake Live CD and see if these problems occur.  If they occur on the Live CD, then likely they will occur upon install.

If Dapper fails, then download Edgy Eft Live CD.

> Also, I have an AMD Turion 64x2 processor. What are the advantages/disadvantages to using the 64bit version of Ubuntu?

Quite a few applications do not work on the 64bit version yet.   Some are just more of a pain to install.

---

### Post by xyz on 2006-12-17
Hi,

Well don't be tooo scared even though I can understand you could be! I have been, tooo!
Have you tried the the Live/Desktop CD?
Or how about dual booting...it's fairly easy to repartition your HD to make room for it?
Let me know...

---

### Post by kolinab on 2006-12-17
Sef,

I'm ignorant and curious - why do you recommend trying the Dapper CD first before the Edgy one?

K

---

### Post by brandoncolorado on 2006-12-17
Yeah, I am curious too.  Which one would work better?

I have tried the Live CD, but lots of the problems show up when I boot with the Live CD.  The problem is that I can't get online to look up some fixes because one of the problems is the wireless network.

---

### Post by macogw on 2006-12-17
From another comp, download ndiswrapper and the driver for your wireless card, and put them on your flash drive or a cd or a floppy if necessary.  Install the driver with ndiswrapper, then you can search online for fixes for other stuff.

If I knew how to reverse engineer, I'd help ya out with some of the stuff.  Any reverse engineers around here?

---

### Post by Zrock on 2006-12-17
Do like i did bite the bullit and just install it.... I downloaded and installed on my laptop and my desktop that i was having troubles with on windows 2000.... I would have actually never found out what the trouble was with my desktop if it had not been for the install... did a mem check and found out i had a bad memory slot..... havent regreted installing on eather system... Just findng things very diffrent and a challange to figure out..... but thats just because i have run a windows environment for 20 years without a change.... both systems are working great.....

---

### Post by xyz on 2006-12-17
The thing isn't "Which one would work better"...it's a matter of trying one and if it doesn't work too good, try and download the other.
There could be HW compatibility problems, for instance. I assume SEF means...try something and then, if you run into problems, come back here and post questions.

---

### Post by halitech on 2006-12-17
Edgy is more cutting edge, Dapper is more stable and fewer changes will be made in regards to the software.

---

### Post by mdsmedia on 2006-12-17
> **kolinab said:**
> Sef,

I'm ignorant and curious - why do you recommend trying the Dapper CD first before the Edgy one?

KNot wanting to read Sef's mind, but I'd suggest he's saying use the Dapper LiveCD first because it's the LTS (long term support) version, and if it's not successful the Edgy LiveCD might have updates that fix any problems.

Then you can either install Dapper, if it works, or Edgy, if Dapper doesn't work but Edgy does.

---

### Post by macogw on 2006-12-17
Hey, here's an idea.  It might not help in the short run, but it can in the long run.  Get the specifics of the hardware (models and stuff).  Try Googling for them with the word Linux.  See if any drivers or anything show up.  If they do, go to Launchpad (launchpad.net) and mark as a suggestion that that hardware be supported in Feisty and include a link to the driver.  If there's nothing, still go to Launchpad and request it.  Maybe someone will be willing to get it working for the next release of Ubuntu.

---

### Post by brandoncolorado on 2006-12-18
Hi I have tried to fix a few of the problems and now I am frustrated.

1) I installed NDiswrapper and the graphical interface for it.  I then tried to install 3 different versions of the Windows driver using the graphical interface for my Realtek 8185.  When I choose the .inf file, nothing happens.  Nothing shows up under installed drivers.

2) I tried to fix my resolution issue by installing the latest Nvidia drivers, now when I boot into Ubuntu, my screen is just black.

](*,) ](*,) ](*,)

---

