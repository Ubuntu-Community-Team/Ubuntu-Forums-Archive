---
title: "First date with Ubuntu..."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by a.taramelli on 2008-02-20
Good morning!

This is my very first time here and ready to start with Linux.

My main PC (Win 2000 + SP4) crashed once more...
My backup PC is the one I am using now.

My aim is to restart win Win 2000 the main iron and to install Linux on the back up one to practice with it.
After a break-in time, I'll definitely move to Linux.

But things are not as easy as I've been told...
I have Ubuntu 7.0.4, which, I've been told, is OK with an absolute beginner.

The c I wan to install it on has an partitioned HDD 
C: 76 Gb (73 Gb free) - where I install the OS
D: 19 Gb (14Gb free) - where I keep my files

My question is...
Should I format the C: partition to install Ubuntu or could I create an Ubuntu folder where to install it?

I apologize for asking such a basic question, but, reading other posts I cannot really understand what is told (and not for English!) :(

Thank you in advance for any help!

---

### Post by techstop on 2008-02-20
This is a good place to start;

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

The Ubuntu installer will take care of the partitioning for you, there is a guided portion of the install that allows you to choose the installer to resize the partition with the largest free space. It does that, then you specify how much you want to shrink the original partition (and therefore how much space you want to give to your new Ubuntu installation), and then the installer will create the appropriate partitions and mount points etc.

It's all very much easier than it sounds. Have a look at the link above, there are some good screenshots. Or, boot up with the LiveCD and see for yourself.

Good luck (not that you'll need it). Needless to say, make sure you back up vital data before installing.

---

### Post by Jussi Kukkonen on 2008-02-20
I'd suggest using the newest Ubuntu/ version: 7.10 -- hardware support gets better all the time and upgrading to the next versions will be easier.

With the same idea (keeping future upgrades as easy as possible), I suggest you make a small partition for the OS and a larger one for the files (/home-directory): 19GB should be more than enough for the OS and any programs you can think of as the basic install is around 6GB if I recall correctly. If you later decide to install a new operating system, the larger partition will be untouched.

In case you didn't know: You can keep your Windows install intact if you want to.

---

### Post by a.taramelli on 2008-02-20
Thank you all! :)

**Re.:techstop**
> 
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Thank you! Looking at something rather than reading about it will be much easier for me!
I', going to check it out very carefully

> Good luck (not that you'll need it)
False! I'll need **all **the luck available. Plus some extra... ;)

______________________________________________________


**Re.:Jussi Kukkonen**

Thank you JK! :)

> I'd suggest using the newest Ubuntu/ version: 7.10 -- hardware support gets better all the time and upgrading to the next versions will be easier.

There is a slight sit I did not mention... living in the middle of nowhere, I do not get a DSL, but just an IDSN, therefore it might take an awfully long time to download it.
But will manage that!

The second problem is... I haven't the faintest idea where to download it from: would you be so kind to let me have the URL, please?

I am _very _interested in an easier upgrading!!

> 19GB should be more than enough for the OS and any programs you can think of

I guess so too as, now, Win 2000 + SP4, KB's, AVG Antivirus, PhotoFiltre, Diskeeper Lite, Office, etc, I use 3,3 Gb!

> In case you didn't know: You can keep your Windows install intact if you want to.

I've been told that, but I am afraid files will "mix" and, should I in future un-install one of the 2 OS, I wouldn't want "leftovers".
Does the Ubuntu installation create a directory of its own?

Sorry for all the questions that sound stupid, but...

Thanks again!

---

### Post by hyper_ch on 2008-02-20
You cannot install within a partition. ubuntu uses a different file format.

So you can

(1) delete the whole disk and dedicate it to Ubuntu

(2) delete one of the two partitions and install ubuntu there

(3) resize one or both partitions and install ubuntu in the emptied diskspace

---

### Post by a.taramelli on 2008-02-20
Opsss...

Thank you hyper_ch!

> 
(1) delete the whole disk and dedicate it to Ubuntu
Would rather not as I might be needing Windows, at least for some time

> 
(2) delete one of the two partitions and install Ubuntu there
I might format the D: partition but would like to keep it to save files and prevent their loss

> (3) resize one or both partitions and install ubuntu in the emptied disk space
**This **sounds appealing as C: has 73,0 Gb available!
But... can it really be done **safely**?
And, last but not least, **what **with?

Thank you again hyper_ch!

---

### Post by techstop on 2008-02-20
> **a.taramelli said:**
> 
**This **sounds appealing as C: has 73,0 Gb available!
But... can it really be done **safely**?
And, last but not least, **what **with?

Thank you again hyper_ch!

As per my post above, the Ubuntu installer does this for you. See screenshots in link.

---

### Post by roaldz on 2008-02-20
Here are some Facts:

Ubuntu uses it´s own file system, called Ext3. Windows can not read this on it´s own, you can install a driver for this, but why should you. Ubuntu **can** read/write windows´s partition though.
The file format used by Ubuntu is the same as on windows - they are exchangeable.
Ubuntu needs it´s own partition, so it can boot it.
If you are planning to dualboot, make sure you install Ubuntu as last, so it can install the bootloader for all existing OS´s. This way you can easily choose which OS to boot.

Hope it´s helpful,

Roald

---

### Post by hyper_ch on 2008-02-20
> **roaldz said:**
> The file format used by Ubuntu is the same as on windows - they are exchangeable.

Actualyl it's not... ubuntu uses by default UTF-8 and Windows doesn't.

---

### Post by roaldz on 2008-02-20
> **hyper_ch said:**
> Actualyl it's not... ubuntu uses by default UTF-8 and Windows doesn't.

Yeah, well.. You´re right, but in n00b terms, it´s the same, becouse windows an linux can read each other´s files.. Who cares about character encoding at that point..

Roald

---

### Post by a.taramelli on 2008-02-20
Thank you techstop!

> As per my post above, the Ubuntu installer does this for you. See screenshots in link.

I was reading it but got interrupted several times... 
I'll go through it all before asking something else, I promise! :)

Thank you.

____________________________________________________

Thank you roaldz!
Therefore I may do what techstop said and, after that choose which system to boot from.

Does the installation itself allow to get the option of a dual booting or do i have to do something special?

Thank you

==================================================

By the way, I've been told with > AVG rescue disk I could get back in order the other PC.
[B]
Should I boot on the stuck PC with Ubuntu CD, Is there a possibility to copy the AVG rescue disk files on floppys to try to get it started again?[/B]

---

### Post by roaldz on 2008-02-20
> **a.taramelli said:**
> Thank you techstop!



I was reading it but got interrupted several times... 
I'll go through it all before asking something else, I promise! :)

Thank you.

____________________________________________________

Thank you roaldz!
Therefore I may do what techstop said and, after that choose which system to boot from.

Does the installation itself allow to get the option of a dual booting or do i have to do something special?

Thank you

==================================================

By the way, I've been told with 
[B]
Should I boot on the stuck PC with Ubuntu CD, Is there a possibility to copy the AVG rescue disk files on floppys to try to get it started again?[/B]

Dual booting will be set up automatically.
I´m not familiar with the AVG Rescue disk.

Roald

---

### Post by a.taramelli on 2008-02-20
Hey roaldz! Fastest replyer in the West! :)

Thank you, but, actually I **do not need an expert in AVG** but just to know if i could copy files from a directory onto a floppy using Ubuntu from CD!

Thanx

---

### Post by roaldz on 2008-02-20
> **a.taramelli said:**
> Hey roaldz! Fastest replyer in the West! :)

Thank you, but, actually I **do not need an expert in AVG** but just to know if i could copy files from a directory onto a floppy using Ubuntu from CD!

Thanx

You can use the Ubuntu LiveCD to copy files from your windows partition to a floppy. You are also able to use the internet if you´re on the livecd.

Roald

---

### Post by billgoldberg on 2008-02-20
I saw you metioned ubuntu 7.04.

I find 7.10 to be better but if you are a newcomer "linux mint" might be easier. (it has the multimedia drivers installed by default and has a more windows like menu).

---

### Post by Jussi Kukkonen on 2008-02-20
> **a.taramelli said:**
> The second problem is... I haven't the faintest idea where to download it from: would you be so kind to let me have the URL, please?


[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

You may also be interested in other options on that page ("buy on CD" and "request free CD"), but be aware that the free CD shipping may take a couple of months in the worst case.

---

### Post by sp0nge on 2008-02-20
So often I see this topic of how to set a dual boot system and mostly the users say they don't want to get rid of windows completely- it's like a security blanket. But what are you hanging on to windows for? 

Since you mentioned formatting, i presume the data on the hard drive is either backed up or not overly important. That being said, I would ask what you're hanging so dearly on to windows for, and advise you to consider on of these options: 

*If multiple machines are available on your network, make one windows machine available for remote access by the ubuntu laptop. 

*If you can't live without windows, consider having your installed Os of choice paired with VMWare. Then you can load multpile virtual machines as needed, limited only by hardware capability.

*Wine- Use an emulator under ubuntu for anything you might need to do in a windows environment.

Hope this helps.

---

