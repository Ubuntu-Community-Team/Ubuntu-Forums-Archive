---
title: "Newbie's last hope"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by Goonie on 2006-03-26
Hello all

I've been struggling with a problem for a long time now and I haven't been able to get the help I need so I've gone back to using Windows. So now I ask for help from you guys so I can start using my Ubuntu again. Here it is. I'm using an Acer laptop with a dual boot setup and when I boot up in Ubuntu I can't get wireless to work. Everything looks normal. I can scan for networks, I get an ip address but the connection doesn''t work. I can't even ping the router let alone addresses outside my LAN. The hardware is working fine since the Windows setup doesn't have a problem. I also had Ubuntu 4.10 installed before and that worked fine, upgraded to 5.04 and the wireless got shaky and then when I upgraded to 5.10 it stopped working completely. From what I've gathered this is a problem with the firmware on the Intel 2200 wireless card and the default ipw2200 driver bundled with Ubuntu. I think I either need to upgrade the firmware on the wireless card or stop using the ipw2200 driver completely and try ndiswrapper again. Now I am a complete newbie and I need things spelled out for me so if anyone can tell me how to upgrade the firmware (step by step) or how to remove the ipw2200 driver from my system so I can install ndiswrapper instead, I would greatly appreciate it. I've run out of ideas... Except for maybe buying a new laptop but that's a bit extreme. I hope you guys can help. 

Kind regards,
Gunnar Freyr

---

### Post by eriefisher on 2006-03-26
There is a good article on the "Ubuntu Documents Storage Facility" about this. Sorry but I don't have the link off hand but look at some of the signatures for a USDF link.

eriefisher

---

### Post by Sef on 2006-03-26
> 25) Installs ndisgtk (WiFi configurator Graphical user interface) 

That is installed by automatix.  See this link for download instructions:

[http://ubuntuforums.org/showthread.php?t=138405&highlight=ndiswrapper]("http://ubuntuforums.org/showthread.php?t=138405&highlight=ndiswrapper")

---

### Post by xtacocorex on 2006-03-26
Here is the link to the Ubuntu Documents Storage Facilty: [http://doc.gwos.org/](http://doc.gwos.org/)

---

### Post by Goonie on 2006-03-26
Hi and thanks for your replies. I will try what you suggested as soon as I get to a wired connection. I will let you know how it goes :=)

Gunnar Freyr

---

### Post by Goonie on 2006-03-29
Hi all

Well I tried looking for how-to docs and found one and I followed it to the letter. Sadly it resulted in the ipw2200 module not loading at all.  There are a lot of references in dmesg (not sure if I can post long error outputs in this forum) to ieee80211 and ipw2200 disagreeing with a bunch of stuff. So here is what I'm going to try befor I give up on using ubuntu on my laptop. I replaced the WL card with a new Intel 2200 card (the same as the old one but with a much newer manufacturing date) and I'm going to try a reinstall of Ubuntu and see if that does the trick. But now I have a new problem.... How do I reinstall Ubuntu on this dual boot laptop safely so that my Windows doesn't get screwed up. Any suggestions there?

Thanks for the help guys
Gunnar

---

### Post by Sandlst on 2006-03-29
Please log into Ubuntu, then in a terminal type ```
gedit /etc/fstab
``` copy and paste the resulting text file into a reply on this thread, this will allow us to give you the exact partitioning scheme to use in the installer.

---

### Post by Sef on 2006-03-29
> How do I reinstall Ubuntu on this dual boot laptop safely so that my Windows doesn't get screwed up. Any suggestions there?

**Back up** your data first.  There is no 100% guarantee that either you will make a mistake or something will destroy your Windows partition(s). However, almost always, you can successfully reinstall Ubuntu.

When I had a dual boot and needed to reinstall Ubuntu, I would delete all the partitions except for the Window partition(s) and /home.  Then I would create the partitions again.  There were 3 of them: Fat32, root and swap.

If you would like some more info, let me know, and I will write down in more detail what to do.

---

### Post by Goonie on 2006-03-30
I will make an image of my hard drive today for backup purposes and give the reinstall a try tonight. I will also post my fstab tonight.

To make things simpler I don't even need to keep my /home since I haven't really gotten Ubuntu to work for my there is nothing in there of value.

I'll keep you posted and thanks again.

Gunnar Freyr

---

### Post by davidmoore83 on 2006-03-30
[QUOTE=Goonie]Hello all

I've been struggling with a problem for a long time now and I haven't been able to get the help I need so I've gone back to using Windows. So now I ask for help from you guys so I can start using my Ubuntu again. Here it is. I'm using an Acer laptop with a dual boot setup and when I boot up in Ubuntu I can't get wireless to work. Everything looks normal. I can scan for networks, I get an ip address but the connection doesn''t work. I can't even ping the router let alone addresses outside my LAN. The hardware is working fine since the Windows setup doesn't have a problem. I also had Ubuntu 4.10 installed before and that worked fine, upgraded to 5.04 and the wireless got shaky and then when I upgraded to 5.10 it stopped working completely. From what I've gathered this is a problem with the firmware on the Intel 2200 wireless card and the default ipw2200 driver bundled with Ubuntu. I think I either need to upgrade the firmware on the wireless card or stop using the ipw2200 driver completely and try ndiswrapper again. Now I am a complete newbie and I need things spelled out for me so if anyone can tell me how to upgrade the firmware (step by step) or how to remove the ipw2200 driver from my system so I can install ndiswrapper instead, I would greatly appreciate it. I've run out of ideas... Except for maybe buying a new laptop but that's a bit extreme. I hope you guys can help. 

Kind regards,
Gunnar Freyr[/QUOTE]

Goonie,

I reccomend using #ubuntu IRC channel. 7 hours on that has sorted linux problems i could never understand in months! I have also learnt alot in those 7hrs.

---

### Post by Goonie on 2006-03-30
Ok now I really am frustrated!

I replaced the Intel 2200 wireless netcard and reinstalled Ubuntu and still the same problem. I've been trying to get help in the irc channel but sadly to no avail. I will have to try a different distro until there is a new Ubuntu release or I buy a new laptop. Thanks for all your help, I really appreciate it.

Gunnar Freyr

---

