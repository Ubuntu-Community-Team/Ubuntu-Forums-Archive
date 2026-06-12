---
title: "Data Backup and travel solution"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by deepblue80 on 2007-12-02
Hello,
I have recieved great help in the past on here and am continuing to seek answers from the gurus out here. I am currently in process of upgrading to Ubuntu 7.1 from FIesty fAWN and need a backup solution to meet three objectives which are:

1. Obviously! Backup my data
2. Access to my desktop environment whilst I am travelling 
3. Dual Booting Windows

Before writing this post off as incoherent a few lines. I am running currently on a single 80 gb hdd. no backup yet in place and i need one. the straight forward one is to buy an external hdd and use one of the backup tools. But since i travel a lot with my companys laptop (windows xp) i may as well find out if i can have a system on the portable drive which is an exact mirror of my desktop so i can plug it into my work laptop which runs windows xp and lo and behold i have my home system up and running. also i wish to  add dual boot. i cant run windows xp in virtual machine for some reason and i do need a windows environment from time to time. 

so do i go for a portable drive + second internal hdd? or should i setup my machine as a server and i could then log in remotely using a web browser? i am a newbie with a couple of good ubuntu books on my desk now so a little explanation will go a long way in helping me understand the solution.
Thanks everyone for reading this. i look forward eagerly to the reply.
deepak

---

### Post by siciliancasanova on 2007-12-02
You can set it up to log in remotely with SSH but this is depends on how important the files are at home.  Do you have a battery backup?  Is there someone at home that can turn on the machine again if there is a long power outage?

If the files are important it would be best to take them with you.  I would repartition it then so the /home folder or just any partition really that you want to store these documents on is a FAT32 so you can go both ways with it between operating systems.

---

### Post by deepblue80 on 2007-12-02
> **siciliancasanova said:**
> You can set it up to log in remotely with SSH but this is depends on how important the files are at home.  Do you have a battery backup?  Is there someone at home that can turn on the machine again if there is a long power outage?

If the files are important it would be best to take them with you.  I would repartition it then so the /home folder or just any partition really that you want to store these documents on is a FAT32 so you can go both ways with it between operating systems.

No there would be no one available to reboot it at home when i am away. so presuming i backup on a portable drive in fat32 format will that be seamless access by Ubuntu and Win XP? If so i can just backup my entire system on the portable hdd and just carry it around.
also, if i dual boot my system with ubuntu/win xp will i see the external portable hdd in both? as i think that will be brilliant.

---

### Post by siciliancasanova on 2007-12-02
Yeah you should be able to see it in both.  I mean pretty much screw any software the HDD asks you to install, you should be able to read and write to it out of the box on both windows and ubuntu.

If you're talking an external drive (something I've never owned so I can't confirm this) but it should be FAT32 already.  So it doesn't seem like you really have much to do expect spend the money to buy it.

---

