---
title: "New to Ubuntu, need some tips"
date: 2011-10-14
forum: Apple Hardware Users
---

### Post by eyedrinkvenom on 2011-10-14
I'm a graphics/music professional and have been using Mac for almost 20 years (with a few stints in Windows that still make me nauseous). I love the openness of the architecture of these OSs and I'm hoping to convert over my entire production pipeline eventually.

I'm currently running 64-bit Ubuntu on an 8-core 2008 model Mac Pro with 32GB RAM (just installed it). It runs really fast (short of the internet connection being much slower) but a few things I'm trying to figure out I hope you can help me with.

1) How can I map my Mac command key so it acts like the control key? I cannot use control. It's too awkward for my hand.

2) Some apps (Banshee, Skype) do not show window bars for dragging. Why is this?

3) How do you enable the draggable window wobble? Is it an additional install? I have OGL Cairo and Emerald installed already. It's not a necessity but looks pretty badass.

4) Is it safe to work and save files back and forth from the HFS+ volumes I have? I don't want to screw up my files.

5) What are some need-to-have security apps and settings for hardening? I use Virus Barrier X6 on Mac so I can allow all connections I want and stop all the rest. 

Thanks, and look forward to learning and using GNU/Linux OS.

---

### Post by WasMeHere on 2011-10-14
Welcome to the Ubuntu Forums eyedrinkvenom,

I might be able to help you with some tips, and other people can help you with 'everything else', as long as you are patient enough. There might be some trial and error before you feel quite comfortable with the different style and logic of the desktop environment and the new applications. I'll be back ...

Have fun finding out about Ubuntu :-)
Olle

---

### Post by eyedrinkvenom on 2011-10-14
Thanks Olle

Looking forward to your info.

---

### Post by WasMeHere on 2011-10-14
> **eyedrinkvenom said:**
> I'm a graphics/music professional and have been using Mac for almost 20 years (with a few stints in Windows that still make me nauseous). I love the openness of the architecture of these OSs and I'm hoping to convert over my entire production pipeline eventually.

I'm currently running 64-bit Ubuntu on an 8-core 2008 model Mac Pro with 32GB RAM (just installed it). It runs really fast (short of the internet connection being much slower) but a few things I'm trying to figure out I hope you can help me with.

1) How can I map my Mac command key so it acts like the control key? I cannot use control. It's too awkward for my hand.

2) Some apps (Banshee, Skype) do not show window bars for dragging. Why is this?

3) How do you enable the draggable window wobble? Is it an additional install? I have OGL Cairo and Emerald installed already. It's not a necessity but looks pretty badass.

4) Is it safe to work and save files back and forth from the HFS+ volumes I have? I don't want to screw up my files.

5) What are some need-to-have security apps and settings for hardening? I use Virus Barrier X6 on Mac so I can allow all connections I want and stop all the rest. 

Thanks, and look forward to learning and using GNU/Linux OS.

Before linux I had experience of old minicomputers and workstations VAX/VMS, unix, DOS and Windows. I have not used Macs very much, but I have run a live Ubuntu system on a powerpc iMac and there were no problems with file read/write.

0. What internet connection are you using, what is your speed and what do you expect?

4. *I think it works well*. But the general recommendation applies: Make sure you have a recent backup (make backups according to a regular schedule)! Particularly when you use new tools, you might do something wrong.

5. *Browse the internet searching for linux and security!* I guess you have a router that is also a firewall. Personally I don't use any antivirus tool in linux, but I have friends who do.

---

### Post by eyedrinkvenom on 2011-10-14
I have a cable model. I get a max of 3.5MB/sec download (yes, megabyte), this does depend on the server being accessed. Most sites I get between 750k-1.5MB/sec. In Ubuntu I have seen 200-300k/sec. This might just be the servers that hold the software are slow, but it seemed consistent no matter what I was downloading.

I'm actually not using a router right now. I need to get a new one with NAT capabilities.

---

### Post by WasMeHere on 2011-10-14
My experience is that wired internet works out of the box at full speed in Ubuntu. The Ubuntu servers might be heavyly loaded now, because the new version 11.10 was released recently. Try some other webside!

Run the command ```
sudo lshw > lshw.txt
``` and read the section about network (it should look something like this)
```
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 7
             bus info: pci@0000:01:07.0
             logical name: eth1
             version: 10
             serial: 00:19:e0:0d:00:95
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: irq:19 ioport:e800(size=256) memory:dffffc00-dffffcff memory:dffc0000-dffdffff(prefetchable)
``` Is your ethernet connector working at full speed (in my case 100 Mb/s although it says 100MB/s)?

Concerning firewall: There is a firewall, that you can make active and tweak in Ubuntu via *ufw*, [[COLOR="RoyalBlue"]_http://help.ubuntu.com/community/UFW_[/COLOR]]("http://help.ubuntu.com/community/UFW"), so if you need no router, you can use that one instead.

---

### Post by WasMeHere on 2011-10-14
> **eyedrinkvenom said:**
> ...
1) How can I map my Mac command key so it acts like the control key? I cannot use control. It's too awkward for my hand.

2) Some apps (Banshee, Skype) do not show window bars for dragging. Why is this?

3) How do you enable the draggable window wobble? Is it an additional install? I have OGL Cairo and Emerald installed already. It's not a necessity but looks pretty badass
...
If you get no replies soon concerning questions 1-3, I suggest that you make new threads with *titles describing what you want*.

---

### Post by eyedrinkvenom on 2011-10-14
I'm on the Mac side now I'll check it out in a few. And I'll post those if no answers come.

thanks

---

### Post by eyedrinkvenom on 2011-10-14
I'm in Ubuntu now. When I execute that command, The next line just says PCI (sysfs) and then the command stops running after a few seconds and takes me to a new prompt. No network info comes up.

The Terminal also doesn't have a window bar. I had to Alt+drag to move it.

---

### Post by WasMeHere on 2011-10-14
The info is in the file [FONT="Arial Black"]lshw.txt[/FONT] Read it with an editor, for example gedit ```
gedit lshw.txt
```

---

### Post by Bucky Ball on 2011-10-14
If you are running 11.** perhaps try something more stable and you might find many problems fixed. You may be interested in Ubuntu Studio [http://ubuntustudio.org/](http://ubuntustudio.org/). 

I go for the long-term support releases, 10.04 LTS being the current one, which are designed for production machines - as yours seems to be - and servers.

---

