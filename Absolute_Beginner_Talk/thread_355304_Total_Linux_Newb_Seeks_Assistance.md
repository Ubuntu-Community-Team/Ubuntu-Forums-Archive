---
title: "Total Linux Newb Seeks Assistance"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by cyberouijaboard on 2007-02-07
Hello All,
I have just read alot of information about Ubuntu and have heard a lot about it so I felt it is something I might want to try.
I have intermediate experiance with Windows 2000pro and it is what I will be Migrating from it to Ubuntu Server 6.06 LTS 64bit.
Mainly I want a gaming machine capable of running the lastest game and also a few older DOS games I have been unboxing lately. 
I do a little bit of video editing too and would like to use this computer as a server for my older computer once I have become confortable using Linux.

Now that I have downloaded the ISO I will be burning it to disk and then firing away!
To get a head start though, I decided to post a early SOS since I feel I will need all the help I can get before getting it installed on my machine.
After I install Ubuntu I will need updates, drivers, security app)antivirus/firewall  blah blah..I could really use some recommendation's!

I was thinking of either using AVG or Avast for Virus Protection.
Not sure what to use for a Firewall though.

I noticed that downloading and installing apps/tools is a lot different from the self executables I am use to on Windows.
Most of it seems to look like CLI through a terminal and the commands are very alien from DOS.
Any and all help is greatly appreciated!

My system specs:

Intel Pentium D 805 Smithfield 2.66GHz LGA 775 Processor

ASUS P5N-E SLI LGA 775 NVIDIA nForce 650i SLI ATX Intel Motherboard

CORSAIR XMS2 1GB (2 x 512MB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model TWIN2X1024-6400C4

Western Digital Caviar SE16 WD2500KS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive

SAPPHIRE 100166L Radeon X1650XT 256MB 128-bit GDDR3 PCI Express x16 HDCP Video Card


Thank you.

---

### Post by Maestro23 on 2007-02-07
Welcome to the community man. Some links to get you started:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

ATI Driver Install: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by kevinlyfellow on 2007-02-07
> Mainly I want a gaming machine capable of running the lastest game

Make sure to keep windows on there (dual boot).  While there are a few new games that have linux versions, its safer just to stick with windows for gaming.  

Your radeon graphics card will need a driver.
[http://ati.de/support/drivers/linux/linux-radeon.html](http://ati.de/support/drivers/linux/linux-radeon.html)

> I was thinking of either using AVG or Avast for Virus Protection.
What are you going to do with those?  Viruses are mainly a windows thing

For a firewall, tryout firestarter

---

### Post by cyberouijaboard on 2007-02-07
Awesome, Thanks!

Question, I can keep Windows installed and install Ubuntu Server 6.06 LTS without a problem?

---

### Post by r4ik on 2007-02-07
No virus/ad/spyware programm needed.
Welcome to Ubuntu !
For you're graphics,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by seshomaru samma on 2007-02-07
Sure
[here]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html") is a detailed howto (its for XP/ubuntu so you'll need to make some adjustments)

some might dispute this but i dont think you need an anti-virus for Linux
firewall is  easy to set

---

### Post by cyberouijaboard on 2007-02-07
> **r4ik said:**
> No virus/ad/spyware programm needed.
Welcome to Ubuntu !
For you're graphics,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

No virus/ad/spyware program needed?
This is hard to grasp!

---

### Post by Sbarton on 2007-02-07
There is also a program called 'Automatix' which I think is helpful to begin with installing some software and which contains a security suite which contains a firewall (Firestarter) and AV (ClamAV) should you wish to install. Personally I would keep Windows until such time as you are convinced you no longer need it. I am still dual booting.
Another very helpful site to view is [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/). I have found this site very useful with dual booting and more.
regards:)

---

### Post by kinson on 2007-02-07
> **cyberouijaboard said:**
> No virus/ad/spyware program needed?
This is hard to grasp!

It's a bit hard to grasp at first isn't it? :p

It's like someone swearing at you in a language you don't understand...its not gonna offend you :P Those virus .exe's or whatever don't run :D

Do install a firewall though (Firestarter or whatever) :)

In terms of keeping Windows, you have a choice of dual booting, or running windows in a virtual machine(VMware or anything similar). I myself am dual booting now, but I plan to wipe everything, install Ubuntu and run XP from a virtual machine. Having said that, there will be a performance hit when running games/windows from a virtual machine, so if you're the kinda person who gets high by extremely high framerates in gaming, dual booting would probably be the best option. :lolflag: 

Cheers,
Kinson

PS: Welcome to Ubuntu :KS

---

### Post by koshari on 2007-02-07
> No virus/ad/spyware program needed?

those are WINDOWS features,

---

### Post by kinson on 2007-02-07
> **koshari said:**
> those are WINDOWS features,

LOL ! That makes me think of this:

[Is Windows A Virus?]("http://www.annoyances.org/exec/show/article09-115") :lolflag: 

Cheers,
Kinson

---

### Post by gatoruss on 2007-02-20
> **koshari said:**
> those are WINDOWS features,

Juat a question, I have recently installed Ubuntu and was wondering the same stuff about viruses.

What purpose does the linux version of AVG Grisoft server? ([http://free.grisoft.com/doc/5390/lng/us/tpl/v5]("http://free.grisoft.com/doc/5390/lng/us/tpl/v5")

---

### Post by george29 on 2007-02-20
Just to clarify... 

for gaming - best to dual boot as linux support for a lot of new games is minimal to non-existent...

The program firestarter is not a firewall - it is a graphical user interface for configuring the firewall 'iptables' which is present in the linux kernel.

If you are planning on using Ubuntu as a file server in a mixed OS network then using anti virus software is recommended for scanning the data files you are serving to other machines. It's not necessary for the ubuntu server installation, but will help protect any Windows clients that are connecting to it and accessing the files that it holds. A virus might not be active when on the linux server, but it can still do damage when transferred to a windows machine.


george

---

### Post by jvc26 on 2007-02-20
You might use a virus scanner as although your odds are you cant be infected, you can transmit the virus to someone else - perhaps in a file you are sharing between Linux and Windows boxes. In this case you may want to scan the thing you've just downloaded to check whether it is ok or not. (Or just send it to the windows box and scan it there)

I'd have a look on here: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
Il

---

### Post by lyceum on 2007-02-20
I would look over Psycocats Ubuntu page before doing anything, and be sure to back up your files. I have some other links in my signature that you might also find useful.

Welcome aboard!! :)

---

