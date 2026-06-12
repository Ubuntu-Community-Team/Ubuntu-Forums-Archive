---
title: "Will xubuntu (latest) run on this older pc"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Silverstarme on 2007-06-20
I have here standing a somewaht older pc. It now runs Windows ME (Misrable Edition) and is mostly used for MSN. Today I fixed it and removed some trojan horses ad/mal/spyware. But still it crashes regulary due that Windows ME is one of the worst and most instable OS'es ever released.
 If it crashes perm. now the costs for reparing (have no Windows CD, so have to take it to a specialist) will be more then the pc is worth.
De systemrequiremnets say how much ram is needed but not how fast the cpu must be.
De specs of the older pc are as following:
CPU: AMD Duron Spitfire 700mhz
RAM: 192mb
HD: 10GB
Graphics: 8mb Nvidia TNT Vanta
Drive1: DVD-ROM
Drive2: CD-RW
How well can it run in a network with a XP Home Edition SP2 machine (the machine I am typing from now)? Or is it impossible, due the so different nature of the OS'es?

---

### Post by atria on 2007-06-20
Xubuntu will run on that computer provided that the hardware is supported.

Ubuntu can co-exist with Windows XP on the same network, dont worry :)

---

### Post by diatribe on 2007-06-20
Xubuntu will most likely run, but you are going to need the alternate-install cd probably.  Also you may want to look into some of the even less resource-heavy window managers, like fluxbox

---

### Post by Silverstarme on 2007-06-20
Well with network I mean not just on the same router, but also enable file sharing. If that is what your meaning with co-excist , no further question. I think this is all I need to now. I am currently downladoing the alternate install cd and will burn that on a disc keep that ic case of emergencies.

---

### Post by notbitmonk on 2007-06-20
I installed Ubuntu on a 515 Mhz AMD with 128 mb of RAM and it ran pretty well (somewhat slow but manageable).  I wasn't able to install Xubuntu on that machine though.

---

### Post by diatribe on 2007-06-20
I dont know too much about file-sharing between windows and ubuntu, but I'm sure if you search the forums there will be plenty of posts and prolly a howto

---

### Post by maruchan on 2007-06-20
I have two similar machines. Ubuntu Breezy Badger ran really well on them...but finally I chose to use [Puppy Linux]("http://www.puppyos.com/") for the slow machines and Ubuntu/Kubuntu for my faster Linux system.

Puppy has a program called "LinNeighborhood Samba Client" that should allow you to connect to, and mount, a Windows network. It works great here.

If you can use Ubuntu or Xubuntu, the package management is much better, and more obscure software is available. But for an old computer, I don't install new packages that often, and when I do, I usually just upgrade Puppy (put in a new CD) instead.

---

### Post by hummingbird59 on 2007-06-20
I haven't used it myself but I've read that damn small linux will run on anything.  See: [http://distrowatch.com/table.php?distribution=damnsmall](http://distrowatch.com/table.php?distribution=damnsmall).  This may be too barebones for you but still an option.  I don't know anything about the networking capabilities - sorry.

---

### Post by ugm6hr on 2007-06-20
> **maruchan said:**
> I have two similar machines. Ubuntu Breezy Badger ran really well on them...but finally I chose to use [Puppy Linux]("http://www.puppyos.com/") for the slow machines and Ubuntu/Kubuntu for my faster Linux system.

Puppy has a program called "LinNeighborhood Samba Client" that should allow you to connect to, and mount, a Windows network. It works great here.

If you can use Ubuntu or Xubuntu, the package management is much better, and more obscure software is available. But for an old computer, I don't install new packages that often, and when I do, I usually just upgrade Puppy (put in a new CD) instead.

The Samba Client in Puppy is exactly that - client - not full server.  So it only allows networking access in one direction (from Puppy to other machines).  To be honest - I couldn't even get that to work properly (but that's proably just my incompetence - because the forums explain it is possible - and I didn't try too hard).  Don't get me wrong though - I think Puppy is actually a more appropriate choice for less than 256MB RAM machines.

Xubuntu should run - it might just be a bit slow booting.

---

### Post by Silverstarme on 2007-06-20
i am not looking to get a machine that boots in 1 sec or so. The machine must be able to play mp3 or other music files and surf the internet smootley and be functional. According to xbuntu you need 64mb minimum, 128mb rec. and 192mb for install.
My main XP machine with a 2.8ghz P4 and 1024mb RAM also quickly takes up 1 to 2 min to completly boot. But is quite fast when it is completly booted.

---

### Post by ugm6hr on 2007-06-20
Sounds like Xubuntu is your choice.  

I now prefer it to Puppy - it just has a more finished look and feel, with readily available packages for Synaptic.  Although Puppy will do everything you want too.  I have had Xubuntu on 128MB machine - it was just a little slow to boot (til I upgraded), but ran OK once loaded (although not as fast as Puppy - which runs in 128MB RAM).

---

### Post by DrRobotnik on 2007-06-20
Ive currently got Xubuntu running on a 300mhz laptop with 160mb of ram.. I would suggest playing around with the hdparm command to speed up the hard drive access otherwise it will feel really slow, Heres a good tutorial..

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)

---

### Post by SoloSalsa on 2007-06-20
Yes, 192 is all that is needed for live install.  Alternate install will run with 128, I think.  Anyway, it sounds like it will work, just fine.  Is there anything valuable in storage?  You should back that up before committing to installation.  And, don't forget, you could always just use the live disc to see if hardware is supported.  If it works live, it should definitely work installed.

---

### Post by Golyadkin on 2007-06-20
Yeah, for me the speed of the computer running the live distribution was nothing compared to the superspeed I got after installing Ubuntu 64 bits edition though. I was even wondering about installing Ubuntu when I felt the live-cd was sluggish. The real install turned out to be faster than any Windows version I ever ran :D

---

