---
title: "A few questions..."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Quisler on 2007-08-23
Hello, first thing is that this looks awesome and I would love to use this, but first I want see what I need to do to get this running...

Well first thing is, I just got a new laptop. The specs are;

Sager 5790
Intel Core(2) Duo @2.00 GHz
2 GB of RAM
160 GB HDD
Geforce Go 9750 GTX
XP Pro SP2


I looked in the list of compatible laptops and I saw a few Sager in there, but nothing as new as this. I wouldn't think there would be any compatibilities problems with the drivers since most of the stuff is commonly used. Only thing would be the new graphics card. 

Next thing is I already have a lot of stuff installed and there is only one partition so can't exactly erase all of it. I do have the ability to back up my data though. I saw tidbits here and there that you can just make a partition with what is left of your HDD without reformatting the whole drive. If that IS a possibility I would like to take that road. 

Dual booting. I was looking around to see if you can dual boot this and XP. From what I read it sounds like its better to have the 2 OS' on different HDDs. If I can, I would just like to do what I mentioned above. 

This OS looks so cool and promising and I would really like to try it out and mess around with it. Just that I don't want to mess up my new lappy by me being stupid with something I should have thought through lol. 

Thank you for your help!

---

### Post by amazingtaters on 2007-08-23
Hokay so here's my thoughts

1. Your specs are great, you shouldn't have any issues, except maybe with wireless but that is common and easily dealt with.

2. Before installing Ubuntu defrag and shrink your XP partiton. If the space is already freed up things will go much easier and you will have no worries about damaging your XP install. HOWEVER: DO BACK UP YOUR DATA. YOU NEVER KNOW WHAT COULD HAPPEN. BETTER SAFE THAN SORRY.

---

### Post by Quisler on 2007-08-23
Ok, incoming noob question of the day. I understand about defragging the drive, but shrinking it? As in using a program to shrink the partition, or with Windows itself? Can you tell me how to do that please? Thanks.

---

### Post by AceofSpades19 on 2007-08-23
boot up the ubuntu livecd, go to system>administration and go to the gnome parition manager and click on the windows parition and then click on the move/resize button

---

### Post by Hobo Joe on 2007-08-23
> **Quisler said:**
> Ok, incoming noob question of the day. I understand about defragging the drive, but shrinking it? As in using a program to shrink the partition, or with Windows itself? Can you tell me how to do that please? Thanks.

The live CD has an app for that.

And as for it being better to have two drives... It's not true, it's actually harder to do it with two drives than it is with one.

---

### Post by Quisler on 2007-08-23
Sweet, thanks a bunch! I'll see how it all goes when I can get all my data backed up. Thanks again!

---

### Post by erfahren on 2007-08-23
you can shrink your Windows partition using the Ubuntu aternate CD (text-based) installer (actually the Live or "Desktop" CD installer will do it as well, but I personally think the alternate one is easier). 

See: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Its a good idea to run the Windows Check Disk (scan disk for errors) two or three times before defragging (it doesn't always fix all the errors the first time thru in my experience). [This standalone freeware defragger](http://www.kessels.com/JkDefrag/) works better than the Windows one. It will actually move everything to the beginning of the partition better (just close as many running processes as you can before running it - antivirus, etc.). 

Note: [this page](http://www.housing.hawaii.edu/resources/support/chkdsk.htm) shows how to view the check disk log in the Event Viewer.

---

