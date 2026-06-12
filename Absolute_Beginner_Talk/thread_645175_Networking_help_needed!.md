---
title: "Networking help needed!"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Rusty023 on 2007-12-19
Help, someone! I'm a complete and utter noob at Linux and Ubuntu, I've got dual boot of Vista and Ubuntu, and I can't set up a network connection. Vista just automatically picks up the network plug in the computer, but Ubuntu can't find it, and I don't know the technical details of the connection. Can someone please help me?

While I'm posting, I have another problem. I wanna drag and drop a file from a CD to the root directory to install a driver, but it says I don't have access. I used a net tutorial to enable root access in the command prompt, but I don't know how to use it, so that doesn't help anything. Help is needed!

I hope you guys can help me! Thanks in advance.

---

### Post by fatsheep on 2007-12-19
> **Rusty023 said:**
> Help, someone! I'm a complete and utter noob at Linux and Ubuntu, I've got dual boot of Vista and Ubuntu, and I can't set up a network connection. Vista just automatically picks up the network plug in the computer, but Ubuntu can't find it, and I don't know the technical details of the connection. Can someone please help me?

While I'm posting, I have another problem. I wanna drag and drop a file from a CD to the root directory to install a driver, but it says I don't have access. I used a net tutorial to enable root access in the command prompt, but I don't know how to use it, so that doesn't help anything. Help is needed!

I hope you guys can help me! Thanks in advance.


Try running [code]gksudo nautilus[/quote] and then moving the file.  Be careful though, this is the file browser running in super user mode so if you delete important system files then you could mess up your system.  

About the networking problem.  I'm not sure what you're running into but you could try the [guide I used](http://ubuntuforums.org/showthread.php?t=202605).

---

### Post by Joeb454 on 2007-12-19
How are you connecting to your network? Are you using a wired or wireless connection?

And what driver are you trying to install? There may be an easier way than dragging the file from the CD etc. :)

---

### Post by Rusty023 on 2007-12-19
It's a wired connection, to answer your question. That guide doesn't apply, unfortunately, and I'm about to try the code. Oh, and by the way...

you put [code][/quote]. Pretty sure you meant ...might be a noob at linux but I'm not too bad at forums lol

---

### Post by Joeb454 on 2007-12-19
Hmm...ubuntu should pick up the connection automatically.

Are you getting any errors or anything?

There should be a little network icon in the top right (if you installed normal ubuntu) what kind of icon is it showing? If you are connected to a network it'll be 2 monitors

---

### Post by Rusty023 on 2007-12-19
It's a monitor with a yellow sign with an exclamation mark on it, lol. I have the same problem with Windows XP, it does that same thing. This really hurts to say, but...Vista is actually good at something!

---

### Post by Joeb454 on 2007-12-19
Lol, not always. I use Vista as well as Ubuntu (dual booting :)) and it decides to just kill my network connection sometimes.

Is there any other info about the network you can give?

---

### Post by Joeb454 on 2007-12-19
Rusty023,

Can you go to Applications > Accessories > Terminal and type: ```
sudo ifconfig
``` and post the output please?

---

### Post by Rusty023 on 2007-12-19
Hmm...dunno how I'm supposed to do that. Not the command, but posting it. If I type it and copy it, when I restart to go to the internet-enabled Vista I won't be able to paste it, as I've restarted.  I'll go do it anyways, and hope it's not too long.

---

### Post by Joeb454 on 2007-12-19
You can copy it and then save it into a text file :)

Under that same accessories menu I believe there's a Text Editor?

---

### Post by Rusty023 on 2007-12-19
lol, i'm back from linux, and I figured out that text editor would work, so I'm not entirely blonde.

ok, here it is:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by Joeb454 on 2007-12-19
I'm going to assume your using a router?

Either way it's not finding you router/modem, because 127.0.0.1 which it's showing there, is your local machine.

Basically it can't see the router (I'm guessing that, but that's what it looks like)

---

### Post by Rusty023 on 2007-12-19
hmm...but why? I added you on MSN, anyways.

---

### Post by Joeb454 on 2007-12-19
Rusty do you know how to get on IRC?

I don't use MSN much, I really ought to take it off the forums

---

### Post by Rusty023 on 2007-12-19
Yeah, I can get on IRC. What's the server/channel?

---

### Post by Seisen on 2007-12-19
Rusty023 go to System>Administration>Network and click on properties for the network card you are using and tell me what it says.

---

### Post by Rusty023 on 2007-12-19
OK, I'll prolly be back in 5 mins with the details.

---

### Post by Joeb454 on 2007-12-19
Rusty is that all you got when you ran ```
sudo ifconfig
``` because you should have another device (usually eth0) or even eth1.

If these aren't present then Ubuntu hasn't found your network adaptor.

I'll post mine as an example: ```
joe@joe-laptop:~$ sudo ifconfig 
[sudo] password for joe:
eth0      Link encap:Ethernet  HWaddr 00:1B:24:65:D6:6B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:AC:25:43  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:feac:2543/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44103 errors:82 dropped:6995 overruns:0 frame:0
          TX packets:36897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40417160 (38.5 MB)  TX bytes:8758399 (8.3 MB)
          Interrupt:17 Memory:d8000000-d8000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
```

---

### Post by Rusty023 on 2007-12-19
Properties for the network card? There is no network card, just something that says modem switched off. In properties for the modem, it's got all this stuff that I don't think applies to me.

---

### Post by Joeb454 on 2007-12-19
Rusty how do you connect to the internet? I think we need to clear this up before we go any further :)

---

### Post by Seisen on 2007-12-19
open up the terminal (Applications>Accessories>Terminal and type this in it

```
lspci
``` and post what it says.

---

### Post by Rusty023 on 2007-12-19
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
00:0d.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```

So that's the lspci, note with the graphicsy stuff, I'm getting the SiS card removed and a nVidia card put in in a couple of days, as I can't play and decent games with the SiS card.

---

### Post by Seisen on 2007-12-27
Sorry about getting back to you so late but I googled you network card and it looks like it isn't supported as of right now in Ubuntu which would explain why it won' work.

---

