---
title: "HP notebook with HP printer"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by liberalist on 2007-05-30
Hi everyone,

A friend of mine has a HP (Compaq nx9010) notebook with a "broken" copy of Windows XP (it is an OEM version and it is expired). It has the label "Designed for Windows XP" and is several years old (three I believe). However, it is terribly slow and due to "genuine advantage" issues, it cannot be rebooted. 

**My questions:**
1. Do you recommend an Ubuntu install or Xubuntu? I prefer Ubuntu 6.06 LTS. The notebook has 256-512 MB (estimated amount of memory), is this enough for Ubuntu or should I install Xubuntu/Kubuntu? It has an estimated hard drive space of 20-40 GB. 
2. Is her HP printer supported by default or should I install HP Linux printing (see [http://hpinkjet.sourceforge.net/]("http://hpinkjet.sourceforge.net/"))? What if she connects a Canon or other brand printer, would that work too with Ubuntu? 
3. Does Abiword consume less memory than OpenOffice.org's Writer? 
4. Do you recommend to install Wine? Does Wine pose a security threat? The Ubuntu standard installation is fine for her needs.
5. Can I install Amarok in Ubuntu or is there another good media player (preferably something like iTunes or Windows Media Player)? 
6. Does an external hard drive work? Should I format it FAT-32 or NTFS (the XP filesystem, is this compatible with Linux)? 

Concerning WiFi, she has either a wireless card (probably from HP) or an USB adapter. Would MadWifi be good or are there any other Linux/Ubuntu drivers?

Thank you very much in advance for your answers.

---

### Post by Inxsible on 2007-05-30
> **liberalist said:**
> Hi everyone,
 
A friend of mine has a HP computer with a "broken" copy of Windows XP (it is an OEM version and it is expired). It has the label "Designed for Windows XP" and is serveral years old (three I believe). However, it is terribly slow and due to "genuine advantage" issues, it cannot be rebooted. 
 
**My questions:**
- Do you recommend an Ubuntu install or Xubuntu? I prefer Ubuntu. The notebook has 256-512 MB (estimated amount of memory), is this enough for Ubuntu or should I install Xubuntu/Kubuntu? It has an estimated hard drive space of 20-40 GB. 
- Is her HP printer supported by default or should I install HP Linux printing (see [http://hpinkjet.sourceforge.net/](http://hpinkjet.sourceforge.net/))? What if she connects a Canon or other brand printer, would that work too with Ubuntu? 
- Does Abiword consume less memory than OpenOffice.org's Writer? 
- Do you recommend to install Wine? Does Wine pose a security threat? The Ubuntu standard installation is fine for her needs.
- Can I install Amarok in Ubuntu or is there another good media player (preferably something like iTunes or Windows Media Player)? 
 
Thank you very much in advance for your answers.
 
1) Your system memory should be just enough for Ubuntu. Kubuntu is also as heavy as Ubuntu ...just with a different desktop environment. I feel Kubuntu is more like Windows ( I am going to be hanged by Kubuntu lovers for saying that ;) )
2) Your hard drive space is also sufficient.
3) HP printers -- not too sure, but HP Toolbox is something you should look into. Run a live CD and see if her printer works. If it works in Live CD ...it will in the full install too.
4) I do not know the actual memory comsumption by AbiWord or Writer, but like you said, its just a replacement for Word. Whereas Open Office is the entire suite apps. It comes pre-installed with Ubuntu. Kubuntu comes with KOffice.
5) If you have some windows apps that you cannot live without..I'd recommend having a dual boot of Windows and Linux. Wine is good, but there can be some apps that would give you a lot of headaches.
6) I installed Amarok in Ubuntu and had lots of problems. There are others who use Amarok in Ubuntu and love it. For me, I use RhythmBox...Its interface is very much like iTunes.
7) External HDD's work...I use many. Formatting it is upto you. If you use that HDD in other Windows machines, keep it FAT32 or NTFS. If you choose NTFS, you will need to install ntfs-3g in Linux. If you choose to format those drives to EXT3, you will need fs-driver in the windows machines. If you dont plan to use those HDD's in Windows at all...format it to EXT3....its a neat file system that offers journaling
 
For info on partitioning or installing
 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
Hope that helps !!!

---

### Post by moredhel on 2007-05-30
I can confirm that Abiword is less demanding than openoffice, but if you need anything else like spreadsheets etc then openoffice would obviously have to be installed.

---

### Post by Zzl1xndd on 2007-05-30
As for your Ubuntu Vs Kubuntu question I would pick the one that you are using as it will be the easiest for you to support. 

Most HP printers have linux support the driver was preloaded for mine but you may want to check the model on the HP site.

If she doesn't need wine i would avoid it.

Amarok would be the way to go and installs nicley on Ubuntu.

and I like open office and if she is gonna use anyother function in it other then Word I would just stick with it.

---

### Post by liberalist on 2007-05-30
Thank you very much for your helpful replies. I think I am going to install Ubuntu 6.06.1 LTS Dapper Drake. 

Concerning WiFi, she has a Siemens Gigaset USB adapter 108. It connects to a KPN/Telefonica Experia (European brand) access point. Would [MadWifi]("http://madwifi.org/") be good or are there any other Linux/Ubuntu drivers?

---

### Post by Inxsible on 2007-05-30
Why not the Feisty?
 
It has much better support for hardware than the Dapper

---

### Post by Inxsible on 2007-05-30
especially since you are using Feisty yourself, you would be in a better position to help her out in case she needs it.

---

### Post by liberalist on 2007-05-30
> **Inxsible said:**
> especially since you are using Feisty yourself, you would be in a better position to help her out in case she needs it.

You have a point. However, I think she prefers to have Canonical Ubuntu support (i.e. security updates) till June 2009 and not October 2008. I have installed Ubuntu 6.06.1 on somebody else's machine and it is not much different from 7.04 Feisty Fawn. Moreover, I have bought the Desktop Guide for Ubuntu version 6.06.1 LTS. 

Would it be wise to install Feisty with the Alternate Install CD or doesn't that make any difference? Thanks in advance.

---

### Post by Inxsible on 2007-05-30
> **liberalist said:**
> You have a point. However, I think she prefers to have Canonical Ubuntu support (i.e. security updates) till June 2009 and not October 2008. I have installed Ubuntu 6.06.1 on somebody else's machine and it is not much different from 7.04 Feisty Fawn. Moreover, I have bought the Desktop Guide for Ubuntu version 6.06.1 LTS. 
 
Would it be wise to install Feisty with the Alternate Install CD or doesn't that make any difference? Thanks in advance.
 
AFAIK, Alternate CD installation is all text based. I think you'd be better off with the regular Install CD, and i think your system specs will handle it too !

---

### Post by liberalist on 2007-05-30
> **Inxsible said:**
> AFAIK, Alternate CD installation is all text based. I think you'd be better off with the regular Install CD, and i think your system specs will handle it too !

OK. Thanks. Should I ask my networking question somewhere else?

---

### Post by meborc on 2007-05-30
with 256 ram it should not be a big difference... go for live cd install just to see that everything runs and gets recognized before install

---

### Post by Inxsible on 2007-05-30
> **liberalist said:**
> OK. Thanks. Should I ask my networking question somewhere else?
I must have missed that question...Oh as well I guess, coz I really can't help you out there.
 
Try the LiveCD and see if you can get it working. If it works for LiveCD, it will most definitely work in the full install too.
 
EDIT : meborc beat me to it :)

---

### Post by liberalist on 2007-05-30
My networking issue is now posted in the correct Networking & Wireless forum:

[http://ubuntuforums.org/showthread.php?p=2749666](http://ubuntuforums.org/showthread.php?p=2749666)

---

### Post by liberalist on 2007-06-01
The soundcard of this notebook (HP Compaq nx9010) does **not** work with Ubuntu 6.06.1 LTS. How can I solve this problem? Thank you very much in advance.

---

