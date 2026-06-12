---
title: "Ok i am having a lot of problems"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by alwaysconfused on 2008-01-02
Ok i have this operating system on one of my old computers but the problem is the only thing i can do is play those little games it comes with for some reason no cd rom will work on it except for my external usb cd rom and that will only play music cds its wierd?? but i have tried internal cd roms that i know for a fact work but it dont and i tried changing the slave and master switches to all of them and it did nothing  so i just got fed up with it and am trying to reinstall windows xp but i have the windows cd that came with the computer but the cd rom dont work i cant boot from an external cd rom for some reason???? it is getting very frustrating and my jump drive and external hard drives will not work in the usb slots and i cant get online with it cuz the wireless card dont work... I am so confused it is realy getting to me could it be my motherboard that makes the internal cd roms not work?? or do i need to get some drivers or what when i go to bios it says cd rom not installed even when it is plugged in????????? i know what i am doing when plugging it in the computer i am on now i built myself so im pretty sure its plugged in all the way im just really confused at to why it is doing this any advise would really help me so much thanks for the help

---

### Post by Furat on 2008-01-02
OK with  what CD drive you installed the Ubuntu ??

---

### Post by thelatinist on 2008-01-02
Try going into your BIOS settings and checking to see if your CD-ROM drives are being detected.  If they are not, then it is probably a hardware problem (anything from a faulty cable to a bad IDE controller).  If they are detected there, then post back with the results of:

```
sudo cat /etc/fstab
```

---

### Post by Crafty Kisses on 2008-01-02
> **thelatinist said:**
> Try going into your BIOS settings and checking to see if your CD-ROM drives are being detected.  If they are not, then it is probably a hardware problem (anything from a faulty cable to a bad IDE controller).  If they are detected there, then post back with the results of:

```
sudo cat /etc/fstab
```

That'd be a good solution.

---

### Post by alwaysconfused on 2008-01-02
no it says no cdrom installed it has power to it it opens and runs the cd and i tried three different ones of those skinny cables with three different cd roms so maybe could it be my motherboard is broke somehow?

---

### Post by alwaysconfused on 2008-01-02
oh and i used jump drive to instal ubuntu but now jump drive wont work its wierd

---

### Post by thelatinist on 2008-01-02
Sounds like a hardware problem.  If you've tried several IDE cables and several (working) CD-Rom drives, then it is probably a problem with the IDE controller. In that case, it's time to replace your motherboard.

---

### Post by alwaysconfused on 2008-01-02
its not worth replacing ha ha i just got bored and wanted to mess around with ubuntu on it its like a 5 year old dell that makes me mad that i cant do anything with it now i dont know how a motherboard just breaks????

---

