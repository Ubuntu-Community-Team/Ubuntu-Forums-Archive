---
title: "Help with install please"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by ForsakenSoul on 2007-03-12
i`ve just tried to install ubuntu 6.10 with the alternative cd because the live one won`t start ... it gives a tty: process turned off or something (i`ve already reported it as a bug), I run the install and the stupid thing doesn`t want to find my cd-rom and i don`t have a driver cd :( help please :(

thank you in advance

---

### Post by bodhi.zazen on 2007-03-12
Moving to Absolute Beginner Talk

I think you will get more help there ....

---

### Post by SurR3AL on 2007-03-12
have u set ur bios to boot from cd?

---

### Post by ForsakenSoul on 2007-03-12
> **SurR3AL said:**
> have u set ur bios to boot from cd?

yeah of course:) the ubuntu alternative cd starts just fine ... but when i go to step 3 - mounting the cd-rom ... it doens`t find it. and i don`t have a cd with the cd-rom driver :(

---

### Post by SurR3AL on 2007-03-12
ouch. then i dont know mate. wait for some1 more experienced :)

---

### Post by Bachstelze on 2007-03-12
Maybe your IDE chipset is new and not supported by Edgy's 2.6.17 kernel. Try a Feisty CD and see it it works.

---

### Post by ForsakenSoul on 2007-03-12
> **HymnToLife said:**
> Maybe your IDE chipset is new and not supported by Edgy's 2.6.17 kernel. Try a Feisty CD and see it it works.

I know this will sound very stupid but what the heck .... what is Feisty CD and where do I get it from ?

by the way i forgot to mentune that i am installing my ubuntu on a empty hard drive which is attached to the line that attaches the cd and the ... other parts of the pc (don`t know how it is called in english :D )

---

### Post by Bachstelze on 2007-03-12
Feisty is the codename for the next Ubuntu release. It is still in testing phase - to be released mid-April - but if that's the only option you have...

---

### Post by ForsakenSoul on 2007-03-12
> **HymnToLife said:**
> Feisty is the codename for the next Ubuntu release. It is still in testing phase - to be released mid-April - but if that's the only option you have...

Would you please give me a link to one Feisty cd :D

---

### Post by SurR3AL on 2007-03-12
check [here]("http://cdimage.ubuntu.com/daily/current/") :)

EDIT: sorry...that link is for the daily build. check [here]("http://cdimage.ubuntu.com/releases/feisty/herd-5/") for the fiesty herd-5 release :) that's your best bet

---

### Post by ForsakenSoul on 2007-03-12
thank you i hope it works ... i`ll post the results tommorow

---

### Post by SurR3AL on 2007-03-12
all the best! :D
cheers mate!

---

### Post by ForsakenSoul on 2007-03-13
Damn it .... the stupid thing done it again ... the alternative cd couldn`t find my cd-rom .... i`ll try to find some drivers for my cd on the net for linux ... but i might as well star looking for another linux system :(:(

---

### Post by SurR3AL on 2007-03-13
are your cdrom cables very old?

---

### Post by ForsakenSoul on 2007-03-13
well not that old :) ... i`ve hooked it up witn some older cables because i couldn`t find another way to install another hard drive ... because i`m planning to install a dualboot system ... why is that a problem ?

---

### Post by Kateikyoushi on 2007-03-13
It depends on the chipset the drivers are in the kernel so other distrs might not support it either. What is your motherboard ?

Boot from the cd then press F6 edit the boot option and edd this to the end of the line, it worked for people whose cd was not recognised.

```
pci=nomsi
```

---

### Post by ForsakenSoul on 2007-03-13
> **Kateikyoushi said:**
> It depends on the chipset the drivers are in the kernel so other distrs might not support it either. What is your motherboard ?

Boot from the cd then press F6 edit the boot option and edd this to the end of the line, it worked for people whose cd was not recognised.

```
pci=nomsi
```

:lolflag: well i don`t know actually ... but on my driver cd it is written

Installer Driver CD for the Intel Desktop Boards DQ965GF, DQ965CO and DQ65WC Executive Series.

I suppose it`s one of those .... so can you tell where can I find out which one is it :D 
Thank god it`s absolute begginer talk because I was going to feel very stupid (not that i am not feeling stupid in the moment :D)

---

### Post by Kateikyoushi on 2007-03-13
I check it but, try what I recommended in the previous post.

---

### Post by ForsakenSoul on 2007-03-13
> **Kateikyoushi said:**
> I check it but, try what I recommended in the previous post.

unfortunately it didn`t word .. I was supposed to add the 
pci=nomsi code with a space after the -- or exactly after them ? and i`m talking about the alternate install cd because the live won`t start the system ... tty problem blqh :( i`ve posted it as a bug and so did others i see :(

---

### Post by Kateikyoushi on 2007-03-13
Seems there is a way to install but probably not what you will prefer. [LINK]("http://ubuntuforums.org/showthread.php?t=317003&highlight=DQ965GF")

There are entries in launchpad that the installer hangs during partitioning which proves someone was able to boot the disc, but they didn't get far either, that problem was fixed so you have a chance that feisty will work.

---

### Post by ForsakenSoul on 2007-03-13
> **Kateikyoushi said:**
> Seems there is a way to install but probably not what you will prefer. [LINK]("http://ubuntuforums.org/showthread.php?t=317003&highlight=DQ965GF")

There are entries in launchpad that the installer hangs during partitioning which proves someone was able to boot the disc, but they didn't get far either, that problem was fixed so you have a chance that feisty will work.

I don`t think this will work for me ... because i`m installing it on an empty hard drive ... and the only usb device which has some space on it is my mp3 player? will it work .. and how can i make it boot before the empty hard ?

---

### Post by Kateikyoushi on 2007-03-14
You should boot from the usb drive.
Anyway I saw someone said feisty worked so give that a try first.

---

### Post by Abhi Kalyan on 2007-03-16
Dear ForsakenSoul,
Dapper drake should work,
Please confirm the following
1. Processor
2. Mother board
3. CDROM - Make
4. Number of hard disks and types of each
5. Whether you can see the CDROM in the bios
6. How you connect the peripherals, The cables
7. Are the HDD and the CDROM connected using the same cable or are you using seperat ecables.?

- Please forgive if you see any typo errors, or spelling mistakes , happens due to my not knowing typing very well.-
hoping to see you through this whole issue.
All the best

---

### Post by ForsakenSoul on 2007-03-20
> Dear ForsakenSoul,
Dapper drake should work,
Please confirm the following
1. Processor
2. Mother board
3. CDROM - Make
4. Number of hard disks and types of each
5. Whether you can see the CDROM in the bios
6. How you connect the peripherals, The cables
7. Are the HDD and the CDROM connected using the same cable or are you using seperat ecables.?

- Please forgive if you see any typo errors, or spelling mistakes , happens due to my not knowing typing very well.-
hoping to see you through this whole issue.
All the best
Well my processor is Pentium 4 with dual core the Mother Board is a Intel Desktop Board DQ965GF, two hard disks ... don`t know the types but they are different :D i thing one is IDE ... yes i can see the cd in the bios ... i connected the new hard with the cd-rom with one cable
by the way the first distro i tried was drapper :) and i`m not the only one with this problem on this mother board :)
thank you :)

---

