---
title: "First Timer Setup"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by fatherkeith on 2008-03-27
Everyone,

First I want to say that I am a expert at windows but a extreme newbie when it comes to the kubuntu 7.10 (Gutsy) 64 bit operating system.  I have found myself wanting to convert to the gutsy operating system.  So here is what I want to accomplish:
1.	Use the Compiz fusion
2.	Run the Virtualbox so I can Windows XP installed and run some programs and stuff that I am stuck with in windows.
3.	Watch tv so my computer is a PVR.
4.	Have a RAID 5 running 

Although I can provide you with more information here is my system info .

ATI All in wonder x1900 card
ASUS M2N32-SLI Deluxe WiFi
Three Seagate SATA 2 drives in the RAID 5
Athlon 64 4200 (I think) with 2GB of RAM. 

Any help would be great. I have tried to load the latest ATI Catalyst drivers but got major issues with the screen flicking (only a single monitor) but I do not know if it was the driver or it was the setup.

---

### Post by ahsile on 2008-03-27
> **fatherkeith said:**
> 
1.	Use the Compiz fusion

You will definitely need the catalyst drivers, or run the open source ati driver. I didn't have a good experience with the catalyst install, and it wasn't exactly easy to remove either. Not sure about the flicker though. I've gone back to just using what's in the repository.

> **fatherkeith said:**
> 
2.	Run the Virtualbox so I can Windows XP installed and run some programs and stuff that I am 
stuck with in windows.

Have you tried wine? It may suit your purposes and be lighter weight as well.

> **fatherkeith said:**
> 
3.	Watch tv so my computer is a PVR.

If you have a video capture card you can record TV with MythTV. It can also be used to set your computer up as a media centre even if you don't have a capture card.

> **fatherkeith said:**
> 
4.	Have a RAID 5 running 

Do some research on mdadm. Basically, you'll need to format your drives and set the type as Linux Raid Auto. Then, use mdadm to build a raid5 array. Finally, you should be left with a device called 'md0' which you can format as ext3 and mount as your raid.

---

### Post by billgoldberg on 2008-03-27
1.	Use the Compiz fusion

Install your driver through system -> administration -> restricted drivers managment or look on google for "envy".

You might have to change you xorg.conf to set composite to "1".

Then go to system -> preferences -> apperance, in the visual effects tab pick "custom".

Then download compizconfig from synaptic, and go to system -> preferences -> advanced desktop effects settings to tweak compiz fusion.

2.	Run the Virtualbox so I can Windows XP installed and run some programs and stuff that I am stuck with in windows.

Virtualbox is in the repositories so you can download and install it using synaptic package manager.

But I'm sure your windows programs have linux counterparts.

3.	Watch tv so my computer is a PVR.

Myth tv, it's in the repo's.

---

### Post by fatherkeith on 2008-04-04
Everyone,

Well here first I want to say thanks for the help.   I have found that the ATI x1900 has its real disadvantage when it comes to Kubuntu  7.10 (Gutsy).  I have tried a number of posts and even though I have done many times with the updated driver version from the ATI site I have not been able to load the driver successfully.  However, by using the ATI x1900 driver that Gutsy comes with works great.  Does anyone know if this driver has the ability to do 3D so I can use the Compiz Fusion drive?

Also I have found that the MythTV does not work with ATI x1900 cards.  So I am wondering if I can use a Virtual software (i.e. VMware, Virtualbox) that will allow me to watch tv in the Virtual mode?

I still have not tackled the RAID 5 issue because I am making sure it works on a single test drive before moving it to my production drives (which is running Windows XP right now).

---

