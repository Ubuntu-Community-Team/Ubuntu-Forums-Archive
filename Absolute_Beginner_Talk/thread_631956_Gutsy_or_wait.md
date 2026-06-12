---
title: "Gutsy or wait?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by PhoHammer on 2007-12-05
I am thinking about installing Gutsy Gibbon on my pc, but I noticed that LTS Hardy Heron comes out in April. How much work would it be to upgrade from gutsy to hardy? Should I just wait (i hope not, lol) and start with Hardy Heron?

---

### Post by LaRoza on 2007-12-05
Gutsy works well for many people, and upgrading it should be no problem, come April.

---

### Post by reincarnut on 2007-12-05
gutsy works for me like a charm. (and this was after i gave up on dapper and went back to mandriva. dapper wouldn't even install on my laptop. after dapper the next ubuntu i tried was gutsy). if gutsy is any indication, upgrading won't be a drag at all...

---

### Post by LaRoza on 2007-12-05
For a more sure thing, post your specs, and try the live CD.

---

### Post by PhoHammer on 2007-12-05
Lenovo ThinkPad R60 9457 (Core Duo 1.83 GHz, 512 MB RAM, 60 GB HDD) is what I have. I tried the live cd, it was cool, but it had to spin the disc quite a bit and was a little delayed when opening things like the sample videos. I figured that was just because it was all on the disc? And what does Ubuntu use the partition for that you give it?

---

### Post by bodhi.zazen on 2007-12-05
> **PhoHammer said:**
> I am thinking about installing Gutsy Gibbon on my pc, but I noticed that LTS Hardy Heron comes out in April. How much work would it be to upgrade from gutsy to hardy? Should I just wait (i hope not, lol) and start with Hardy Heron?

Why wait ? By that I mean desktop users typically like to be on the cutting edge, I know  I do. There will always be another version of Ubuntu right around the corner (releases occur every 6 months or so).

Upgrading usually goes well, but not always. I would bet that most people make a seaprate home partition and do fresh installs.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I suggest a /data partition (/media/data or /mnt/data) because /home also holds configuration files and, IMO, it is not necessary to save those ...

With this said, there are those who upgrade and this generally works well.

---

### Post by Mostlyharmless42 on 2007-12-05
I would say go with Gutsy now, but be sure to install with a separate /home partition.  Upgrading to Gutsy was so flaky that i ended up reinstalling with a CD.  This leads me to recommend that you be prepared to do this.  Also, from what i've read, it's generally better to use a fresh install anyways.

---

### Post by hyper_ch on 2007-12-05
As you are new to linux you will "experiment" in the beginning quite a bit and very likely screw up (I did ^^^). So you can test Gutsy now, get yourself familiar with it and linux in general... and then in april you'll know a lot more and you'll do a fresh install then according to your desires ;)

---

### Post by khurrum1990 on 2007-12-05
If u r new to Linux then I would say install Gutsy. If u r using Fiesty and everything works perfect then there is no need to upgrade unless there r some bugs or some fearures don't work. Then u should upgrade to 8.04 since its a long term release, it will probably be very stable.

---

### Post by PhoHammer on 2007-12-05
> **bodhi.zazen said:**
> 

I suggest a /data partition (/media/data or /mnt/data) because /home also holds configuration files and, IMO, it is not necessary to save those ...


This sounds complicated... I thought I would just make a partition for the current version, then use a program to repartition my hard drive when the hardy heron comes out? Is this a bad idea?

---

### Post by bodhi.zazen on 2007-12-05
> **PhoHammer said:**
> This sounds complicated... I thought I would just make a partition for the current version, then use a program to repartition my hard drive when the hardy heron comes out? Is this a bad idea?

Well, it is a snap to make a data partition.

Your plan works as well.

==============

How to data partition :

Use gparted to make a root ( / ) partiton to install Ubuntu size = 10 Gb 

make a swap partition , size = RAM X 2, max 1 GB, swap = RAM on laptops.

make a third partition (this will be your data partition). When installing you will be asked where to mount the partition. Manually enter a mount point of /media/data or /mnt/data

/media/data will appear on your desktop

/mnt/data will not appear on your desktop (I think ?)

you can change "data" to anything you like , for example /media/music or /media/share

Now you data is separate from you operating system, so you can reinstall without losing data.

---

### Post by PhoHammer on 2007-12-06
will Gparted give me choices as to what i make each partition? Like will it ask me if I want it to be the "swap" part?

---

### Post by bodhi.zazen on 2007-12-06
> **PhoHammer said:**
> will Gparted give me choices as to what i make each partition? Like will it ask me if I want it to be the "swap" part?

Yes

---

### Post by misfitpierce on 2007-12-06
7.10 works perfectly fine. Only prob you could have upon boot is no splash screen and sits at black screen. Either boot with nosplash or hit CTRL+ALT+F1 and google a fix which there is. Thats in worst case scenario though. 7.10 is fine and will upgrade to 8.04 just fine im sure.

---

### Post by PhoHammer on 2007-12-06
So should I make my swap partition 1 GB? Is 1 GB the absolute max you can make it? Does the size of your swap partition make a difference in performance?

---

### Post by PmDematagoda on 2007-12-06
No, if you have a lot of RAM, say about 2Gb, then a SWAP partition is completely unnecessary.

But if you have a lesser amount such as 512Mg of RAM, then about 1Gb for the SWAP partition will be enough.

The size of the SWAP partition does not govern how well your PC runs(Unless you have a very little amount of RAM), if you have a lot of RAM, then even a 1Tb SWAP partition will not make a difference. So don't waste space on a SWAP partition if you have a lot of RAM or do only a few memory intensive tasks and applications.

---

### Post by Sighn on 2007-12-10
I believe I just read that having 2GB of system memory means that there is no need for a swap partition, as far as Ubuntu goes?

I have an Acer Aspire 5672 laptop with 2GB of ram. Running Ubuntu, I've noticed that the system always reports 0 bytes of the, installation created, 3.1GB swap partition is being used. In other words the swap partition is never ever used, as far as I can see. Is this due to the size of the ram?

During the installation of Ubuntu, at the partitioner stage, I selected the second option (to use the entire hard drive). I assume the swap partition was created for the purpose of Hibernation, if not operation  performance.

In any case, Hibernation never works for my laptop. The system never actually shuts down. The monitor just goes blank. Normal suspend mode 'almost' works, but won't wake from being suspended.  I can't help wondering if the Hibernation problem and the lack of swap partition usuage ( 0 bytes)  might be linked? Is Ubuntu just not using the swap partition due to some kind of fault? After a few past rounds with Ubuntu, concerning other solved problems, I've not been able to conquer this hibernation issue.

Would be grateful for any help.

Ubuntu 7.10/Gutsy x86    Acer Asipre 5672    2GB    Ati Mobility X1400 (fglrx)    T7600 Core2Duo

---

### Post by Sighn on 2007-12-14
Nevermind. ATI driver thingy etc etc...

---

### Post by Gradius on 2008-06-30
> **Sighn said:**
> Ubuntu 7.10/Gutsy x86    Acer Asipre 5672    2GB    Ati Mobility X1400 (fglrx)    T7600 Core2Duo

Off-topic:

Hi Sighn,

Can you tell me if T7600 runs fine on Aspire 5672?  Because I have the same notebook and I want to upgrade the processor too.

Or if someone else did the same thing, please send me PVT confirm me if that (T7600) runs ok.

Thanks,
Gradius

---

