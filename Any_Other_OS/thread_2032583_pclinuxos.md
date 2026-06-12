---
title: "pclinuxos"
date: 2012-07-24
forum: Any Other OS
---

### Post by coffee7 on 2012-07-24
please help me i want to delete windows vista and install pclinuxos 2012 my laptop 
sys model: hp compaq presario C700 
sys type: X86-based PC
ram: 1 GB
processor:Intel(R)pentium(R)Dual CPU T2370@1.73 GHz,2cores
sys manufacture: Hewlette packard
is every things work in right way????

---

### Post by DarkAmbient on 2012-07-24
PCLinuxOS is not something I've installed before. But after downloading the imagefile, burnt it to disc and then inserted it into your computer, their should be an step-by-step installationguide. It usually is atleast when it comes to many Linux-distros. From that installationguide you can choose to wipe out everything on your harddrive(s) before installing PCLinuxOS.


*Dont bother this beneath if you choose to automatically setup partitions: *
If you choose to manually setup partitions, choose filesystem "ext4" for all partitions. Then a good setup would be 7-15GB space for "/".  256mb for a swap-partition, and the rest of your discspae goes to "/home". That way you can re-install your OS in the future without loosing your home-folder and all its files.

---

### Post by coffee7 on 2012-07-24
thanx so much for illstration but i hope to know is pclinuxos compatible with my laptop

---

### Post by sffvba[e0rt on 2012-07-24
If it uses Intel graphics (like it seems to with a quick Google search) you should be good to go. I would recommend trying it Live first from the CD/DVD but I can't see from the website if their available images are Live or not...


404

---

### Post by drawkcab on 2012-07-24
Yes run the live cd and test it before you install it.  This should give you a pretty good idea of whether or not it works.

---

