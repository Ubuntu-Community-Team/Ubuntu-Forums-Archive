---
title: "Slow Lan"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by brander on 2007-03-02
Search finds a lot of people with the same problem but no solution yet so I am asking again. In Linux the speed of a large file being transferred to a Windows share through my LAN is 3 Mbytes/sec. The same machine in XP does around 10 Mbytes/sec.
As it happens, 3 Mbytes/sec is the same as Windows 98 and NT4 which makes the Ubuntu speed look a little out of date.

The conditions are: connect to server/windows share. The net card is Realtek 8139 
100Mb/sec and is connected to 100 or 1000 Mb switch.  I have run the ethtool and it is running at 100 Mb/sec Full Duplex. Is it likely to transfer data  at 30Mbytes/sec(10X current speed) if I put a Gigbit net card in?

---

### Post by firefly2442 on 2007-03-02
Your download speed is probably going to be based off a lot of things.  First of all, the transfer protocol that you use will probably have a small effect.  The 100 Mbit LAN ethernet connection is good, but like you said, 1000 Mbit is better.  It could also be the fact that you are maxing out the available read speed of your hard drive either on the reading or writing side.  I had some old SCSI drives that had a max read speed of 40MB/s which I maxed out under 1000 Mbit ethernet.  It could also be the fact that your LAN network is congested with lots of traffic and thus slowing down your download.  So there are lots of possibilities.  Why do you need it to be faster?

---

### Post by brander on 2007-03-03
Hi, thanks for the reply. I assure you that there is no other network traffic nor is the drive maxed out at just 3 Megs a second.
In response to your question on speed, if I want to move a number of HD movies or drive backups around, much less time is required. With my intention of using Linux as a file store with Terabytes of files, speed of transfer is quite important. I`ll try a Gigabit net card. Thanks.

---

### Post by firefly2442 on 2007-03-03
Make sure your ethernet cable is CAT5e or better as this supports gigabit speed.  Yeah, if you are building a huge server you will certainly want the fastest access possible.  A fast computer with decent hard drives and gigabit ethernet is the way to go.  I switched one of my machines over from 10/100 to 1000 Mbit and the transfer rates skyrocketed.  Good luck with the project. :)

---

