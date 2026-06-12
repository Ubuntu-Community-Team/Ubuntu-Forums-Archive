---
title: "How do I get my D-Link DWL-G510 to work?"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Incompl on 2006-10-08
I'm using 6.06, and I have no clue how to get it to work.


I tried to find out for myself, but the results were full of things I didn't understand.

---

### Post by The Mekon on 2006-10-08
The DWL-G510 comes in a couple of versions.  If it uses the Atheros chip set it should just work.

In a terminal enter 'lspci'.  I get:

brian@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chi pset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:01:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0 01a (rev 01)
brian@ubuntu:~$

You will see that my wireless card has an Atheros chip set.

If you have this select:
System/Administration/Networking and, after entering you Password, you should see your a Wireless Connection area.

Select it and select Properties to set up you ESSID, WEP Key(if any) and Enable it.  After clicking OK you should soon be online.

Of course is you dont have and Ateros chipset it is another story and search for help on ndiswrapper.

Brian

---

### Post by KeyDesignz on 2007-02-13
I have the exact same card on my machine. I have done this time and time again, it sees my network, but I can't get it connected. It just seems to forget the settings and won't let me get online. Any suggestions? I am running Ubuntu 6.06.

---

### Post by OldGaf on 2007-02-19
> **KeyDesignz said:**
> I have the exact same card on my machine. I have done this time and time again, it sees my network, but I can't get it connected. It just seems to forget the settings and won't let me get online. Any suggestions? I am running Ubuntu 6.06.

Mine worked in Edgy with the x.x.x.10 kernel. Now I have upgraded to x.x.x.11 and it will not connect. It is detected, just will not get an IP from the router.

---

### Post by TekMuzik on 2007-02-19
> **OldGaf said:**
> Mine worked in Edgy with the x.x.x.10 kernel. Now I have upgraded to x.x.x.11 and it will not connect. It is detected, just will not get an IP from the router.

Same thing for me. Except mine isn't even detected anymore.

---

### Post by lreyes6 on 2007-02-19
maybe it's not the best solution but maybe you can get it to work witn **ndiswrapper** and the drivers for windows :D 

That's the easy way... i use to have a DWL-G650+ and it was a real pain to get it to work... at the end I replace the card.

---

### Post by OldGaf on 2007-02-20
> **TekMuzik said:**
> Same thing for me. Except mine isn't even detected anymore.

Sorry..... I was seeing my other nic :oops:  ..... is was a LONG day!

G510 has completely gone. I blew everything away today and started over. The install CD saw the G510, after I booted it could still see it. Once I upgraded to 2.6.17-11-generic it was gone again!

The real problem I have is that I need the latest drivers from Nvidia and they need nvidia-kernel-source which is........ 2.6.17.7-11.1

---

### Post by OldGaf on 2007-02-20
OK, I got my D-Link DWL-G510 (Atheros chipset) to work again under 2.6.17.11. It seems that 2.6.17.10 had built in madwifi support in the restricted modules that are eather missing or are broken in -11.

The solution was to get the MADWIFI driver and compile it under -11. 
It is very simple to do, just follow these instructions.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

If you do not have an Atheros chipset, try ndiswrapper (NOT the one in the repos....... get 1.37 and compile it.) Here is a simple set of instructions.

**NOTE: At this time 1.37 is the latest ndiswrapper. You will also have to change the Winblows driver for the one that matches your card.

[http://www.ubuntuforums.org/showthread.php?t=342558](http://www.ubuntuforums.org/showthread.php?t=342558)

BTW...... This is a BIG pi$$ off and a pain in the @$$ to have to do. This should have been picked up on before the release of -11.

---

