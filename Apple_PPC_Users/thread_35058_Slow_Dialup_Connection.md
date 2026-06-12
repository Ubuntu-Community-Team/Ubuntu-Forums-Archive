---
title: "Slow Dialup Connection"
date: 2005-05-17
forum: Apple PPC Users
---

### Post by danield on 2005-05-17
On a rev. B iMac using its internal modem, my download speeds are only about 1K per second.  The same modem works fine under Mac OS 8.6, so it's not a hardware problem.  Under Linux the modem shows up as /dev/ttyS0 after autodetect.

I noticed in Network Tools that there seems to be activity in the Loopback Interface(transmitted bytes/packets and received bytes/packets).  Could this be related to my problem?  Could the "loopback interface" be crowding my ppp connection?

I'm an extreme newbie when it comes to linux, so easy on the code. :)

---

### Post by defkewl on 2005-05-17
How slow is slow? Could you give a comparison. The loopback interface has got nothing to do with it. Every computer has a loopback interface for stating localhost.

---

### Post by danield on 2005-05-17
[QUOTE=defkewl]How slow is slow? Could you give a comparison. The loopback interface has got nothing to do with it. Every computer has a loopback interface for stating localhost.[/QUOTE]

I get 5K per second download speeds under Mac OS, but only 1K per second speeds under Ubuntu Linux.

---

### Post by ssam on 2005-05-18
one tip i remember from a few years ago is when you set up a modem and it asks for your speed, dont put in 56000, leave it at  115200(or what ever it is be default).

i am not sure how this effects to speed.

sam

---

### Post by raw_knee on 2005-08-06
it should be set to 115200 because the speed settng is that of your modem to your computer... it's different from the connection set from your modem to your provider...

---

### Post by mingus on 2005-08-13
[QUOTE=danield]On a rev. B iMac using its internal modem, my download speeds are only about 1K per second.  The same modem works fine under Mac OS 8.6, so it's not a hardware problem.  Under Linux the modem shows up as /dev/ttyS0 after autodetect.
 :)[/QUOTE]

Go to [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/) download, install, run scanModem.  It will tell you the modem chipset and most current driver, which may be the source of the problem.

---

### Post by Ptero-4 on 2005-08-14
[QUOTE=mingus]Go to [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/) download, install, run scanModem.  It will tell you the modem chipset and most current driver, which may be the source of the problem.[/QUOTE]

Mingus. IIRC a rev b iMac is one of the first g3 iMacs. danield got one of the iMacs with a hardware modem so the chipset is def not the problem. The slowass conexant modems were added to the iMac line with the flat panel G4 iMac.

---

### Post by glasgobip on 2005-08-25
[QUOTE=Ptero-4]Mingus. IIRC a rev b iMac is one of the first g3 iMacs. danield got one of the iMacs with a hardware modem so the chipset is def not the problem. The slowass conexant modems were added to the iMac line with the flat panel G4 iMac.[/QUOTE]

I have the same problem on a PC laptop with external 56 K modem. Max download speed on windows is 5K/sec. On linux, max speed is 1 k/sec. Do you have an idea about this gap? 
Do you know a tool which can display on linux the speed connexion with my provider (42000 with window)

---

### Post by mingus on 2005-08-25
[QUOTE=glasgobip]I have the same problem on a PC laptop with external 56 K modem. Max download speed on windows is 5K/sec. On linux, max speed is 1 k/sec. Do you have an idea about this gap? 
Do you know a tool which can display on linux the speed connexion with my provider (42000 with window)[/QUOTE]

There are many factors that can affect network throughput, not only inside your machine but also externally.  Go to [www.dslreports.com](www.dslreports.com) and perform the speed test from several sites, both from Linux and Windows.  Compare the results.  If Linux is giving you poor results by comparison, check the driver you have.  You may also have to look into setting the modem's parameters (such as how it initializes, settings that may conflict with your ISP, handshake, compression), not a Linux or Windows issue, a modem configuration issue.

---

