---
title: "How to make the internet connection"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2006-05-06
PC Chips MLR 810
Duron 800
512 Meg Ram
250 Gig Seagate HD

During the install of ubuntu it failed to automatically set up my net work connection. I am running on a USB network adapter on this system.

I tried to install my Linksys CD which has a file from my main PC ( the one connected directly to my network), this file can be ported to any remote pc and makes it easy to connect to my network

In this case the CD is not auto installing so I cannot get the wireless adapter working. Also I want to go to the HD and select the drive D:/ which should be the CD so that I can run the programme but I cant figure out ( no right click on explorer available)how to see my drive.
Also when is Kubuntu better than Ubuntu is it when I want a look and feel of windows and can I download it and simply upgrade or is it an overwrite
Thanks

---

### Post by neouser99 on 2006-05-06
kubuntu vs. ubuntu is merely a difference between the desktop session that you wish to use kde vs. gnome respectively. you can have both of them installed side by side without a problem... and we could probably worry about that after we get your network card working.

the said cd probably does not have linux drivers on it, and therefore probably will not install off that, and it definately doesn't have an auto start script similar to windows. there would be a few things that would be helpful to get the card working.

what exactly is the card model??
and paste the output of this
```
sudo lscpi
```
that command can be run in the terminal, which can be found under the Applications -> Accessories menu. Don't be intimidated if this is your first time at a terminal (this is an assumption, and i apologize if it isn't)... as it could become your best friend down the road, and one of the reasons so many people love linux. also, it will ask for a password, just type the one that you use to logon with.

-neo

---

### Post by clemkonan on 2006-05-06
The network ( Nic) is integrated into the motherboard but I also have a Linksys card  10/ 100 version 5.1 in a pci slot its about 4 years old.

---

### Post by clemkonan on 2006-05-06
Typing the code into terminal correctly prompted me for a password, which I entered but for some reason was not visiable when my glance went back to the screen. Subsequent efforts failed to give me a password prompt all I get is 
sudo: lscpi : command not found

---

### Post by clemkonan on 2006-05-06
I tried Ispci -v | grep Ethernet this returned the following:
0000:00:01.1 Ethernet controller SIS 900 pci fast ethernet (rev82)

Subsystem SIS 900 10/100  Ethernet adapter

0000:00:0b.0 Ethernet controller Linksys NC100 Network everywhere  fast ethernet  10/100 ( rev 11)

As I said before the first NIC is on the mobo the second is in a pci slot.

Is this code correct "sudo lscpi" or should it be Ispci?

---

### Post by neouser99 on 2006-05-06
i don't understand what you mean by a usb network connection then. as you have stated, you have an onboard nic and a pci nic, so what is it that you are trying to do?

---

### Post by clemkonan on 2006-05-06
Sorry for the confusion I have 2 computers one is connected directly to the internet through my Linksys router , the second pc the one I am experimenting with Linux on is a remote pc and has a Linksys wireless USB adapter.

The file I was trying to use would typically be inserted in the CD Rom of the remote computer and would set up the wireless adapter using settings from the main computer. Clearly this solution works for Windows and not for Linux.
So I am trying to get a wireless Linksys USB adapter connected.

---

### Post by neouser99 on 2006-05-07
there might be someone around here that has used that wireless card before. there are some drivers that you need, as the kernel isn't picking it up at boot time, making it difficult for it to connect to anything. i'll see if i can find some stuff later if no one has had any success. you might wanna try google a bit see if you can come up with some linux drivers for the card, or even search the ubuntu forums a bit.

-neo

---

### Post by mips on 2006-05-07
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

First you will have to establish what chipset your Linksys uses. Look at the above guides.

---

### Post by monomaniacpat on 2006-05-07
I highly recommend you use open source drivers, of which there is a database [here.]("http://linux-wless.passys.nl/")

If there are none available, the easier option is probably [ndiswrapper.]("http://ubuntuforums.org/showthread.php?t=81461&highlight=ndiswrapper-utils")

This is a difficult task, especially for n00bs, so let us know if you get stuck. On the database you should at least find the chipset (the hardware which is the same across many network cards) which is more likely to turn up results when googling or searching the forum.

---

### Post by clemkonan on 2006-05-07
I spent the last day checking the forums and came away with a headache. ndiskwrapper seems to be the way to go but for a novice I might stll be here come Xmas.
So, I pulled out the old cordless drill,  punched a hole through the adjacent wall, set aside the wireless adapter and using cable ran the connection from the NIC on the mobo to my router(Linksys WRT 54G V3) 
So lets forget about wireless for a moment what do I do next ( keep it simple please)so that I can get online. In the mean time I will keep searching the forums.

---

### Post by clemkonan on 2006-05-07
Eureka !  Home run Thanks everyone. I stumbled my way through and found 
 something like System | administrator | Networking  I set up the two cards then eventually found the one that worked. 

I do want to come back to the wireless solution because I have decided I want all my machines running Linux. I have ndiskwrapper on my desktop along with a driver called rt24001.2.2.b3 tar.gz is this the correct driver for Linksys USB54G ver4 and how do I do the set up.
Is there a getting started manual or tutorial I can read over the next day to start the leaning process?

Thanks again

---

### Post by mips on 2006-05-08
Did you look at the links I posted as the info is there I believe.

---

### Post by clemkonan on 2006-05-08
Yes I did but I need to take a more detailed look, will do over the next few days. Thanks again

---

