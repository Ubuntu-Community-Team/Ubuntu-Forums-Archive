---
title: "d-link modem driver for linux"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by boobahzone on 2007-12-25
Hi,

I just set up Ubuntu on an old computer and got the system running.  While I was setting up the OS, I did not have internet access.  Now the computer is connected to the internet using an ethernet connection, however I do not have the proper driver for my D-Link DCM-202 cable modem.  After doing a google search and looking on the company tech support site, I've only found drivers for Windows which specifically state that they are not compatible with Linux systems.  Is there a way that I can get the drivers and/or connect to the internet through this modem without having to buy a new one?

Thanks so much!

---

### Post by spiderbatdad on 2007-12-25
might have to configure the modem on a windows computer for dhcp then connect it at your point of use.

---

### Post by boobahzone on 2007-12-25
Thanks spiderbatdad, 

The D-Link modem already works with my computer (this computer) that has Windows on it.  Would I need to do something separately to configure it differently, or since I am connected to the internet already does that mean that I am already configured to dhcp?  

Thanks again

---

### Post by rkd on 2007-12-25
You can easily check to see whether Windows is using DHCP.  If it is, then the modem is providing it.

To check in Windows, open the Network Connections control panel, double click on the Local Area Connection, click the Properties button, in the new properties dialog, scroll down to the line that says Internet Protocol (TCP/IP) and click once on it, click the properties button in that same dialog, a third dialog comes up.  If the "Obtain an IP address automatically" and "Obtain DNS server address automatically" are selected, then Windows is using DHCP.  It is unlikely that anything other than the modem is supplying DHCP, so if Windows is using it, the modem most likely is set up to supply it.

Another way to test would be to boot from the Live CD and see whether it finds the internet connection by itself.  If it does, the modem almost certainly is set up for DHCP.

I think a way you can get your Ubuntu install to connect properly is to use network-admin:
```
sudo network-admin
```
When it opens, in the Connections tab, click once on Wired Connection, then click Properties.  If the Configuration line does not show Automatic Configuration (DHCP), change it until that is selected and click Okay.

Then click the DNS tab and see what it shows for DNS servers.  If there are any listed, make note of the numbers, then use the Delete button to delete them.  Then click the Close button. I'm not really sure about how to deal with the DNS addresses.  The DHCP ought to set them up automatically, but the directions I was reading seem to say you have to put them in manually, which seems wrong.

If the new network settings don't take effect right away, I don't know any way other than rebooting to do it.  Maybe someone else can post better advice on that point.

Try ping google.com and if that doesn't work, try ping 208.67.222.222 to see whether it is just the DNS that doesn't work.  If things aren't working, perhaps posting the results of an ifconfig command would give some clues about what to do next.

EDIT: Found more info: I think the way to restart the network interface without rebooting is to open a terminal and enter these commands:
```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by boobahzone on 2007-12-25
Thanks rkd,

Here's what I did:

When I checked to see if Windows was using DHCP, the "Obtain an IP address automatically" and "Obtain DNS server address automatically" options were selected, so I am assuming this is being supplied by the modem.

I then typed in "sudo network-admin" in the terminal and went to the Wired Connection part where "Enable Roaming Mode" was originally selected, and I had to un-select it so the drop-down menu that contained "Automatic Configuration (DHCP)" was enabled.  I unselected "Enable Roaming Mode" and selected Automatic Configurateion (DHCP).

From there, however, there were no DNS servers listed, so I couldn't really move on from there.  I rebooted and still got the same results.  I entered ping google.com and ping 208.67.222.222, which were both unavailable.

Lastly, I ran ifconfig and here are my results (sorry, I can't copy and paste them so I am trying to re-type them as best as I can):

eth0 Link encap:Ethernet HWaddr 00:80:1E:17:2C:62
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped: 0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 {0.0 b} TX bytes:0 {0.0 b}
Interrupts:20 Base address:0x8c00

eth0:avah Link encap:Ethernet HWaddr 00:80:1E:17:2C:62
inet addr:169.254.3.156 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:20 Base address:0x8c00

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metrick1
RX packets:58 errors:0 dropped:0 overruns:0 frame:0
TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes 5305 (5.1 KB) TX bytes:5304 (5.1 KB)
 
Any ideas?  Thanks so much for any help!

---

### Post by boobahzone on 2007-12-25
> **rkd said:**
> 
EDIT: Found more info: I think the way to restart the network interface without rebooting is to open a terminal and enter these commands:
```
sudo ifdown eth0
sudo ifup eth0
```

Should I do this if I've already rebooted?  (PS: I am super-new to Ubuntu) :)

---

### Post by rkd on 2007-12-25
The ifdown and ifup aren't needed when you reboot.

Two things to try to gather more information:

(1) Post the exact error message you get when you try the command ping 208.67.222.222 

(2) Boot from the live CD and see whether the network works.

If the network does work from the live CD, post the results from the ifconfig command and run sudo network-admin and look around on all the tabs to see what the settings are.  Note them down, then compare them with what you see when you boot Ubuntu from the hard disk and run sudo network-admin.  If there is are differences, tell us  what they are.

If the network doesn't work when booting from the live CD, then maybe you don't have the right driver for your network interface installed.  I guess posting the output from lspci would help figure out what driver to look for.

To save typing, you can copy the text output in the terminal window, paste it into an empty text file in an editor and save the text file on a USB flash drive (or a floppy, if the computer has one).  Then back in Windows, you can get the text from the flash drive (or floppy) to post here in the forum.

---

### Post by boobahzone on 2007-12-25
When I booted from the LiveCD, I still did not get any network connections apparently.  I went through similar steps of your previous post (i.e., Automatic Configuration (DHCP), DNS tab, etc.) and there were still no servers listed.  

_When I ping 208.67.222.222, I get:_
“PING 208.67.222.222 64   56(84) bytes of data
From 169.254.3.156 icmp seq-2 Destination Host Unreachable
From 169.254.3.156 icmp seq-3 Destination Host Unreachable
From 169.254.3.156 icmp seq-4 Destination Host Unreachable” etc and it keeps repeating.

_From the LiveCD, when I lspci I get:_
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:01.0 Communication controller: Conexant Unknown device 2702 (rev 01)
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

[U]
From the LiveCD, when I  ifconfig, I get:[/U]
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7456 (7.2 KB)  TX bytes:7456 (7.2 KB)

…I don’t really know what most of that means.  Still no Ethernet connection.  Thank you so much for any help!

---

### Post by rkd on 2007-12-25
Okay, the network controller is a Realtek 8139, a pretty standard one, if I recall correctly.  We should be able to find a driver for it easily.  I (or someone) will post back after looking up how to get that driver.

---

### Post by rkd on 2007-12-25
Well, it might be that the problem is a bug in the driver for the Realtek 8139.  This thread describes it:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

At first, it was found with 8168 and 8169 controllers, but an update says some users have seen it with 8139 controllers, too.

So to see whether this is the problem you are having, shutdown the computer, pull the power plug out of the A/C socket, wait 15 seconds, put the power plug back in the socket, make sure the ethernet cable is properly plugged in at both ends, then boot Ubuntu (not Windows!).  You could boot either the Ubuntu from the hard disk or the live CD.

If the network connection starts working, then the workaround is to boot Windows and configure the Wake on LAN after Shutdown feature of the network controller, as mentioned in the thread mentioned above.

If the network connection does not start working after this test, you have some other problem.  Post your results and I'll look for other explanations.

---

### Post by boobahzone on 2007-12-25
Thanks rdk.

I should mention that the computer with the non-working internet issues only boots to Ubuntu.  It is a Dell Dimension 4550 that used to run Windows, and stopped correctly running Windows about 2 years ago.  The computer sat in storage for a while and was replaced by a separate Windows machine that only runs Windows, which I am using for internet access currently.  So the computer I'm speaking of doesn't boot Windows, just Ubuntu.  Both computers are set up in the same room right now and I am moving the modem connection back and forth between them, hooking it up to my Ubuntu-only computer when I am trying to test how I get it to connect to the internet, and connecting it back to my Windows-only computer to use this forum.  

I shut down the computer and unplugged the a/c socket and waited for 15 seconds, plugged everything back in and booted Ubuntu and got the same results as before.

"Well, it might be that the problem is a bug in the driver for the Realtek 8139."

The Ubuntu-only computer was wiped clean to get rid of the old malfunctioning Windows, which I would imagine any existing drivers disappeared with it.  That is, I might not even have a driver for the Realtek 8139, unless the driver was inside the modem itself (which works for the Windows-only computer) or comes with the Ubuntu CD.  Perhaps a Linux-compatable driver for Realtek 8139 would be the solution?

Thank so much for any help!

Kevin

---

### Post by rkd on 2007-12-25
I wasn't completely clear.  The bug described in that other thread is in the Linux driver for the Realtek 8139, not in the Windows driver.

I guess it doesn't matter much, since the unplugging test seems to show that your problem is something different.  I don't know yet what to try next.  I will look for other reports of problems that seem like what you are seeing and post again when I have something else to try.

---

### Post by boobahzone on 2007-12-25
Thanks rdk.  I'll post anything if I make any new discoveries as well.  Thank you for all of your help.

---

### Post by boobahzone on 2007-12-26
I don't know if this gives any info about the situation, but FYI:  I plugged my ethernet connection into my Windows machine to find my IP address, then manually added that address to the list of DNS servers after moving the ethernet connection to my Ubuntu machine.  When I select Wired Connection from the Network Settings box and click "properties" The IP address shows up along with a Subnet Mask (which does not completely match the subnet mask for Windows) and Gateway address (which matches the Default Gateway reported by Windows).  It looks like Ubuntu might have filled in these last two peices itself, so maybe it is recognizing something?  I could just be getting excited though.

Keep the ideas coming, they are much appreciated!

---

### Post by rkd on 2007-12-26
I haven't been able to find much additional information. Let's try a few things to see whether we can learn more about what is happening on your computer, or maybe stumble upon a solution.

Your most recent experiment with copying some network settings from the Windows machine was a plausible thing to try in the absence of detailed understanding of how the network stuff works.  As you saw, it didn't help, and I wouldn't have expected it to work, but experiments like that are not a bad thing.  You usually can't cause any great harm unless you are experimenting with stuff related to a hard disk whose contents are important to you, and sometimes you can get valuable clues or even solutions that way.  Unfortunately, it didn't help in this case.

So, if you have not already done this, the first thing I want you to do is to reverse those changes you did to copy the settings from the Windows machine.  We want it to be configured to get all its network information via DHCP.  Don't give it a static IP address; don't give it DNS servers.

Next, I want to repeat the experiment about trying to reset the network card by disconnecting the power.  You did that once before, but let's try it once more.  This time, leave the power disconnected for at least 2 minutes, just in case your computer's power supply can somehow retain a small bit of power for an unusually long time after the power has been disconnected.  If you aren't in a hurry to do this experiment, I'd even suggest leaving it unplugged overnight, as an extreme measure.  But 2 minutes probably is more than enough.

Before you plug the power cable back in, make sure the network cable between the computer and the modem is plugged in at both ends and that the modem is powered on.  Then turn on the computer and boot.  The reason for this is that I saw a report that the Linux driver for the 8139 has a bug that makes it not activate the device if the network cable isn't already connected to a working modem at boot time. 

I'd suggest booting from the Ubuntu CD instead of from the hard drive, just to be sure the experiment won't have any interference from any incorrect configuration information that might be on the hard drive.

When the boot is done, see whether the network is working.  If it is working, get into network-admin and make note of the settings, then reboot from the hard drive and see whether the network also is working.  If it isn't, check the settings with network-admin and post here to report what is different.  Try booting from the CD again and see whether the network works in that environment again.  If it works from the CD but not from the hard drive, the problem probably is just something wrong with the configuration and I'm sure we will be able to figure that out, eventually.

------------------------

If the above doesn't solve the problem, gather some information and post it for us to see:
```
ifconfig
ping -c 4 208.67.222.222
ping -c 4 192.168.1.1
sudo ethtool eth0
```
On the second ping command, replace 192.168.1.1 with whatever address your Windows machine shows as the default gateway address when you run the command ipconfig in a DOS window.

Also, look at the modem and back of the computer.  Where the network cable plugs in, sometimes the devices have indicator lights that turn on when the devices have sensed a proper connection.  If your modem or computer has these indicator lights, see whether they come on.  If your devices don't have these indicator lights or you aren't sure which lights are the indicators, don't worry about it -- it isn't so important; just another thing that might give a clue.

-----------------------

There is a small chance that the network cable you are using just doesn't make a good connection with the socket on the Ubuntu computer.  If you have another network cable, try substituting it.

-----------------------

Another experiment you could try is to boot a non-Linux OS on the computer to see whether that OS can make the network work.  I'm not suggesting that you would then use that OS instead of Ubuntu.  This is just a possible way to find out whether your network hardware actually is functional.  (There is always the possibility that your network card has died, though I think that is not what happened.)

In a quick search with Google, I found these two pages that have non-Linux live CDs:

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)
[http://livecd.sourceforge.net/](http://livecd.sourceforge.net/)  

I have not tried either of these live CDs, so I don't know whether either of them would be suitable.  The first is some kind of Windows-based environment, at least that is the impression I got from a quick read, though I don't understand how they can supply a Windows-based environment without a Microsoft license.  The second is a FreeBSD-based environment.

This might not be such a good idea to try, since it takes a long time to download those large image files, and I can't give you any hints about how to go about checking the network once you have booted from one of those CDs.  But if you are ambitious and want to try it, this is a possibility.

Don't feel limited to the two live CDs I pointed to.  If you or a friend have any old live CD available, it can't hurt to try it.  If it is another recent Linux-based live CD, it probably will have the same driver bugs, but you might get lucky.  If it is a non-Linux-based live CD, I'd hope that its network driver doesn't have the same bugs (but the free software people share a lot, so even drivers from other projects might have the same bugs).

------------------------------------------

If you feel comfortable opening your computer and fiddling with the adapter cards, here is something else you could try.

Some background: Not often, but more often than you might imagine, electronic equipment can malfunction because of build-up of oxidation within connectors, making the connection between components weak or broken.  I have fixed a number of devices simply by disconnecting cables and reconnecting them, one-by-one.  This can help by scraping away the oxidation.  I don't try to clean the contacts -- just the scraping involved in sliding the connectors apart and together again is all that is involved.  It doesn't always fix problems, but it often is easy to try and worth the small effort.

If you feel comfortable working inside your computer, do something like this:

- Disconnect the power to the computer.

- Unplug the network cable from the back of the computer.

- Unplug any other cables that might make it difficult to move the computer around as needed to get access to work on it.

- Open the cover of the computer.

- Touch some bare metal inside the case with both hands to discharge any static electricity charge you might have.  Do this frequently when working inside the computer, especially after you have moved around at all.  Even with this precaution, try to avoid touching the chips and conducting paths on the circuit cards.  When you work with a card, try to hold it by the metal bracket at one end and by the edge of the card at the other.

- Identify which adapter is the network card and undo the screw holding its metal bracket against the frame at the back of the computer.

- Lift the network adapter card out of the connection slot on the motherboard, into which it is plugged.  I usually do this by grasping the card by its metal bracket and by the upper corner of the back of the card, then rocking a bit as I pull up.

- Push the network adapter card back into the connection slot on the motherboard.  Make sure it goes all the way in.  It is hard to describe how much pressure is needed.  Usually there is a bit of a snap-in sensation you will notice when it slides into proper position, but that doesn't always occur.  Put the screw holding the bracket to the computer frame back in.  

With some case/motherboard combinations, the tongue of the metal bracket of the card can get hung up, preventing the back of the card from pushing down to the proper position. If that seems to be happening, you just have to wiggle the card around a bit to move the tongue of the bracket to a position that lets it slide past the obstruction.  Or you can try bending the tongue slightly in or out, as appropriate, to try to move it away from the obstruction.

- Put the cover back on the computer, reconnect all the cables, plug the power cord in, and boot.

---------------------------------------

It might be that the network card is bad.  If you have an old network card or can borrow one from someone and feel comfortable about working inside your computer, you could try substituting another network for the one you have.  

You might swap network cards between the two computers you have (if the other computer's network is built into the motherboard rather than on a separate adapter card, you clearly can't do this).  There is a small chance that you could cause trouble with your Windows computer if you try this, so it is okay if you don't want to take that risk.

------------------------------------

You don't have to do all of these things.  Do what you feel like trying and post here to tell us what you have tried and the results.  You don't have to do them all at once, either.  If you are unsure about any of the directions, please ask for clarification.

I'll keep thinking about your problem and will post any other ideas as they come to me.

---

### Post by boobahzone on 2007-12-27
Thank you so much for your help rkd.  I have tried some of the suggestions you've made:

I undid the changes I made to the network configuration.  I, too, figured that they wouldn't work, but I figured I would mess around with the very little changes I know how to make.  And for the record, I am completely okay with experimenting on the Ubuntu computer -- there is not one single byte of valuable information on that system that I would be afraid of losing.  

> **rkd said:**
> Next, I want to repeat the experiment about trying to reset the network card by disconnecting the power.  You did that once before, but let's try it once more.  This time, leave the power disconnected for at least 2 minutes, just in case your computer's power supply can somehow retain a small bit of power for an unusually long time after the power has been disconnected.  If you aren't in a hurry to do this experiment, I'd even suggest leaving it unplugged overnight, as an extreme measure.  But 2 minutes probably is more than enough.

Before you plug the power cable back in, make sure the network cable between the computer and the modem is plugged in at both ends and that the modem is powered on.  Then turn on the computer and boot.  The reason for this is that I saw a report that the Linux driver for the 8139 has a bug that makes it not activate the device if the network cable isn't already connected to a working modem at boot time. 

I'd suggest booting from the Ubuntu CD instead of from the hard drive, just to be sure the experiment won't have any interference from any incorrect configuration information that might be on the hard drive.

After I undid the network configuration changes, I shut down the computer and unplugged the a/c power and the ethernet cable for several minutes.  Then, I plugged in the ethernet cable and then plugged in the power, and rebooted from the live CD.  Doing this yielded the same results as I normally got.  I repeated these steps, booting from the hard drive and also got the same rusults.


> If the above doesn't solve the problem, gather some information and post it for us to see:
```
ifconfig
ping -c 4 208.67.222.222
ping -c 4 192.168.1.1
sudo ethtool eth0
```
On the second ping command, replace 192.168.1.1 with whatever address your Windows machine shows as the default gateway address when you run the command ipconfig in a DOS window.

Sure thing!  Here is what I got:
```

kevin@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3960 (3.8 KB)  TX bytes:3960 (3.8 KB)

kevin@ubuntu:~$ ping -c 4 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
From 169.254.3.156 icmp_seq=1 Destination Host Unreachable
From 169.254.3.156 icmp_seq=2 Destination Host Unreachable
From 169.254.3.156 icmp_seq=3 Destination Host Unreachable
From 169.254.3.156 icmp_seq=4 Destination Host Unreachable

--- 208.67.222.222 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3008ms
, pipe 3
kevin@ubuntu:~$ ping -c 4 70.171.174.1
PING 70.171.174.1 (70.171.174.1) 56(84) bytes of data.
From 169.254.3.156 icmp_seq=1 Destination Host Unreachable
From 169.254.3.156 icmp_seq=2 Destination Host Unreachable
From 169.254.3.156 icmp_seq=3 Destination Host Unreachable
From 169.254.3.156 icmp_seq=4 Destination Host Unreachable

--- 70.171.174.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3007ms
, pipe 3
kevin@ubuntu:~$ sudo ethtool eth0
[sudo] password for kevin:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: p
        Current message level: 0x00000007 (7)
        Link detected: no

```

> Also, look at the modem and back of the computer.  Where the network cable plugs in, sometimes the devices have indicator lights that turn on when the devices have sensed a proper connection.  If your modem or computer has these indicator lights, see whether they come on.  If your devices don't have these indicator lights or you aren't sure which lights are the indicators, don't worry about it -- it isn't so important; just another thing that might give a clue.

Sure thing.  When the ethernet cable is plugged into the back of the computer, an orange LED turns on, in addition to several greenish-yellow LEDs that remain on regardless of whether the ethernet is plugged in.  Also, I don't have an extra ethernet cord, but I reversed the plug (that is, I moved the end that was connected to the modem and connected it to the computer, and connected the computer end into the modem) and still got the same results.


> Another experiment you could try is to boot a non-Linux OS on the computer to see whether that OS can make the network work.  I'm not suggesting that you would then use that OS instead of Ubuntu.  This is just a possible way to find out whether your network hardware actually is functional.  (There is always the possibility that your network card has died, though I think that is not what happened.)
I have not tried this yet, but I would be more than happy to do so.  I'm not afraid of spending a little time and elbow grease to fix this problem.  After I finish this post, I will download the CD image and run the live CD and post the results. :)

> If you feel comfortable opening your computer and fiddling with the adapter cards, here is something else you could try.
I will also try this as well, possibly after I run the liveCD for a non-linux OS and will post the results for this as well.  I'm not too familiar with computer hardware (although I was an electrical engineering major for three years, believe it or not!) but I'm not afraid to experiment with this computer.  :)

> It might be that the network card is bad.  If you have an old network card or can borrow one from someone and feel comfortable about working inside your computer, you could try substituting another network for the one you have.  
This is one thing that makes me a little nervous.  I don't know too much (or anything at all, really) about hardware, and I would worry that in the slight chance I screw things up, I would ruin another person's network card (i.e., the card on my parents computer).  This makes me a little nervous, so I might need to pass on this suggestion, but thank you for the idea!

So, there are a the results from some of your suggestions.  I will continue to follow through with more of them and post my results again.

Thanks so much for your help!

---

### Post by rkd on 2007-12-27
Good job.  Too bad none of my suggestions got it working.

I don't see anything in the results you describe that clearly stands out as the problem, but I should say again that I'm new to Ubuntu, so I could easily be overlooking something that is clear to others.

I probably should have asked you to do the ifconfig command after trying the pings, so we could see whether the pings caused any packets to be transmitted on eth0.  Could you try that?

The information from ethtool seems a little odd to me -- it says the port is MII rather than twisted pair, which is what it shows on my system, but my system has the ethernet built into the motherboard and uses a Marvell controller.  Maybe that makes the difference, but I don't know for sure.  It seems odd.  Your system shows 32 for PHYAD, while mine shows 0.  That is the physical address, and I think it is okay for that to be different from one computer to the next.

I'm pretty sure that the action of the orange indicator light that you saw means that the cable is correctly connecting the modem with your ethernet card.

One more thing I can think of to check: Let's look at the system log to see whether it gives any clue about why the ethernet link doesn't get going.  The system log is in /var/log/syslog and there is a viewer available from the desktop.  From the menus: system -> Administration -> System log.  When it opens, in the left pane, find and click syslog, and that should show you all the messages.  I understand very little of them, but they might give some hint about what to look at next.  

I'd suggest booting from the CD for this. It might be easier to use the file manager to copy /var/log/syslog to a floppy than to copy and paste from the log file viewer, but find a way to get that log over to your Windows system to post it.  It will be rather long; I hope the forum rules allow that. I don't remember anything about length of postings when I looked at the rules at the beginning, but I might have forgotten.  Maybe you could attach the log file to your post instead of copying it into the post.

I understand your reluctance to risk damaging the network card in your parents' computer, so it is fine to skip that experiment.

My feeling is that the experiment of trying a different operating system is still worth trying, if you feel like doing it and have the time.  I think the experiment of pulling out the network card and replacing it to clean its contacts is less important. If it were me, I'd do it, but if you feel at all uneasy about it, we can put that one off until later.

---

### Post by boobahzone on 2007-12-28
Thanks again for all of your help rkd.  Here is what I've come up with so far:

> **rkd said:**
> I probably should have asked you to do the ifconfig command after trying the pings, so we could see whether the pings caused any packets to be transmitted on eth0.  Could you try that?

Sure thing.  I rebooted from the CD and ran the same commands as before, however this time I got different output for some reason I'm unaware of.  For example, when I entered the ping command, rather than returning info about the 4 tries it makes to connect, I just got one message saying the network was unreachable, and I don't know why.  Here is the result of running the same commands as before from the live CD, only with the ifconfig command after the pings.

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5120 (5.0 KB)  TX bytes:5120 (5.0 KB)

ubuntu@ubuntu:~$ ping -c 4 208.67.222.222
connect: Network is unreachable
ubuntu@ubuntu:~$ ping -c 4 70.171.174.1
connect: Network is unreachable
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5120 (5.0 KB)  TX bytes:5120 (5.0 KB)

ubuntu@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: p
        Current message level: 0x00000007 (7)
        Link detected: no
ubuntu@ubuntu:~$ 
```

> One more thing I can think of to check: Let's look at the system log to see whether it gives any clue about why the ethernet link doesn't get going. 

Absolutely.   I was able to copy and paste all the data easily, so the data is attached to this post.  The .txt file was too big for this message board, but I was able to attach it as a .zip file with no problem.

> My feeling is that the experiment of trying a different operating system is still worth trying, if you feel like doing it and have the time.

I agree, and I certainly am willing to put some time into this thing.  I downloaded the files and looked over the information about the two liveCDs you posted, both of which seemed to require some extra savvy that I did not have.  However, I found one called LiveSBIE ([http://www.freesbie.org/share/2.0/manual/](http://www.freesbie.org/share/2.0/manual/)) which says it runs off of FreeBSD.  I looked up FreeBSD on Wikipedia and it seemed like it was a different OS from Linux, but it also mentioned a great deal of compatibility between the two.  Because of this, I wasn't sure if FreeBSD would cut it for our purpose, because I don't know how much the two systems have in common.  

I made a LiveCD for LiveSBIE and ran it on my machine and found that I had the same results as my last post, for which I posted the results of the ifconfig and ping -c 4 208.67.222.222 commands.  However, I never found out how to copy and paste the results from the terminal in this OS, so I can't post them here.  I know that it was not connecting to the network though, which I confirmed by the ping command results and by opening firefox.  Please let me know though if you think that FreeBSD is too close to Linux, and I am certainly willing to try this with another OS LiveCD.  Seeing them all is quite interesting, as I've mostly only used Windows and some OS X, so it's neat to work with the different ones any.  

That being said, these experiments have been very educational to me and I'm enjoying working on this problem.  I appreciate all of the help!  Please, keep it coming!

Next stop: working with the connections between the electronic components as you described in your previous post.  I'll certainly provide updates as things move along.

---

### Post by boobahzone on 2007-12-28
Another update:

I tried opening my computer and following the instructions you provided, however I wasn't exactly sure on where my network card was.  I did a google image search for "network card" and it looked like the card should be exactly opposite to where my ethernet plug is on the external side of the computer casing.  It seemed to me that there wasn't anything there on the opposite side.  I don't know where my network card would be on the inside, though I will keep doing some research to find out where it would be.  I would think it is in there somewhere, as I know this computer used to run off of a cable modem several years ago, and has remained untouched since.  

Just to make sure though: the results I've posted so far do suggest that I have a network card, right?

---

### Post by rkd on 2007-12-28
You are right -- the network card should be right behind the ethernet jack. I'm sorry, I should have mentioned that. 

The ethernet jack is on the end of the card that is exposed at the back of the computer.  Or that is the way it is when your computer has a separate network card that plugs into one of the expansion slots.  If your computer has an integrated LAN controller, then the electronics for the LAN are on the motherboard (the big circuit board into which everything else plugs).  With an integrated controller, there aren't any contacts to try to clean.

When I looked up the Dimension 4550 on the Dell web site a couple of days ago, I found descriptions that say that the Dimension 4550 has a separate network card. After seeing your most recent post, I went looking a bit more, and Dell's description of the 4550 is inconsistent, in that it also says it has an integrated LAN controller.

So I'm confused.  Could it be that your computer is not a Dimension 4550?  Or did Dell change the implementation of the Dimension 4550 at some point?  Please double-check the exact model of your computer. I think Dell puts that information on a label on the back panel of the computer, or maybe inside the case somewhere.

Here are some pointers to the Dell documentation. You can compare the diagrams and descriptions with your computer and see whether they match.  

The main documentation page I found is at:
[http://support.dell.com/support/edocs/systems/dim4550/](http://support.dell.com/support/edocs/systems/dim4550/)

The others, below, can be reached from that main page, but I'll give you pointers to a few of the pages most relevant at the moment:

Technical overview, diagrams of the inside of the computer
[http://support.dell.com/support/edocs/systems/dim4550/techov.htm#1101565](http://support.dell.com/support/edocs/systems/dim4550/techov.htm#1101565)

Changing an adapter card
Dell Dimension 4550 Owner's Manual, pages 85-90
[http://support.dell.com/support/edocs/systems/dim4550/D0995bk0.pdf](http://support.dell.com/support/edocs/systems/dim4550/D0995bk0.pdf)

Installing and Removing Cards
[http://support.dell.com/support/edocs/systems/dim4550/replace.htm#1101572](http://support.dell.com/support/edocs/systems/dim4550/replace.htm#1101572)

Technical Specifications
[http://support.dell.com/support/edocs/systems/dim4550/specs.htm#1101572](http://support.dell.com/support/edocs/systems/dim4550/specs.htm#1101572)

The Technical Overview page says the network adapter should be in the third PCI slot (see table at the bottom of the page and see the second drawing on the page for how the PCI slots are numbered).

Both the Technical Specifications page and the Owner's Manual contradict that. The Technical Specifications page says that the network is an integrated Intel 82562ET, and the drawing of the case at the start of the Owner's Manual shows the ethernet jack over by the other motherboard jacks, not on one of the expansion slots. 

Since the lspci command on your computer shows the Realtek 8139 controller, and does not show the Intel 82562, it seems pretty clear that your system does not have the integrated Intel LAN controller. But if you didn't find an adapter card behind the slot that has the ethernet jack, that confuses me.

What did you find on your computer? Is the ethernet jack where the drawing in the Owner's Manual shows it, or is it on one of the expansion slot covers?  If it is on one of the expansion slot covers, what is inside of the computer behind the ethernet jack? Did you find a few wires leading off to plug into the motherboard somewhere?  Or something else?

To answer your question, I was pretty sure your computer has a separate network card, but I'm not at all sure right now.

To summarize my questions: 

Look for a label that gives the exact model of your computer - what does it say?

How does your computer compare with the drawings in the various documents available from that Dell support page?

Is your ethernet jack on one of the expansion slot covers?  If so, describe what is on the inside right behind the jack.

Slight subject shift: Do you have any of the CDs that came with your computer when it was new?  One of them, called the Dell Dimension Resource CD, contains diagnostics that we might be able to run to see whether they can find anything wrong with the network card.  I know it is a long shot, since most people seem to lose those CDs within a few hours of opening the box containing the computer, but I wanted to ask.

---

### Post by rkd on 2007-12-28
I now had a chance to study the results you described in post #18. 

I think we need to figure out what was different between post #18 and post #16. In #16 the ping command was able to find the network, but in #18 it was not able to find the network.

In #16, from reading your description, it seems like you did the ping commands when you had booted from the hard disk. You said you first booted from the CD, tried the network, found it didn't work, then booted from the hard disk, tried the network, and found it still didn't work.  Your post then went on to give the results from running ifconfig, the pings, and ethtool.  Since you didn't mention booting from the CD again, it seems like the ifconfig, ping, and ethtool results were obtained while running from the hard disk.  

Do you remember clearly whether that is how it went? I know it is hard to keep all the details straight in your mind when you are trying so many things, so if you don't remember clearly, that's okay.  When I'm working on a problem, I often have to go back and try things again because I wasn't sure of a detail like that.

When I asked you to redo the test with the ifconfig command after the pings, I suggested that you boot from the CD, simply because I have the feeling that starting from the CD gives us the same starting point each time (no chance that something we tried on an earlier test affects the configuration parameters for the current test). Maybe that wasn't a good idea. Maybe the system comes up enough differently when booting from the hard disk vs. the CD that the LAN works better from the hard disk. Or maybe something you tried earlier has beneficially affected the configuration parameters stored on the hard disk, making the LAN work a little better when booted from the hard disk.

That was a long-winded way of  saying that I think you should try it again, this time booting from the hard disk. If the ping commands give the network unreachable error again, then it isn't just a difference between booting from the disk vs. booting from the CD. In that case, stop there and we'll have to think of what else could be different. If the ping commands get the host unreachable error, then do the ifconfig command and post the results, and also post the syslog. It probably would be good to post just the part of the syslog from the current boot, just to keep it small. The time given at the start of each line should help you find the right place to start.

When you are doing this test again, before trying the pings, look at the network configuration to see whether it says to use DHCP. If it doesn't say DHCP, note what it is and do the test without changing it, but if the pings get the network unreachable error, change the network configuration to make it use DHCP, reboot, and try again. (I'm sure there is a way to get the change to take effect without booting, but I'm not sure how to do that; I know booting will get the change to take effect.)

Did you happen to notice whether the orange indicator light by the LAN cable jack was on or off when you got the results posted in post #18?

Remember that there is a bug in the Linux driver for the 8139 that makes it not work right if the LAN cable is not plugged in at the time you boot, so remember to get it set before booting.

I looked at the syslog you posted. I don't understand most of it, but I noticed a couple of things.  One is that Linux first tries using the 8139cp driver, that driver decides the LAN controller is not an 8139C+ and says it is trying the 8139too driver instead. The 8139too driver reports that it found an 8100B/8139D LAN controller and appears to be satisfied with that.  Maybe that initial misidentification is an important clue, maybe it is nothing unusual. We should keep that detail in mind to look into later if nothing else we can think of helps.

The other thing I noticed is that there is nothing in the log from the dhclient.  When I look at the syslog from booting an Ubuntu 07.04 CD, there are some lines that report the dhclient doing things that look like it is asking for the TCP/IP information needed.  I don't see anything like that in the syslog you posted. The very last entry in your syslog says that the network manager is activating eth0. In my syslog, that message about activating eth0 is the first of several messages from the network manager about activating the device, and it is followed by messages from dhclient about things it is doing. I wonder why we don't see the corresponding messages in your syslog. Is there a chance that you somehow didn't get all the messages from your syslog? I don't know how that might have happened, so I don't know what to tell you to do diferently to be sure to get them all. Just look carefully at how you are getting the messages from syslog and try to be sure you aren't missing any of them.

Your experiment with LiveSBIE is exactly what I had in mind for you to try.  I assume that one FreeBSD-based system is pretty much the same as any other FreeBSD-based system, so it appears that either FreeBSD has the same software problems as Linux has with your hardware, or there is something broken with your hardware.  Unfortunately, we can't tell which case it is.  If the FreeBSD system had been able to get the network working, we would know the problem is Linux, not your hardware. Unless you have the Dell diagnostic CD I mentioned at the end of post #20, I can't think of anything else right now that would help us distinguish between hardware problems and software problems.  

There is one new thing I thought of to try -- you might try booting the Ubuntu CD on the Windows computer and see whether the network works from there. I don't think that is a very important thing to try.  If it worked on that computer, it would tell us that there isn't anything special needed to communicate with your modem and/or ISP that Ubuntu isn't doing correctly.  I think you said it is a cable modem, and I believe it is highly unlikely that there is anything special involved, but it might be nice to be reassured that way. Booting the live CD on that computer should be very safe, very unlikely to disturb the Windows installation on the hard disk, but if you would rather not take the chance, that's okay -- I won't push for that test.

---

### Post by rkd on 2007-12-28
I just had another thought.  Might be completely wrong.

Suppose your computer really does have the Intel LAN controller integrated on the motherboard AND suppose that the Linux automatic device recognition code is misidentifying it. In that situation, things might work just enough that some of the Linux code thinks the device is working, but other parts disagree.  Perhaps that could lead to the problem you are seeing.  I think it is pretty low probability, though.

One way to check on this would be to look for the Intel 82562ET chip on the motherboard.  That's not very easy to do when the motherboard is in the case and has lots of stuff plugged into it, but if you want to give it a try, go ahead. But don't make it a high priority. (And don't go looking for it if you discover that you really do have a separate LAN adapter card!)

If there is any diagnostic software that gives a list of the devices integrated onto a motherboard, I'm not aware of it. That would be much more convenient than trying to read the labels on the chips.

This speculation assumes, for the moment, that your computer really is a Dimension 4550 and that the Dimension 4550 uses the Intel 82562ET LAN controller.  That might turn out not to be true, in which case, this is completely wrong.

I don't have time to do it right now, but probably tomorrow I can look to see whether there are any Linux problems with the Intel 82562ET LAN controller that might lead to this situation.

---

### Post by boobahzone on 2007-12-29
Thanks for all the suggestions!  I will tackle them in a series of posts so that I don't get too far ahead of myself.  To start with the first post:

> **rkd said:**
> Look for a label that gives the exact model of your computer - what does it say?
I looked around for a label on the back and inside of my computer and didn't see one with the exact model number.  The model number on the front of the computer says "Dimension 4550" which was where I figured the model out from in the first place.  I used the service tag model of my computer and looked it up on the dell website, which also confirmed that the model was a Dimension 4550.

> How does your computer compare with the drawings in the various documents available from that Dell support page?  Is your ethernet jack on one of the expansion slot covers?  If so, describe what is on the inside right behind the jack.
To the best of my limited understanding of computer hardware, my hardware seemed similar to the hardware given on the dell support page.  The ethernet jack was not on one of the expansion slot covers.  Rather, the ethernet jack is above the expansion slots, on the same panel as the I/O for my monitor, mouse, keyboard, and 4 USB ports.  When I looked inside right behind the ethernet jack, there was a metalic box about 1"x1"x0.5" that connected directly to the motherboard from the jack with the numbers "3042-L71 10/100 BT" printed on it.

> Slight subject shift: Do you have any of the CDs that came with your computer when it was new?  One of them, called the Dell Dimension Resource CD, contains diagnostics that we might be able to run to see whether they can find anything wrong with the network card.  I know it is a long shot, since most people seem to lose those CDs within a few hours of opening the box containing the computer, but I wanted to ask.
I actually don't have these CDs with me, however there is a chance that my brother might.  For about a year, my brother (who knows even less about computers than me) held on the the computer and all the accompanying CDs and parts.  When the computer came to be in my possession, all I had were the monitor, mouse, keyboard, tower, and connecting cords.  However, luckily I am meeting up with my brother tomorrow and can see if he has all the CDs that came with it, hopefully meaning I might end up with a diagnostic CD.

I looked online to see if there were any iso images of Dell diagnostic CDs and found a website that guides you through the process of making your own ([http://www.bay-wolf.com/diag.htm](http://www.bay-wolf.com/diag.htm)).  I downloaded and extracted their files as well as the necessary files from Dell to make my own bootable Dell Diagnostic CD, however the CD-burning program they used to make the boot CD was Nero, which I do not have.  (I have Roxy and Deep Burner, and recently installed ImgBurn to see if this would give me a similar setup to Nero.)  Unfortunatley, Deep Burner and ImgBurn would not recognize the .img file that came with bay-wolf's .zip file, at which point I gave up on creating my own diagnostic boot CD and started hoping I would eventually find the old one.

So, does this mean that I have an integrated LAN controller, since my network card is not on one of the expansion slots?

Now onto working on the next post :)

---

### Post by rkd on 2007-12-29
More good work! Keep at this and we'll get it working pretty soon.

You definitely have an integrated LAN controller. Everything you describe confirms that.  That makes me wonder a bit more about why Dell says the system uses an Intel LAN controller, but Linux thinks it finds a Realtek LAN controller. I'll continue my online searches about the Intel LAN controller and Linux.

That's good luck that you will be able to ask your brother about the Dell CDs. Try to get anything related to the computer -- user manuals, CDs, whatever. If you can get what's needed to restore Windows onto that computer, if we get desperate, we could do that to see whether Windows can run the LAN, to find out whether the hardware really works or not.

Good work on tracking down instructions for making your own Dell Diagnostic CD! I looked around a bit and didn't find that. I believe I remember reading about a way to use .img files with other CD writing programs. If you can't get the Dell CDs from your brother, we probably can finish the process of creating your own.

---

### Post by boobahzone on 2007-12-29
Thanks again for the line of suggestions!  Unfortunately, I don't remember too much about about the details for when I was working on each of these posts; my mind tends to blur things together even when I'm dealing with the subjects that I am familiar with, so I'm afraid I would be too inaccurate to recall what I did in the past, although I am certainly willing to repeat experiments.  I've worked on some of the things you listed in the second post, let me know if I misinterpreted any of the tasks you provided...

> **rkd said:**
> When I asked you to redo the test with the ifconfig command after the pings, I suggested that you boot from the CD, simply because I have the feeling that starting from the CD gives us the same starting point each time (no chance that something we tried on an earlier test affects the configuration parameters for the current test). Maybe that wasn't a good idea. Maybe the system comes up enough differently when booting from the hard disk vs. the CD that the LAN works better from the hard disk. Or maybe something you tried earlier has beneficially affected the configuration parameters stored on the hard disk, making the LAN work a little better when booted from the hard disk.
Yes, I thought it was interesting too for the error message I got.  What was really peculiar is that I am certain that I've booted from the hard drive and from the CD and recieved the same error messages, so I am no completely sure why I got the weird ping response that one time only.  Perhaps I neglected to connect the modem before startup or some other confounding variable affected my results.

> That was a long-winded way of  saying that I think you should try it again, this time booting from the hard disk. If the ping commands give the network unreachable error again, then it isn't just a difference between booting from the disk vs. booting from the CD. In that case, stop there and we'll have to think of what else could be different. If the ping commands get the host unreachable error, then do the ifconfig command and post the results, and also post the syslog. It probably would be good to post just the part of the syslog from the current boot, just to keep it small. The time given at the start of each line should help you find the right place to start. 
Superb.  I booted from the hard disk and checked the syslog, which I have again attached to this post (with only the recent events kept in it).  I ran the ifconfig, ping, ifconfig, and ethtool commands and got the following results: 

```

kevin@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          inet addr:169.254.3.156  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5144 (5.0 KB)  TX bytes:5144 (5.0 KB)

kevin@ubuntu:~$ ping -c 4 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
From 169.254.3.156 icmp_seq=2 Destination Host Unreachable
From 169.254.3.156 icmp_seq=3 Destination Host Unreachable
From 169.254.3.156 icmp_seq=4 Destination Host Unreachable

--- 208.67.222.222 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3
kevin@ubuntu:~$ ping -c 4 70.171.174.1
PING 70.171.174.1 (70.171.174.1) 56(84) bytes of data.
From 169.254.3.156 icmp_seq=1 Destination Host Unreachable
From 169.254.3.156 icmp_seq=2 Destination Host Unreachable
From 169.254.3.156 icmp_seq=3 Destination Host Unreachable
From 169.254.3.156 icmp_seq=4 Destination Host Unreachable

--- 70.171.174.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3009ms
, pipe 3
kevin@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          inet addr:169.254.3.156  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5928 (5.7 KB)  TX bytes:5928 (5.7 KB)

kevin@ubuntu:~$ sudo ethtool eth0
[sudo] password for kevin:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: p
        Current message level: 0x00000007 (7)
        Link detected: no

```


> When you are doing this test again, before trying the pings, look at the network configuration to see whether it says to use DHCP. If it doesn't say DHCP, note what it is and do the test without changing it, but if the pings get the network unreachable error, change the network configuration to make it use DHCP, reboot, and try again. (I'm sure there is a way to get the change to take effect without booting, but I'm not sure how to do that; I know booting will get the change to take effect.)  I checked, and DHCP was selected.  I don't think that this is by default though, as I remember having to physically change it to that by unchecking the enable roaming button, and then choosing DHCP.  But DHCP was selected when I ran it from my hard disk because my computer saved my previous changes for that.

> Did you happen to notice whether the orange indicator light by the LAN cable jack was on or off when you got the results posted in post #18? 
Unfortunately I don't... sorry!

> Just look carefully at how you are getting the messages from syslog and try to be sure you aren't missing any of them.
I double-checked this time to see that I was copying and pasting everything, and the data that I've included on this post matches everything that showed up in the system log for this boot.  The syslog data is attached to this post like before and everything listed since the last boot is included on it.  The times presented might not match up directly with the times listed from the "ping" commands I posted, because I forgot to save my terminal output so I had to redo it.  However, all of the syslog data was the same for both times I did it, they just had different hour-minute-second times posted on it.

Did I get all of this right?  Please correct me if I misinterpreted...

Also, I will try booting my windows machine from the Ubuntu CD and post the results!  I need to take a break right now, but hopefully I can get to it tonight or tomorrow, as well as your other post.

Thanks for all of the help!  Your assistance is greatly appreciated!

---

### Post by boobahzone on 2007-12-30
Since my last post, I've tried running Ubuntu on my Windows machine via the LiveCD.  The OS and the network connection run automatically like a charm with the machine, which supports the other evidence that this must be a problem with the Ubuntu computer hardware.

Also, I opened up the Ubuntu computer to look for the 82562ET LAN controller and had a hard time locating it.  I looked on as many labels as I could on the integrated circuits and boards within the computer and didn't see any that matched that label.  I also did a google image search for "82562ET" and didn't see any parts that looked similar to this board.

I will see how much additional components I can gather from my brother tomorrow and post an update.

Thanks again!

---

### Post by rkd on 2007-12-30
Yes, that confirms that the problem isn't that your cable modem needs some special treatment that Ubuntu doesn't do. So the problem is either that Ubuntu isn't running your hardware correctly or that the hardware isn't working. That's what I expected, but getting it confirmed is good.

Thanks for trying to find the LAN controller chip on the motherboard. It is pretty hard to read those chip markings when the motherboard is in the case with everything plugged in, isn't it? It turns out that the LAN controller might be still a different one -- see further down in this post. If you feel like looking again to see whether you spot either of the other possible controllers, tell me and I'll tell you what they might be. 

I looked at the bay-wolf site, downloaded their files and looked at them.  I think the .img file isn't a CD image, but rather an image of a boot floppy. The CD boot process usually involves loading an image of a boot floppy from the CD, so I think using a floppy image is very common. I looked at the ImgBurn web site for usage directions, and I think its function for creating a bootable CD should accept that floppy image file. Did you try to put that filename into the field for the boot image on the screen for making a bootable CD? Did it give you an error? What did the message say? Or did something else happen to make you think it doesn't work?

I didn't try looking for usage directions for the other CD writing programs you mentioned, but if they have an option for making a bootable CD, I think bay-wolf's floppy .img file would work with them. So do try to get any stuff from your brother that goes with that PC, but if he doesn't have the Dell Dimension Resource CD, I think you'll be able to create a CD from which you could run the diagnostics. If we need to try that, tell me and I'll try using ImgBurn to make a bootable CD with the diagnostics and give you precise directions if it works.

Your ping and ifconfig results confirm something I was guessing from the earlier results. It sure looks like the pings cause packets to be sent and received on the loopback device. The packet count isn't exactly what I expected, so I might be misinterpreting the results. As far as I understand things, the pings shouldn't use the loopback, so that's another oddity we need to keep in mind to look into later if we get stuck.

The system log doesn't look much better than the earlier one (given the little I understand of it).  A small point that might be good is that the 8139cp driver seems to be satisfied with the LAN controller. It did not emit the message that was in the earlier syslog that said the controller was not 8139C and switch to the 8139too driver.  On the other hand, there were no messages saying the eth0 link was up. The earlier log had a link up message followed closely by a link down message. I don't know which situation is better. Neither is good -- the link should come up. I imagine the fact that the link is down is the reason we don't see any DHCP activity (and that the pings don't work), but I don't know a lot about this, so I might be wrong.

I only found one report of network trouble on a Dimension 4550 that seemed similar to what you are seeing, and the guy who reported it didn't get an answer on the forum. He hasn't posted anything since then (middle of 2006), either. I figured it wasn't likely he would see any message I posted to him to ask whether he solved the problem, so I didn't try.

On the site hardware4linux.info, I found a list of components in Dimension 4550 computers, and it lists two Intel LAN controllers, neither of which seems to be the one mentioned on the Dell web site. And I don't understand why hardware4llinux lists two LAN controllers. I doubt it means a single 4550 computer contains two LAN controllers. More likely they have seen some 4550s with one of the controllers, and other 4550s with the other controller.  From what I read on hardware4linux.info, the same Linux driver, e100, supports both of those LAN controllers, as well as the one the Dell site says they use. So another thing we could try is forcing Linux to load the e100 driver. I searched for clues about how to do that, and I think I found out how that is done. 

But I don't know whether that's right. The lspci output you posted a few days ago definitely shows the ethernet controller as Realtek 8139. From reading the description of lspci, it is displaying the information it retrieved from the devices themselves. Well, no, it gets ID codes from the devices and has a table it uses to look up the ID codes to find the text name for the make and model. Could that table be wrong? Seems unlikely, but not impossible. Puzzles, puzzles, puzzles.

A few days ago, you mentioned that this computer had been running Windows a couple of years ago, but it stopped running Windows correctly and was replaced. Do you remember any details about what was wrong that it didn't run Windows correctly? Did it, by some chance, stop connecting to the internet properly?

I wonder what would happen if we just used a sudo ifup eth0 command to tell the eth0 device to come up. That is simple to try. Open the program that displays the syslog, scroll to the end of the log, in a terminal enter 
```
sudo ifup eth0
sudo /etc/init.d/networking restart
``` 
and see what appears in the syslog. If it does anything that looks like it brought the link up, try the ping commands. If it comes up but goes back down again, try it once again. If that doesn't get the network to work, try this:
```
sudo modprobe -r 8139cp
sudo modprobe 8139cp
sudo /etc/init.d/networking restart
```
Again, if it looks like it might have come up, try the ping commands. If it doesn't work the first time, you can try it again once or twice. I'm sort of grasping at straws here. If the hardware is a little flaky, maybe if we get the software to go through the initialization a few more times, one of the times it will work. Can't hurt to try. Post the part of the syslog that records the activity from these commands, and if you get something new from the ping commands, post it, too.

If that doesn't give you any success, as long as we are experimenting, let's try the e100 module:
```
sudo modprobe -r 8139cp
sudo modprobe e100
sudo /etc/init.d/networking restart
```
That removes the 8139cp module and loads the e100 module. I'm pretty sure the e100 module won't work, but I think it is unlikely to cause any more trouble.

---

### Post by boobahzone on 2008-01-01
Thanks again rkd.  I moved back to my home and am working with a different windows computer and a different modem back at my place instead of at my parents while I was visiting for the holidays.  Sorry for the gap of time in response, I was mostly en route to my home.  I will tackle some of your questions right now, then work on some of the linux commands you gave me and post those in a separate response.  Unfortunately, I only have one monitor now, so booting between systems involves a bit more connect-reconnect action, but it can still be done :)

> **rkd said:**
> I looked at the bay-wolf site, downloaded their files and looked at them.  I think the .img file isn't a CD image, but rather an image of a boot floppy. The CD boot process usually involves loading an image of a boot floppy from the CD, so I think using a floppy image is very common. I looked at the ImgBurn web site for usage directions, and I think its function for creating a bootable CD should accept that floppy image file. Did you try to put that filename into the field for the boot image on the screen for making a bootable CD? Did it give you an error? What did the message say? Or did something else happen to make you think it doesn't work?
It seemed like both programs would not support the file type.  When creating a boot CD, Image Burn only accepted .iso file types, so .img was not even a viewable option for that program.  For Img Burn, the .iso was a filetype option, but when I selected it while I was trying to create a boot CD it said that the file was an invalid file type.

> I didn't try looking for usage directions for the other CD writing programs you mentioned, but if they have an option for making a bootable CD, I think bay-wolf's floppy .img file would work with them. So do try to get any stuff from your brother that goes with that PC, but if he doesn't have the Dell Dimension Resource CD, I think you'll be able to create a CD from which you could run the diagnostics. If we need to try that, tell me and I'll try using ImgBurn to make a bootable CD with the diagnostics and give you precise directions if it works.
Unfortunately, I was not able to get the resource CDs from my brother when I met with him.  He did say, however, that he has a boxful of CDs that I can take.  I am asking him to mail them to me, which of course will take a few days, and I can let you know when they arrive.  Wasn't exactly what I was hoping for, but that's how things go I guess.

> A few days ago, you mentioned that this computer had been running Windows a couple of years ago, but it stopped running Windows correctly and was replaced. Do you remember any details about what was wrong that it didn't run Windows correctly? Did it, by some chance, stop connecting to the internet properly?
Good question!  I probably should have brought the issue up earlier.  When the computer stopped working properly about 2 years ago, it was having trouble properly loading windows.  I don't know if there were network problems, because the computer never even really booted correctly into windows.  When the computer would start up, it used to take a long time (~15 minutes) to boot into Windows, then when Windows was starting it did not present the user login screen, just a blue welcome-to-Windows screen.  

I don't know if this is related (but this might have caused the aforementioned problem), but when I start the Ubuntu computer it still gives me a warning message saying "WARNING: Dell&#8217;s Disk Monitoring System has detected that drive 0 [which is my hard drive] on the primare EIDE controller is operating outside of normal specifications. It is advisable to immediately back up your data and replace your hard-disk drive by calling your support desk or Dell Computer Corporation.&#8221; Then I press F1 to continue, and Windows would always fail to load.  With Ubuntu, however, pressing F1 always loads the OS without any apparent problems except for the current network issue.  The issue is briefly discussed in this thread: [http://ubuntuforums.org/showthread.php?t=648822](http://ubuntuforums.org/showthread.php?t=648822)

I will try working on some of the commands you've posted and let you know how it goes.  Thanks!

---

### Post by boobahzone on 2008-01-01
> **rkd said:**
> 
I wonder what would happen if we just used a sudo ifup eth0 command to tell the eth0 device to come up. That is simple to try. Open the program that displays the syslog, scroll to the end of the log, in a terminal enter 
```
sudo ifup eth0
sudo /etc/init.d/networking restart
``` 
and see what appears in the syslog. If it does anything that looks like it brought the link up, try the ping commands. If it comes up but goes back down again, try it once again. If that doesn't get the network to work, try this:
```
sudo modprobe -r 8139cp
sudo modprobe 8139cp
sudo /etc/init.d/networking restart
```
Again, if it looks like it might have come up, try the ping commands. If it doesn't work the first time, you can try it again once or twice. I'm sort of grasping at straws here. If the hardware is a little flaky, maybe if we get the software to go through the initialization a few more times, one of the times it will work. Can't hurt to try. Post the part of the syslog that records the activity from these commands, and if you get something new from the ping commands, post it, too.

If that doesn't give you any success, as long as we are experimenting, let's try the e100 module:
```
sudo modprobe -r 8139cp
sudo modprobe e100
sudo /etc/init.d/networking restart
```
That removes the 8139cp module and loads the e100 module. I'm pretty sure the e100 module won't work, but I think it is unlikely to cause any more trouble.

Thanks!  I ran all of these commands, none of which got the network started.  I saved the terminal output and the syslog output, both of which are given below:

syslot output (starting from when I entered the commands)
```

(sudo ifup eth0 command)
Jan  1 10:44:14 ubuntu kernel: [  183.705901] eth0: link down
Jan  1 10:44:14 ubuntu kernel: [  183.706354] ADDRCONF(NETDEV_UP): eth0: link is not ready

(sudo modprobe 8139cp command)
Jan  1 10:46:26 ubuntu kernel: [  315.720759] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jan  1 10:46:37 ubuntu kernel: [  326.996585] eth0: link down
Jan  1 10:46:37 ubuntu kernel: [  326.996984] ADDRCONF(NETDEV_UP): eth0: link is not ready

(sudo modprobe 8139cp command again)
Jan  1 10:48:15 ubuntu kernel: [  424.739376] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Jan  1 10:48:19 ubuntu syslogd 1.4.1#21ubuntu3: restart.
Jan  1 10:48:39 ubuntu kernel: [  448.583057] eth0: link down
Jan  1 10:48:39 ubuntu kernel: [  448.583444] ADDRCONF(NETDEV_UP): eth0: link is not ready

(sudo modprobe e100 command)
Jan  1 10:50:11 ubuntu kernel: [  540.080300] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Jan  1 10:50:11 ubuntu kernel: [  540.080306] e100: Copyright(c) 1999-2006 Intel Corporation
Jan  1 10:50:25 ubuntu kernel: [  554.775086] eth0: link down
Jan  1 10:50:25 ubuntu kernel: [  554.775484] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

The terminal output for each of these is as follows:
```

kevin@ubuntu:~$ sudo ifup eth0
[sudo] password for kevin:
ifup: interface eth0 already configured
kevin@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5191
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:1e:17:2c:62
Sending on   LPF/eth0/00:80:1e:17:2c:62
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:1e:17:2c:62
Sending on   LPF/eth0/00:80:1e:17:2c:62
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
kevin@ubuntu:~$ sudo modprobe -r 8139cp
kevin@ubuntu:~$ sudo modprobe 8139cp
kevin@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                             There is already a pid file /var/run/dhclient.eth0.pid with pid 5294
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:1e:17:2c:62
Sending on   LPF/eth0/00:80:1e:17:2c:62
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:1e:17:2c:62
Sending on   LPF/eth0/00:80:1e:17:2c:62
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                                            [ OK ]
kevin@ubuntu:~$ sudo modprobe -r 8139cp
kevin@ubuntu:~$ sudo modprobe 8139cp
kevin@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                             There is already a pid file /var/run/dhclient.eth0.pid with pid 5503
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:1e:17:2c:62
Sending on   LPF/eth0/00:80:1e:17:2c:62
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:1e:17:2c:62
Sending on   LPF/eth0/00:80:1e:17:2c:62
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                                            [ OK ]
kevin@ubuntu:~$ sudo modprobe -r 8139cp
kevin@ubuntu:~$ sudo modprobe e100
kevin@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                             There is already a pid file /var/run/dhclient.eth0.pid with pid 5674
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:1e:17:2c:62
Sending on   LPF/eth0/00:80:1e:17:2c:62
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:80:1e:17:2c:62
Sending on   LPF/eth0/00:80:1e:17:2c:62
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


Also, I now have access to a machine that can use floppy drives.  I remember that some of the boot CDs (maybe including the diagnostic CD from Dell) seemed to have simpler instructions for creating bootable floppies.  Since the Windows machine I'm using right now has a floppy drive, I can take advantage of those as well.

Now that I am in a new location, I'm going to try booting from the Live CD, just to check things out with my new modem (Linksys rather than D-Link, although it seems the modem is not the problem).  I don't think that this will give any different results, but I figure why not try?  I'll make a post if this yields anything interesting.

---

### Post by boobahzone on 2008-01-01
I ran Ubuntu via the Live CD one more time and ran the ping commands one more time.  When I did it, I got the same "network unreachable" error messages as I described several posts back.  I don't know why I got this message.  I connected the ethernet cable before I booted.  Then, when I noticed that the network was not automatically connecting, I opened the Network Manager and made sure "dhcp" was selected.

I don't know if this is important or not, but here is what I got:

```

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8752 (8.5 KB)  TX bytes:8752 (8.5 KB)

ubuntu@ubuntu:~$ ping -c 4 208.67.222.222
connect: Network is unreachable
ubuntu@ubuntu:~$ ping -c 4 192.168.1.1
connect: Network is unreachable
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:1E:17:2C:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8752 (8.5 KB)  TX bytes:8752 (8.5 KB)

ubuntu@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: p
        Current message level: 0x00000007 (7)
        Link detected: no
ubuntu@ubuntu:~$ 

```

As I said, this may not be important and may have to do with something else besides the main problem I'm experiencing.   I really don't know...

---

### Post by rkd on 2008-01-01
Hmmm. I don't know why sometimes it says "network unreachable" but other times it says "destination host unreachable".  I mean, I understand what the two messages mean; I don't understand why the network doesn't come up at all sometimes (network unreachable), but comes up partially other times (host unreachable). Odd behaviour, but maybe it is that I just don't understand the details of Linux networking enough yet.

I will try to follow the steps to create the CD with the Dell diagnostics and see whether I can figure out a way to get past the problem you are having with that. Right now, I'm busy doing some stuff for my wife, so I probably won't get to try that today, but I'll do it the first chance I have.  Your idea to try setting up a floppy disk with the diagnostics is a good one. Maybe you can get that working before I can figure out how to make the CD.

I'm not very surprised that the experiments with ifup and with modprobe didn't get it working, but they were simple things to try, so I figured we should see what happens. One good bit of information they showed: It does try to do the DHCP stuff when you restart the network. I don't know why that doesn't show up in syslog -- it does on my Ubuntu 07.04 system. But at least we now know that the DHCP software is doing its thing. I assume the only reason it isn't working is because the underlying network stuff isn't working. Once we get that fixed, I'm pretty sure the DHCP stuff will work properly to configure the network.

That WARNING you are getting at startup means (according to a list of Dell messages I found) that the hard drive's controller has reported to the motherboard that it thinks the hard drive is failing. The description didn't give any more details. That might mean that your hard drive is not long for this world, or it might be relatively harmless -- I have no way to tell.  It does seem a little strange that Windows couldn't boot, but Ubuntu can. Perhaps one of the critical Windows files got messed up at the time that the disk had the problem that the disk controller is remembering.  It might be that if you had the Restore CD for the computer and reloaded Windows, it would boot properly.

Maybe the diagnostics disk has a disk diagnostic that could tell us more about the disk problem.  Failing that, at least some of the hard disk manufacturers have diagnostic programs you can download from their web sites. We could look into that once we get the network problem fixed. 

I think it is not likely that this problem is directly related to the problem with the network not working. It might be indirectly related if some external event, such as a minor power surge, damaged both the hard disk and the network controller at the same time, but I think the chances of that are small.  It's not impossible, but small.

Do be careful when switching the monitor between the computers. I imagine it is the older, analog connector (the 15-pin kind). It is best if you make that switch when both computers are turned off. Maybe that is how you've been doing it.

I think the best next thing to try is the diagnostics to see what they say about the network controller. I'll try to figure out the problem you had creating the CD for the diagnostics. If you can get them onto a floppy before I get to work on that, so much the better. If I think of anything else, I'll post it.

---

### Post by rkd on 2008-01-04
Sorry for the long time since the last post. I had a bunch of unexpected things come up at the same time.

I was able to make a bootable CD with ImgBrn, and I'll describe the steps, but I also tried the approach of using floppy disks, and that is much easier. I'd recommend using that approach if your floppy disk drives on both computers are working properly.

First, the easy way: When you follow the link from the bay-wolf site to Dell and get to the page for the Dimension 4550, if you choose the download for diagnostics on floppy disk, you'll download a file named CD122000.EXE. To use it, you need 4 formatted floppy disks.  If you have brand-new floppy disks that haven't been formatted before, format them before running CD122000. When ready to put the diagnostics onto the floppies, double-click the CD122000.EXE file and put the floppies into the drive as the program prompts you.  Be sure to number them.  Then, on the Ubuntu computer, boot from the first floppy, and give it the subsequent floppies as it asks for them.

At that point, you'll be in the Dell diagnostic program, but I can't tell you any more, because the program checks to see whether the system it is running on is a Dell system, and refuses to run if not. I have no idea what the interface to the program looks like, how you tell it to test the LAN card, or anything. I notice that a couple of the files in the DIAGS folder are named NICxxx. LAN controllers are sometimes called NICs (Network Interface Cards), so if the diagnostic program uses that abbreviation, now you know what it means.

Jump down to the part following the directions for making the bootable CD with ImgBrn for closing thoughts.

Now I'll tell you how to make a bootable CD containing the diagnostics. It boots on my computer and enters the diagnostic program, but, again, it sees it is not running on a Dell computer and refuses to go any further.

The trick with ImgBrn is that it only writes image files to a CD. You must first create an image file containing what you want on the CD (using the Build mode), then copy that image file to the CD (Write mode).

1. Start ImgBrn.
2. Go to the Mode menu and select Build.
3. Go to the Output menu and select Image File.
4. On the right part of ImgBrn's window, click Options.
5. Select ISO9660+Joliet.
6. Tick the boxes for Recurse Subdirectories, Include Hidden Files, and Include System FIles.
7. On the right part of ImgBrn's window, click Labels.
8. Put RESOURCE_CD into the ISO9660 and the Joliet boxes.
9. On the right part of ImgBrn's window, click Advanced.
10. Click Bootable Disc.
11. Tick the Make Image Bootable box.
12. In Emulations, select "Floppy Disk (1.44 MB)".
13. In the Boot Image box, type the full path for the BOOT.img file that you got from bay-wolf, or click on the little icon to browse to that file.
14. Click Restrictions.
15. Click ISO9660.
16. For Folder/File Name Length, choose Level X.
17. For Character Set, choose Standard.
18. Tick the boxes for:
        Allow More Than 255 Characters In Path
        Allow Files Without Extensions
        Don't add ';1' Version Number To Files
19. Click Joliet.
20. For Folder/File Name Length, choose Level X.
21. Tick the box for Allow Files Without Extensions.
22. On the left side of ImgBrn's window, in Source, use the icon for browse for folder to select the DIAGS folder you got from bay-wolf and into which you expanded the file you downloaded from Dell (CDD1220.EXE).
23. Also in Source, use the icon for browse for file to select the files you got from bay-wolf: DELLDIAG.BAT, DIAGS32.BAT, and DOSMENU.BAT.  Bay-wolf's directions say to include BOOT.IMG here, too, but it isn't needed. (I tried it both with and without and it seems to work the same both ways.)
24. On the left side of ImgBrn's window, in Destination, fill in the full path name of the image file you want to create, or browse to a folder and fill in a name for the image file that you want to create.  This is the file you later will write to the CD.  It will get the extension .iso automatically.
25. Click the green triangle below the Destination box.
26. You'll see one pop-up that tells you how many files and folders it is putting into the image. Click OK. You'll see another pop-up that says it is done. Click OK.
27. Go to the Mode menu and choose Write.
28. In Source, browse to the image file you just created.
29. Make sure the Destination is the CD writer you want to use (in case you have more than one).
30. If you want to have ImgBrn read the CD back to verify it after writing it, tick the Verify box.
31. Click the green triangle below the Destination box. It will write the CD.

When you boot from that CD, you'll have to respond to a prompt asking you whether to boot from the hard disk or the CD. Type 2 to boot from the CD.  After it is done booting, it presents a menu asking whether you want to run the diagnostics or quit. When you enter 1 to run the diagnostics, it loads the diagnostics program. And this is as far as I get because the diagnostics refuse to run on my computer.

End of directions for making the CD.

I didn't look for directions about running the Dell diagnostics, because I saw a notice somewhere (I don't recall where) that said the diagnostics were only to be run under the direction of a Dell technician.  So I doubt they publish any directions about using the diagnostics. 

You may have to make some guesses once the diagnostic program puts up its main screen if the choices aren't clear. There might be a choice to run all the diagnostics. That might not be a bad thing to do, except it might take a long time and might display a lot of information we'd have to dig through.  

There might be a way to run diagnostics on selected parts of the computer.  If it has such a choice, I hope it identifies the parts in a clear way.  If it identifies them in a way you can't decipher, post what it is asking and I'll try to help figure it out.

I think it is unlikely that you can cause any harm by experimenting with the diagnostics, except possibly if you run a disk test diagnostic that writes on the disk, and you can recover from that by reinstalling Ubuntu. So feel pretty free to try things.

That's all I can think of right now.  I'll watch for a post about what you learn when you try to use the diagnostics.

---

### Post by lisati on 2008-01-04
> **spiderbatdad said:**
> might have to configure the modem on a windows computer for dhcp then connect it at your point of use.

When I started using Ubuntu on my laptop, I'd already configured a D-link ADSL modem (a different model to that mentioned by the OP) and a Linksys router using Windows. Ubuntu 7.04 (Feisty) is able to connect without any hassles.

---

### Post by rkd on 2008-01-04
To lisati: 

Sometimes what you say is necessary, but in this case, we know the modem is doing DHCP because when he boots the Ubuntu live CD on another computer connected to the modem, the network connection comes up normally. So the problem here seems pretty clearly to be either broken hardware in the computer in question or that Ubuntu isn't accessing the hardware correctly.

---

### Post by boobahzone on 2008-01-05
Muchos muchos gracias, rkd.  Unfortunately, many things are popping up this weekend (albeit most of them are quite pleasant in reality).  I bought some floppies today though and will work through creating a diagnostic set of floppies and/or boot CD, then I will surely post the results on here when I get to them.  It may be a few days, however.  Thanks so much for all of your help!

---

### Post by boobahzone on 2008-01-05
Thanks rdk, the set of instructions you gave me to create the diagnostic CD were perfect.  I had no problems creating the bootable image then burning and loading the diagnostic CD in the Ubuntu computer.  

I don't know that the diagnostic CD ran any tests for the LAN, however.  I noticed the NIC files did in fact load as the system started up the diagnostic CD.  However, in the list of devices to test, the NIC test was not present.  I also noticed that the SYMTREE.INI file mirrored the diagnostic symptom tree that the diagnostic CD ran if I went into "symptom mode," however the options which appear in the SYMPTREE.INI file were not present when I ran the CD.  

Specifically, two lines that were missing when I ran the diagnostic CD program that were present on the SYMTREE.INI file in the DIAGS folder were:```

[SYMPTOM] [IEEE 1394 Device Not Functioning.]
ieee1394.mdm

[SYMPTOM] [Problems Accessing the Network.]
nic.mdm
nic8254x.mdm
```

This seems very peculiar, as I did notice that nic.mdm and nic8254x.mdm loaded when the diagnostic CD was starting up.  Could it be that if my machine isn't even recognizing the correct hardware, it doesn't display the options to test it in the diagnostic CD?

Since the diagnostic CD was pretty simple and just gave a list of devices to check, I ran all of the diagnostics except for the ones controlling things like CD/DVD player, mouse, monitor, etc.

Here are a list of the diagnostics I ran and the results I got:
[LIST=1]
[*]PCI Devices
-Testing these devices came up with a message for each device reading that the device was detected as present, but no test or diagnostic was run.  "There may be additional diagnostics for this devices in Delldiag or a vendor-supplied diagnostic, or facilities in the operating system test for this device."  The devices on this list were: NVIDIA GForce MX 420 NV17, Other Comm. Device, Audio Multi-Media, Ethernet Controller.
[*]System Board (PMA Controller, Real time clock, system timer, interrupt controler, system speaker, floating point unit)
[*]System Management (SMBIOS)
[*]Cables (Cable Detect Inputs)
[*]USB (Controllers 0-2, Logitech-USB Optical Mouse)
[*]Parallel Port 1
[*]Serial Port 1
[/LIST]

Hoping that if I were to find a way to run the NIC diagnostics I might find more information about the current problem, I started to format the floppy disks I bought the other day so I could create bootable floppies, just in case that method would allow me to runt he NIC diagnostics.  Silly me though, having not bought floppy disks in about 10 years I just now realized my Windows computer will not allow me to format MAC floppy disks... whoops!  I'm sure it won't be a problem to exchange them then test the system using bootable Windows-formatted floppy disks.

Anyway, that seems very odd that even though the NIC diagnostics were included, they were not showing up when I ran the CD both in the test-by-device mode and the test-by-symptom mode.  Perhaps this gives more information about the hardware problem my computer might be having?

Thanks again for your help!

---

### Post by rkd on 2008-01-05
Quick reply now -- I have to leave in a minute.

Mac diskettes are the same as PC diskettes.  If they say HD or High Density, or 1.44 MB or 2 MB (unformatted), they are the right kind.

I'm pretty sure you won't see any difference running the diagnostics from the floppies as from the CD, but it can't hurt to try.

Tell me a little more about what you see on the screen when the program has finished loading all the parts. Any menus at the top of the screen or buttons on the screen that might give more options? What does the screen look like?

The messages about 1394 not functioning and problems accessing the network sure sound like if a device doesn't seem to be working, you don't get to test it.

Don't know what else to try unless you can find more choices by playing around with the program.

Gotta go right now.  Back in a little while.

---

### Post by boobahzone on 2008-01-06
The program that runs from the bootable diagnostic CD, once loaded, allows for four options: express diagnostics, extended diagnostics, custom diagnostics, and symptom tree.  The express and extended diagnostics go straight into a standardized test, whereas the custom diagnostic and symptom tree display  a list of devices or symptoms.  On this list of devices and symptoms, anything having to do with LAN, Network Card, NIC, etc. were missing.  From the options that were available, you could just click that device and run all the diagnostics on that device, or sometimes you could expand the item and choose to run specific diagnostics/tests for the device if there were several diagnostics/tests to choose from for it.

 I played around with it yesterday and more today to see if I could uncover anything outside of these four options, but the program seems to run very simply, placing the available options in very easy to find spots.  Therefore, I think I can only run the options that were given to me, which I've included below.  The options for diagnostics are:

1. Express diagnostic: testing the 20-30 most commonly-needed diagnostic tests.

2. Extended diagnostic: I am assuming this tests everything that is available in the custom diagnostic that can be checked by the computer.

3. Custom diagnostic: included the following components to check
a. Processor (L1 cache, L2 cache, I/O APIC)
b. System Board (DMA Controller, System Speaker, Floating Point Unit)
c. System Management > SMBIOS (BIOS Info, Enviornment Info, I/O Info, Memory Info, Processor Info, System Info)
d. Video 
e. CDROM/DVD
f. Cables > Cable Detect Inputs (cable detection summary)
g. USB (Controller 0, Controller 1, Controller 2, Logitech-USB Optical Mouse)
h. Keyboard
i. Pointing Device
j. PCI Devices (NVIDIA GeForce 4 MX 420 NV17, Other Comm. Devices, Audio Multi-Media, Ethernet Controller).  All of these devices had one "testing" option called PCI Info.  I put "testing" in quotation marks because running PCI Info for these devices yielded a message saying that no diagnostic or test was performed, but the devices were detected as being present, as described in my last post.
k. Parallel Port 1 (Internal Test)
l. serial Port 1 (Baud Rate Test, Interrupt test, Internal Transmit Test)
m. Diskett Drive
n. Hard Drive

(FYI: I skipped the info on the devices like keyboard, hard drive, diskett drive, video, cdrom/dvd, pointing device since I figured these would have very little to do with the current problem.)


4. Symptom tree: Displayed common symptoms (e.g., "I cannot play my audio CD"), which if expanded would list a set of diagnostics/tests for that problem.  Again, anything having to do with NIC, Network Card, LAN issues, etc. was removed.



Since the diagnostic program might not even be detecting that the NIC is present, should I try purchasing another NIC and installing it into my computer?  I looked online and saw that they can be purchased for US$ 10-30, maybe it would work with a new NIC?

Thanks again!

---

### Post by rkd on 2008-01-06
It is a little surprising to me that Linux recognizes the NIC enough to load a driver for it, but the diagnostic program doesn't offer to test it. But only a little surprising. You probably haven't overlooked any option in the test program.

Even before you mentioned it, I was thinking that buying a new NIC might be the only option left. I can't think of anything else to try, and as you see, they aren't very expensive. 

I see some cards on Pricewatch under $5 that should be perfectly good. I'm not suggesting buying the cheapest card listed on Pricewatch, just because you don't know how reliable the seller is, but it does show that NICs are pretty much commodity items these days. When I was thinking about it before, I figured you'd probably be able to get a card for $10 to $15. Now I'll bet you can get a perfectly good one for under $10. If you want to ask me to check your choice before you order one, I'd be happy to do that. If there are some electronics stores near you that have NICs and you want to buy there to get one quickly, that's fine. I would be surprised if anything you found would not work with Linux (it would be a reasonable precaution to ask whether the seller knows whether it will work with Linux, but even if they don't know, it should be okay). If there is a used/surplus electronics store nearby you probably could get a good card at a bargain price. NICs don't wear out, though they could be damaged by static electricity or a voltage surge, so find out whether they will exchange if you find the card is dead or ask them to test it in one of their computers before you take it. They might not be willing to take the time to test it, since it is such a low-cost item, but if they won't exchange one you find to be dead, you probably should skip the deal.

Things I think you should watch out for: One is don't buy a card based on the old ISA slot. Your computer has only PCI slots. The second is don't get a NIC that is just 10 megabit speed - get a 10/100 (often called Fast Ethernet). Third is try to pick a card that is full duplex and autosensing. This isn't as important as the other points. Fourth is to make sure it has the RJ-45 kind of connector rather than BNC or the other kind I can't remember. And if it is a used card, take a close look at the RJ-45 jack to make sure it looks like the jack hasn't been damaged mechanically. Ask them for a LAN cable to plug in to be sure it goes in and out easily and seats securely in the jack.

When I looked at the manual on the Dell site, I didn't see any provision in the BIOS for disabling the integrated NIC. It might do that automatically when it senses another one plugged in, or it might leave the old one active. I believe that won't be a problem because we will be able to tell Linux which NIC to use if it sees two.

So, yes, I think it is time to declare the integrated NIC dead and get a replacement.

---

### Post by boobahzone on 2008-01-08
Success!  I now have an ethernet pci adapter installed that allows me to connect to the internet :)  I'm making this post on the Ubuntu computer now :)

Thank you so much for your help, rkd.  I appreciate all of your time and effort for helping me get started in the world of linux and Ubuntu.  I am so greatful to you, I want to bake you cookies or something for all of the great, specific help you have given me in this enormous post.  I don't know how I can repay you.

Thank you so much!

Kevin

---

### Post by rkd on 2008-01-08
I'm glad you finally got the network working. That was an odd failure -- half working and half not. You don't see that very often.

You're welcome of course, and your thanks is the only reward I want. I do this because I enjoy solving problems and helping people.

So enjoy using the computer and Ubuntu!

---

