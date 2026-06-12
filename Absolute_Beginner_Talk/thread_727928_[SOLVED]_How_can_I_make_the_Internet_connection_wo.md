---
title: "[SOLVED] How can I make the Internet connection working on nForce 6 ?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Pierrot Lafouine on 2008-03-18
Hi

I must honestly says that it's my first time with Linux, I installed Ubuntu 7.10
It went well, except I don't know how to connect to internet.

Look likes it's missing an Ethernet driver,
How can I see if the Ethernet driver is installed ?

If I need to install a driver, where can I get it ?
Motherboard's CD doesn't have any Linux driver.
And BFG don't support Linux (what a shame)

Help, I fell so lost in this completely new world...

Motherboard manufacturer : BFG 
Motherboard model : 680i-LT (nForce 6 chipset)
CPU : Intel Dual core

Cheers!

---

### Post by Ub1476 on 2008-03-18
Post the command of:

```
lspci | grep Network
```

(This will show what Ubuntu recognize as the network controller)

---

### Post by Pierrot Lafouine on 2008-03-18
> **Ub1476 said:**
> Post the command of:

```
lspci | grep Network
```

(This will show what Ubuntu recognize as the network controller)

Hi
Thanks for the quick response
Nothing happen to the command 
```
lspci | grep Network
```

I tried 
```
lspci
``` and saw the list of installed hardware.
Ethernet was in the list but no Network.
What is the next step ?
Thanks,
PL

---

### Post by halitech on 2008-03-18
can  you post the output of lspci so we can see what you do have

---

### Post by Delkster on 2008-03-18
> **Pierrot Lafouine said:**
> t of installed hardware.
Ethernet was in the list but no Network.

If it's a wired connection, the ethernet one is probably the one we're looking for. Could you post the details of that line here?

I don't personally know about latest nForce chipsets or their support in Linux but the information might help someone else give you guidance.

On my machine, the wired ethernet controller shows up as "ethernet" on the list while the wireless chip appears as "network controller".

---

### Post by Ub1476 on 2008-03-18
Ethernet should work - always.
Network is wireless, if it doesn't show (it obviously didn't), you don't have the driver for it installed.

If you don't get any connection through Ethernet, post the output of:

```
lspci | grep Ethernet
```

---

### Post by Pierrot Lafouine on 2008-03-18
Hi
Got an image of the result of command lspci:

[IMG]http://img.photobucket.com/albums/v396/PierrotLafouine/Divers/Lspci-1.jpg[/IMG]

Thanks

---

### Post by Pierrot Lafouine on 2008-03-18
This is the response to the command :
```
lspci | grep Ethernet  
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
```

This is the response to the command :
```
lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

What is the next step to fix the Internet connection ?
Thanks, Cheers!
PL

---

### Post by Pierrot Lafouine on 2008-03-18
What command can I try to see what's wrong with my Internet connection ?

Thanks,
PL

---

### Post by Xiong Chiamiov on 2008-03-18
I'm assuming that you know this machine works under a different operating system, and/or that you can connect with this cord to this port on your router (or just into the wall).
Is it simply that you can't access something in Firefox, or have you tried multiple applications?

---

### Post by Xiong Chiamiov on 2008-03-18
> **Pierrot Lafouine said:**
> What command can I try to see what's wrong with my Internet connection ?

Thanks,
PL

You can post the output of ifconfig

---

### Post by Pierrot Lafouine on 2008-03-18
> **Xiong Chiamiov said:**
> I'm assuming that you know this machine works under a different operating system, and/or that you can connect with this cord to this port on your router (or just into the wall).
Is it simply that you can't access something in Firefox, or have you tried multiple applications?

You are right.  WinXP-SP2 works fine.
I have Linux installed on the same machine on different HDD, but not able to connect to Internet with Firefox.  What other application shall I try ?
I tried to ping the wired modem, no success

Cheers!

---

### Post by Xiong Chiamiov on 2008-03-18
Post the output of
```
ifconfig
```

and check if you can ping any websites.

---

### Post by Pierrot Lafouine on 2008-03-18
This is the output of ifconfig:

eth0 
Link encap:Ethernet  HWaddr 00:04:4B:03:24:EE  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3595 (3.5 KB)
          Interrupt:17 Base address:0xe000 

eth0:avah 
Link encap:Ethernet  HWaddr 00:04:4B:03:24:EE  
          inet addr:169.254.5.218  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 

lo       
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


By the way, I tried to ping the modem under Windows and doesn't answer either...
What is the next step ?
Create a broadband connection ?

Thanks!

---

### Post by Pierrot Lafouine on 2008-03-18
What is the next step ?
Create a broadband connection ?
Maybe it's the only thing I need to do to have access to Internet ?

---

### Post by Pierrot Lafouine on 2008-03-18
Please what is the next step to get Internet working ?
Thanks,
PL

---

### Post by Pierrot Lafouine on 2008-03-18
up

---

### Post by Pierrot Lafouine on 2008-03-18
up, please,
I'm looking forward to surf and response to this forum with Ubuntu

---

### Post by Neo0351 on 2008-03-18
can you ping [www.google.com?](www.google.com?)

---

### Post by Neo0351 on 2008-03-18
If you can't, try this

```
sudo modprobe forcedeth
```

I think this is the module for you ethernet card

---

### Post by Pierrot Lafouine on 2008-03-18
Output of 
```
ping www.google.com
```
is : unknown host

There were no output for the command 

```
sudo modprobe forcedeth
```

Question :
Do I have to install a driver for ethernet card ?
If so, I have not done it

Do i have to create a broadband connection ?
If so, I have not done it, and I don't know how.

Sorry, I'm beginner...!!!

---

### Post by Pierrot Lafouine on 2008-03-18
Output of 
```
ping www.google.com
```
is : unknown host

There were no output for the command 

```
sudo modprobe forcedeth
```

Question :
Do I have to install a driver for ethernet card ?
If so, I have not done it

Do i have to create a broadband connection ?
If so, I have not done it, and I don't know how.

Sorry, I'm beginner...!!!

---

### Post by Neo0351 on 2008-03-18
Ok, modprobe forcedeth should have loaded you driver.  Try pinging google again

---

### Post by Pierrot Lafouine on 2008-03-18
> **Neo0351 said:**
> Ok, modprobe forcedeth should have loaded you driver.  Try pinging google again

Output of
```
sudo modprobe forcedeth
ping www.google.com
```

is : unknown host

Do I have to enable DHCP stuff ?
Do I have to install driver ?
Do I have to create Broadband connection ?

Thanks,
PL

---

### Post by Delkster on 2008-03-18
> **Pierrot Lafouine said:**
> Do I have to enable DHCP stuff ?
You shouldn't have to. DHCP is used by default.

> Do I have to install driver ?
Usually not. That's what we were trying to find out when asking for the output of lspci.

As far as I can tell, the driver that should support your ethernet chip is "forcedeth" (as Neo0351 also said), which comes with the system and doesn't need to be installed separately.

> Do I have to create Broadband connection ?
If you use DHCP over ethernet, you shouldn't have to manually create any kind of a connection.

Can you try entering the following command after running "sudo modprobe forcedeth"?
```
sudo /etc/init.d/networking restart
```

Judging by the output of ifconfig it seemed that the driver is loaded but for some reason you aren't getting an IP address over DHCP. The command mentioned above brings networking down and back up, and should also try again for an IP address.

When run explicitly from the console, it also gives a lot of output. Could you post that output here?


Edit: I should also mention that the command may take a while to finish, especially if it can't seem to find a DHCP server. Just wait patiently for it to finish. At some point it should either tell you the IP address it got or give a message that there are no DHCP leases available.

---

### Post by Neo0351 on 2008-03-18
Sorry, this is out of my league, but it appears to be possibly a bios problem.  Here's a thread that might help.

[http://ubuntuforums.org/showthread.php?t=303341](http://ubuntuforums.org/showthread.php?t=303341)

---

### Post by ugm6hr on 2008-03-18
Please confirm some basic information.  Your ethernet is not currently actively connected to anything.

Sounds like you have a broadband connection.  If this is not true, let us know.

You say Windows XP works - but can you get online from XP?

How do you connect to the internet?  Do you have a modem, or modem-router setup?  If you don't understand the difference, please let us know what the brand / model number of your modem is, ideally with a link to the online manual.

Have you input your ISP details into the modem directly?  If not, do you know how?

One last thing - post the output from the following command (case sensitive - i.e. C not c):
```
lshw -C network
```

---

### Post by Pierrot Lafouine on 2008-03-18
I have hi speed internet
Wired internet modem is SpeedStream 5200, and look likes there is no micro code in it (it doesn't response to ping 192.168.2.1).  Not exactly sure how I can know if there is a router etc...
I have WinXp SP2 on one HDD
I have Linux Uguntu 7.10 on a second HDD
Both disk on same computer.
I'm writing on this forum with WinXp, so yes I can get online with SpeedStream 5200 and WinXp.  I have to kind of dialup before connecting to internet under WinXp.
I don't think my ISP settings are stored in modem.

I will provide the output of the command in few minutes (I have to reboot)

Cheers!

PL

---

### Post by ugm6hr on 2008-03-18
OK.

You have an ethernet modem (but not modem-router).

I think you have to use pppoeconf to "sort of dial-up" in Ubuntu...

Unfortunately, I don't know how to do that.

This might help: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

PS: The lshw -C network command will confirm that the ethernet card has a driver installed properly.

---

### Post by IsawSp4rks on 2008-03-18
Maybe the modem is attached to your PC via USB?  That would explain the issue.

Have you tried USB Modem Manager?  It's ot guaranteed to work, but certainly might help in debugging the problem.

[http://ubuntuforums.org/showthread.php?t=585647](http://ubuntuforums.org/showthread.php?t=585647)

---

### Post by Pierrot Lafouine on 2008-03-19
there is no output when I write command
```
lsh -C network
```

I also tried 
```
lsh -C Network
```
No output either.
 What is the next step ?

Thanks,
PL

---

### Post by ugm6hr on 2008-03-19
> **Pierrot Lafouine said:**
>  What is the next step ?


Read my post again:

```
lsh**w** -C network
```

---

### Post by Pierrot Lafouine on 2008-03-19
sorry, typo,
I tried :
```
lshw -C network
```
No output

I also tried 
```
lshw -C Network
```
No output

Does it mean there is no driver install for the network ?

Thanks,
PL

---

### Post by ugm6hr on 2008-03-20
> **Pierrot Lafouine said:**
> Does it mean there is no driver install for the network ?

I think that ethernet should work.

The fact that eth0 exists means it appears to be detected.

I think it is also supported in the Linux kernel.

However, it is listed as "Bridge" rather than "Network" or "Ethernet" controller in lspci.  Not sure if that matters.

Perhaps it is listed in a different class in lshw.

Try this:
```
lshw -short
```

Post the results here.

EDIT:
[http://www.hardwaresecrets.com/article/84](http://www.hardwaresecrets.com/article/84)

This looks interesting.  It suggests that this modem *can* work as a router.  I would suggest you look into this, because it will:
1. Improve security (in Windows and Ubuntu)
2. Mean you don't have to "dial-up"
3. Make things much easier in general.
4. You should not have to set anything up in Ubuntu.

But please make sure you know what you are doing (maybe print out the instructions pages 1-3) before you do the upgrade, since you may lose your connection until you have set it up again.

And the admin page is [http://192.168.254.254/](http://192.168.254.254/)

---

### Post by Pierrot Lafouine on 2008-03-29
I succeeded to surf on the web last week.
I followed these instructions :
[http://ubuntuforums.org/showpost.php?p=567725&postcount=12](http://ubuntuforums.org/showpost.php?p=567725&postcount=12)

I thank you all for your help.

:guitar:

---

