---
title: "instal problem..help please"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by huziiik on 2007-11-14
I m tottaly new to forum,so sorry if i do spam or how you call it,but i have a problem wth installing ubuntu 7.10 on my laptopnd. I installed it on my old PC with no problems and i was really interested in it.I have a problem with starting live cd.Cause when i choose start or install ubuntu from boot menu,it begins to boot but after the process comes to loading restricted drivers,my cd rom stops working and my PC is freezed.then starts to write som error message with input output-something like: buffer I/O error on device hdc... i don´t know what to do.so please help me if you can.My laptop is MSI processor-amd sempron 3500+, graphic card-Nvidia geforce go 6100, 1,5 Gb ram, and some LG dvd ram.thanx for help so much.

---

### Post by zabien1970 on 2007-11-14
If you give some of the specs of your computer it may help

oops, my bad, I see you did

---

### Post by fuente on 2007-11-14
i am only 2 wks old in the linux world, but try that. try installing ubuntu 5. it should clean up ur hard drive. if it doesnt install completely no prob just remove the linux 5 cd and put in the 7.10 and install it again.

---

### Post by huziiik on 2007-11-14
I tried to instal 6.06 version but it did the same.but thanx,i ll try it

---

### Post by huziiik on 2007-11-15
I tried,and it did the same.:( some other idea???? doesn t somebody know what does it mean install with driver update cd(in boot menu).could it help me somehow???

---

### Post by Inxsible on 2007-11-15
you might want to install using the alternate CD, which is a text based installation. Once the install is complete, you can then configure your graphics card etc.

---

### Post by oneadvent on 2007-11-15
So you tried 2 different CDs? It sounds like your CD or CD Player isn't working right. 

Have you used Check Sum on the disk? Or run the memory test that comes on it.

I know I have downloaded bad copys of Ubuntu before.

---

### Post by huziiik on 2007-11-18
> **Inxsible said:**
> you might want to install using the alternate CD, which is a text based installation. Once the install is complete, you can then configure your graphics card etc.it 
Thanx for this tip. I installed it with alternate CD but now I don´t know again what´s wrong because on my home PC was Ubuntu in desktop mode after starting,but now I have only command line and I´d like tu torn to desktop mode bur don´t know how.can somebody help me?? And I have one more question. By installing i had one error specifically in choosing and installing software or something like that??but I skipped that and ubuntu installed.Is it a big problem???

---

### Post by overdrank on 2007-11-18
> **huziiik said:**
> it 
Thanx for this tip. I installed it with alternate CD but now I don´t know again what´s wrong because on my home PC was Ubuntu in desktop mode after starting,but now I have only command line and I´d like tu torn to desktop mode bur don´t know how.can somebody help me?? And I have one more question. By installing i had one error specifically in choosing and installing software or something like that??but I skipped that and ubuntu installed.Is it a big problem???

HI and yes that could cause problems. Did you check the cd for errors and check sum as previously suggested? It is probably the graphics card that is causing the issue, have you tried to reconfigure you xorg from the command line, 
he command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by tyggna1 on 2007-11-18
I had that same problem when installing linux on my server.   I thought it was just additionally complications coming from the fact that it was an OEM hard drive.   Turns out, that after fiddling with the hard drive settings in the BIOS I was able to boot to the live CD.  

Here's my story:   I bought a computer for $40 with 128MB of RAM and no hard drive.  It also doesn't have a CD-drive to this day.   I copied the live CD onto a jump drive and booted from that (not easy).   When I tried, I'd keep getting a buffer I/O error on my hard drive, and it would take about 20 minutes to boot before it failed.
I thought my hard drive was a piece of junk.   After upgrading the RAM to 1Gig, It would boot from my live jump drive whenever the hard drive was plugged in.   Apparently--that hard drive was setting itself as a slave, when it needed to be set as a master.

Also, I was using an IDE hard drive (the computer thought it was SATA for a while), and I had to turn off the UDMA in BIOS for it to work.  After doing those two things, it worked like a charm.

Hope this helps

---

### Post by huziiik on 2007-11-18
thanx all for help.it s done :mrgreen:

---

### Post by overdrank on 2007-11-18
> **huziiik said:**
> thanx all for help.it s done :mrgreen:

Great and could you please mark the tread as solved under thread tools. :)

---

