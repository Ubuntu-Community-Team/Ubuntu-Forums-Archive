---
title: "What is wrong with my edubuntu 7.10 server installation??"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by dasbisw on 2008-01-11
Hi everyone,
I am a beginner in this total UBUNTU environment. Trying to install it as a server and trying to setup a LTSP configuration. But i am getting so many errors that i am stucked into middle of my work. Problems what  i have faced and some tricks which i tried to implement (Though those will sound foolish, as i really dint know what was i doing.)

**Configuration:**
_Motherboard:_ INTEL 965RY
_Proccessor:_ core2 duo
_Harddisk:_ 300gb SATA
_RAM:_ 4gb ram
_DVD WR:_ LG
_LAN Card:_ 1. INTEL Gigabit [Built-In] (For Internal LAN)
                  2. Realtek [External] (For Internet)
_VGA:_ Built-In
_Sound:_ Built-In


**Problems Faced:**
1. Most of the time it shows one error as "An error occurred while trying to install kernel into the target system kernel package linux-generic" (Most cases while installing base system at 83% progress).

2. Next type of error is "unable to install the software...".


**Tricks Used:**
1. _CD Problem:_ Tried with 5-6 variation of CD. But all gave them same error.
2. _CD ROM Problem:_ Tried with different brand ROM.
3. _Configuration Problem:_ Tried with INTEL 865, others were same.
4. _LAN Problem:_ Unplugged External/Kept both lan. Tried both.
5. _Internet Problem:_ While installing Kept internet on/Off both.
6. _Hard Disk Problem:_ Everytime hard disks were secured cleaned, so no chances of previous installation traces. Even tried with raw hard disk.
7. _Partitioaning problem:_ No idea, because we tried with both default partioning and manual one.


Now what is left??? I am totally a beginner. It will be very helpfull if any1 can suggest me what to do with the installation or how to do. I will be waiting for the answer.
:popcorn:

---

### Post by reckless2k2 on 2008-01-11
are you using the alternate install CD? 

also, there are boot commands that can be used to bypass some errors. it might be a ACPI, DMA, or even video issue. 

i remember some commands being like:

no acpi or video = vesa


someone please weigh in on the boot bypass commands.

thanks.

---

### Post by dasbisw on 2008-01-12
reckless2k2 --- > Thanx for replying.:)

We are using "alternate install CD".....

But i am not getting what are u trying to say....:confused:

It will be good for me if you can explain that.....:KS

---

### Post by dasbisw on 2008-01-12
So no one knows or came across this problem??

---

### Post by Dragonbite on 2008-01-14
I assume you've checked your CD for errors.  Burning it more than once won't solve it if it is a bad image to start with.

I have at least 1 Ubuntu CD that is defective (and I got it from ShipIt too!).  Had an Edubuntu fail too but not after getting most of the way through the installation. Scanning the disk confirmed my suspicions (good thing I had another ;) )

Are you using Edubuntu 7.10?

---

### Post by dasbisw on 2008-01-15
> **Dragonbite said:**
> I assume you've checked your CD for errors.  Burning it more than once won't solve it if it is a bad image to start with.

I have at least 1 Ubuntu CD that is defective (and I got it from ShipIt too!).  Had an Edubuntu fail too but not after getting most of the way through the installation. Scanning the disk confirmed my suspicions (good thing I had another ;) )

Are you using Edubuntu 7.10?
Ya i am using EDUBUNTU 7.10.

And your kind information i am having the ISO file dowmloaded, cheked "md5sum" too.

So i dont think it can be a corrupted CD...and let me tell you its installing all other system without any single problem.....

Funny???

---

### Post by Dragonbite on 2008-01-15
Do you have a RAID?  Our computer club has a server that Ubuntu died on because of the raid, though it never got to the installation stage so I am doubtful that is the cause.

I believe what reckless2k2 was refering to is when the boot screen starts you usually have options listed along the bottom of the screen (F1 F2 F3 ..).  They may list somewhere some of the different configurations (noacpi, etc.)

Another option is to try (either with Edubuntu or a Server CD) installing the bare minimum system (practically kernel & apt-get only) and then use APT-GET to install the Edubuntu files/configuration.

Have you tried any LiveCDs?  Ubuntu, Knoppix and Damn Small Linux are 3 good ones to try. If they don't work they may provide some information on where they are failing (graphics, motherboard, NIC, etc.).  I take it from your description that the installation screen doesn't tell you what it's working on when it fails?

Just seems to not like something with your system, but that's where installing another distro may help.  The server mentioned above with the RAID Ubuntu failed on also failed with CentOS ( a Red Hat clone) but on the CD drive, not the RAID and openSuse installed without a single hiccup!

Good luck.

---

