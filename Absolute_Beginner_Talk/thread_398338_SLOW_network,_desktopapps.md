---
title: "SLOW network, desktop/apps"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by msfisher on 2007-03-31
I've finally managed to get Ubuntu 6.1 installed (long story, not for this thread), but I've got two big problems.

First, all of my network connections are VERY SLOW.  This is for web browsing AND updates/add-remove programs/Synaptic.  I had exactly the same problem with Mandriva 2006 & 2007 (in fact, it's the reason I decided against using it).  I have NOT had this problem with either Windows 98 or Xandros 3.0.  Using the download package monitor, I've gotten speeds no higher than 18KBps and as low as 700Bps – yes, less than a kilobyte – with an average of about 6 or 7KBps.  I usually get ten to twenty times that much and have broken 1000KBps!  The basic update set took four hours.  Google takes thirty seconds to load its bare main page!  I haven't been able to see the other (Windows) computers on my home network yet, so I can't say if the problem exists “intranet” as well.  I've read here and on both the newsgroups and at least one mailing list about the problem, but the answers (such as they are) don't seem helpful.  I have a triple-boot system (Win98SE, Xandros & Ubuntu 6.1 installed using the Alternate CD) with a Realtek 8139 (I think) NIC on the motherboard, through an SMC wired/wireless router.  I've set it up to do DHPC with the router as Gateway and as the local network host (192.168.2.1 for the SMC).  I understand that ipv6 should be disabled, but I still have entries for it under Network Settings-Hosts. How do I shut it off in Ubuntu (I'm looking around right now, too)?  I notice that under Services Settings, Multicast DNS services discovery is not checkmarked.  Part of the problem?  I've also seen it suggested that using an older kernel is the solution, along with several different aliasing approaches.  All the reading I've done so far seem to suggest  that ipv6 isn't the only source of the problem.  Any other ideas?

The second problem is that, when I first start Ubuntu, ALL of the applications, from GNOME load onward are EXTREMELY SLOW.  Really, two minutes to load gedit and another two to open a file.  In addition, when I open a terminal, it doesn't actually start.  Instead, I have to minimize it, open something else like a disk access, then close it and restore the terminal.  As I use the system, the problem goes away, ergo it's just something at boot.   

Thanks in advance for any help on either problem.

---

### Post by dstew on 2007-04-01
To shut off your network in Ubuntu, use the command

ifdown eth0

if it is the eth0 interface you want to turn off.

I think all your slowness might be due to your network issues. Your network issues are no doubt due to software problems. Maybe the driver is not correct, or your configuration is not correct.

To start, let's look at the output of your **lspci** command to see what the card name is. Then, do **ifconfig -a** to see what interfaces are present, and whether they are running or not.

---

### Post by csleech on 2007-04-01
I just installed xubuntu and have the same problem... I ran ifconig -a like you suggest and the following is what it shows... I am new to linux so I don't have a clue what it means...

~eth0      Link encap:Ethernet  HWaddr 00:04:61:71:52:40  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:61ff:fe71:5240/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7700443 (7.3 MiB)  TX bytes:508169 (496.2 KiB)
          Interrupt:177 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8123 (7.9 KiB)  TX bytes:8123 (7.9 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
~

Any help is greatly appreciated....

To verify that it isn't my internet and is an issue with the linux install, I did a bandwidth test and get 2MB PS on my windows box and get only 250K PS on the linux box....

THANX!

---

### Post by msfisher on 2007-04-01
>To shut off your network in Ubuntu, use the command
>
>ifdown eth0
>
>if it is the eth0 interface you want to turn off.

Now why would I want to do that??? 

>I think all your slowness might be due to your network issues. Your network issues >are no doubt due to software problems. Maybe the driver is not correct, or your >configuration is not correct.

If the driver you mean is the one in Ubuntu, then I suppose it's possible, though I expected Ubuntu to spot it properly.  Remember from my first post that this ONLY occurs in Ubuntu and, when I had it installed, Mandriva 2006 & 2007.  NOT Xandros (Debian based like Ubuntu) and NOT Win98SE.

>To start, let's look at the output of your lspci command to see what the card name >is. Then, do ifconfig -a to see what interfaces are present, and whether they are >running or not.

02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139

Just like I said in my post.

eth0      Link encap:Ethernet  HWaddr 00:13:D3:9E:28:0D  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe9e:280d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1324 errors:2 dropped:2 overruns:1 frame:0
          TX packets:1294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:932928 (911.0 KiB)  TX bytes:194411 (189.8 KiB)
          Interrupt:15 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

If I read this right, it is running.  I notice both errors, drops and overruns, though.

---

### Post by Austin_KW on 2007-04-01
You might try disabling ipv6; seems to sause problems for some

 gksudo gedit /etc/modprobe.d/aliases
and change the ipv6 line to "alias net-pf-10 off #ipv6"

---

### Post by msfisher on 2007-04-04
Tried it.  Didn't help.  Still slow/strange on startup -- get wallpaper, then long wait, then top & bottom panels with no icons, wait, get icons (not active), wait, icons activate but some applications don't run properly, wait, applications finally work right but network still slow.  I'll look around here some more, but any help -- even just pointing me to a thread -- would help.

---

### Post by oilchangeguy on 2007-04-04
if your computer was born with 98, it probably just barely meets the requirements to run 6.10. please advise your computers specs.

---

### Post by msfisher on 2007-04-04
The system has LONG since been upgraded beyond 98's original requirements.  However,

AMD Sempron 2600
512megs PC2700 memory
Realtek 8139 NIC
AC 97 sound
GeForce 3 250 chipset
Nvidia video, don't remember model but 64megs ram

I am having this problem ONLY with Ubuntu.  I'm only a newbie to Ubuntu -- my system is a triple-boot Win98SE (no problems), Xandros 3 (no problems, don't flame me) and Ubuntu 6.10.  I saw the slow network with Mandriva 2006 & 2007 (why I ditched it in favor of Ubuntu).  I had to install from the alternate CD because I kept hitting a mount point bug (reported and confirmed) in Ubiquity and had to log in initially as OEM.  THAT login worked just fine except for the slow network.  The desktop/app problem is new since adding myself as a user.  I've seen another thread or two where the problem was seen with Feisty beta, but not with Edgy.

---

### Post by oilchangeguy on 2007-04-04
i've also used xandros 3.0 oce, it's not bad. i've got to ask however, what's the point in having 3 os's, other than just to say you did it?

---

### Post by msfisher on 2007-04-05
To try them out and learn about them.  All OS's and distros have strengths and weaknesses.  The only way to see if one particular one is best for my needs.  Plus, it's fun to try out new systems, even if getting to the point of fully using one is a pain.  Besides, in going through the frustration, I can both learn about the OS and evaluate it at the same time.  I'm even thinking about trying out BeOS and ReactOS.  There are a couple of more out there that sound interesting also, including the Mac OS.

---

### Post by velocity303 on 2007-04-05
I am also having a similar problem, where my network connection has gotten considerably slower. I am connected through a college LAN, and almost everything I do on the internet is considerably slower. I never had this problem with previous installations of ubuntu, only in the fiesty beta. Does anyone know if it is simply the fiesty beta causing these problems?

I have a nforce4 motherboard
amd 3200+
2gb of ram

To me it seems like some type of driver issue, but ubuntu never had this kind of problem before so it is rather confusing.

---

### Post by drizzt on 2007-04-29
Did anybody solve this problem?

I've got an nforce4 motherboard and the last Ubuntu version having network is Dapper, Edgy and Feisty have same problems.

Thanks in advance,
drizzt

---

### Post by drizzt on 2007-04-30
In this period I'm studying the problem and it seems that is related to the firewall integrated in the nforce4 motherboards.

Unfortunately I think that we can't do anything because the problem can be solved just at a kernel level.

I would like to have a geek opinion.

Thanks,
drizzt

---

