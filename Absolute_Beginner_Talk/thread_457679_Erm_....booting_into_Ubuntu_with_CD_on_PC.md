---
title: "Erm ....booting into Ubuntu with CD on PC"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by TeuchterNYC on 2007-05-28
I'm completely new to Ubuntu. I have downloaded 7.04 Desktop and then unloaded the iso before burning it to a CD. When I try to boot with this CD, I'm told the CD is not bootable. Which file should I have that the computer will look to boot from. I don't see a .com or .sys. There is start.exe and start.ini. Thanks.

---

### Post by taurus on 2007-05-28
You are not supposed to unpack it before you burn it.  You should just burn the .iso file and as image file with your burner app.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by TeuchterNYC on 2007-05-28
Thanks....so I can boot from an iso?

---

### Post by taurus on 2007-05-28
> **TeuchterNYC said:**
> Thanks....so I can boot from an iso?

You need to burn it to a CD first but you _must_ burn it as an image file.  Don't just copy it from your harddrive over to a CD because that will not boot.

---

### Post by TeuchterNYC on 2007-05-28
I'm not understanding something that is probably pretty basic and obvious. I don't think I understand what is meant by an burning an image file. I have downloaded ubuntu-7.04-desktop-i386.iso on to my desktop (on a mac actually). I can view the actual files in a finder window and first time round burned these files onto a CD (so you could actuallly read the individual files contained on the iso on the CD) which wouldn't boot (on my PC). I then burned the ubuntu-7.04-desktop-i386.iso directly onto a disk, which not surprizingly did not boot (on my PC). I'm not clear as to exactly what the CD should contain and how to get it there....

---

### Post by taurus on 2007-05-28
Please look over the two links in my previous post on how to burn it to a CD.

---

### Post by TeuchterNYC on 2007-05-29
The links did the trick thanks (missed them earlier)- I'm up and running. Still don't understand the technical difference between burning a disk image and copying as data, but that is opening a whole new can of worms and I'm just happy it is working....

---

### Post by Wim Sturkenboom on 2007-05-29
I don't know the finer details, but for a disk to be bootable certain files need to be on a certain place; there might also be certain info on the disk to indicate that it's bootable. That info will not be there if you extract first and the files are written in unknown order.

In the old DOS days, there was a command *sys*. Having e.g. command.com on your disk was not sufficient; *sys* would copy/move it (as well is two other files if I remember correctly) to the correct place on the disk.

Under linux, I think it's about the file syslinux or isolinux (the first thing that is loaded).

---

### Post by SoulinEther on 2007-05-29
These screencasts need to get more advertising, lol. It would have helped you with your problem.

Alan Pope did a good job with them honestly. You can still watch some of the other more detailed ones... With a 150kb/s connection I can watch the OGG Theora format streaming off the internet just fine.

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

---

