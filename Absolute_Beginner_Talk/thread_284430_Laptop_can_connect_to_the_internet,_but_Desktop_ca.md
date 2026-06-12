---
title: "Laptop can connect to the internet, but Desktop can not."
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-25
I have a laptop computer and a desktop computer here. If I connect my laptop to the modem directly with a CAT5 cable, I can access the internet just fine (as you can see from me posting here ;) ) however if I run the CAT5 from the modem to my desktop, I can't connect to the internet at all. Both computers are set with DHCP in the network panel. Both computers are running Dapper Drake, although the desktop has never been online yet, so it hasn't gotten any updates in anything.

Anybody have any troubleshooting steps I can take to figure out what's up? Command line is perfectly fine with me as well. :mrgreen:

---

### Post by TitusDalwards on 2006-10-25
on your desktop computer does ethernet modules installed correctly while sytem is booting? if i were you i pluged the network cable and reboot the computer

---

### Post by nickpaton on 2006-10-25
When you plug the cable into the desktop, reboot it and then see if it connects to the Internet.

If it doesn't please can you post the results of the following commands:

```
ifconfig
```

This lists all your active Ethernet ports.

You could also send us the list of all components fitted in the PC:

```
lspci
```
(first letter lower case L)

---

### Post by UnknownVariable on 2006-10-25
All entries when booting gave an **ok**. :)


Edit: Nickpaton, just saw your post. Just a second, as I'll have to manually type out the results on my laptop. :)

---

### Post by UnknownVariable on 2006-10-25
```
[font="Courier New"]
alexander@degre-desktop:~$ ifconfig
eth1       Link encap:Ethernet  HWaddr 00:0C:41:ED:92:28
           inet6 addr: fe80::20c:41ff:feed:9228/64 Scope:Link\
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:479 errors:0 dropped:0 overruns:0 frame:0
           TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:29932 (29.2 KiB)  TX bytes:2178 (2.1 KiB)
           Interrupt:5 Base address:0xe800

lo         Link encap:Local Loopback
           inet addr:127.0.0.1 Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:87 errors:0 dropped:0 overruns:0 frame:0
           TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:6340 (6.1 KiB)  TX bytes:6340 (6.1 KiB)
[/font]
```

Looks like there's a lot of devices in the lspci check. I guess I wasted time typing out the previous hunk of code then, as I went and got my USB flash drive to copy and paste this bit below. :lol:

```
[font="Courier New"]
alexander@degre-desktop:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (r ev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 10)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a )
0000:00:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev  0a)
0000:00:0c.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet  10/100 (rev 11)
0000:00:0d.0 Ethernet controller: Broadcom Corporation BCM4211 iLine10 HomePNA 2 .0 + V.90 56k modem
0000:00:0d.1 Computer telephony device: Broadcom Corporation BCM4212 v.90 56k mo dem
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
[/font]
```

---

### Post by nickpaton on 2006-10-25
Just one thing - on the PC ethernet socket, is the green light on and the yellow light flashing?

If not you could have a faulty ethernet connection - I say this because I had this and tried a new CAT lead which solved it.

Also, go into System>Administration>Networking.  Is your "Wired connection" shown?
Does it have a tick beside it?  If not click for the tick, click on Properties and tick "Enable This Connection".  
Also select "Automatic Configuration (DHCP) OK out and OK again to close Network Settings box.  
Reboot and see if it connects.

---

### Post by nickpaton on 2006-10-25
Mmm seems to show that you network card is working OK as Eth1.

Can you carry out the checks in my previous post & get back.

can you also try a ping:

```
ping 127.0.0.1
```

What router do you have?  We'll try an access the router next.

*[SIZE="1"]Edit: Added ping and router request[/SIZE]*

---

### Post by UnknownVariable on 2006-10-25
There's two lights, a green and a tan-orange-yellow, but the green one is flashing and the other is stable.

In the network settings, my ethernet connection is indeed shown, it is indeed active, and the "Enable this connection" is indeed ticked. The configuration is set to DHCP, and the default gateway device is set to eth1 (same as the eth connection).

I reboot the computer, and... Still nothing. :(

See, this is my mother's computer. She had a dead install of windows on it and had lost the activation key for it, so I told her it was either buy a new copy of WindowsXP or let me install Ubuntu and make her computer experience much more fruitful. ;) She seemed cool with the idea, so I went and installed it for her. She had *two* ethernet cards in the computer, because a microsoft tech apparently said she'd need two of them. I told her only one was needed as (obviously) the secondary one was just being left there. She told me I could take one out and keep it for myself. :)

That being said, I do have the second ethernet card in the other room if you'd like me to swap them and try all of this again. :)

---

### Post by UnknownVariable on 2006-10-25
Here's the ping results:
```

alexander@degre-desktop:~$ ping -c 5 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.056 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.051 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.059 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.060 ms

--- 127.0.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.051/0.059/0.069/0.005 ms

```

Also, the router I was using for a year and a half just bought the farm yesterday, so I had my mother order [this one](http://www.newegg.com/Product/Product.asp?Item=N82E16833124190) as a replacement. It's not here yet, so we're trying to get a direct connection to the cable modem up and running. :) It works with the laptop, but not the desktop.

---

### Post by nickpaton on 2006-10-25
Misposted

---

### Post by NetworkGuy on 2006-10-25
If you are connecting the cable to a DSL/Cable modem you must reboot the modem each time you connect it to a different network card.

---

### Post by nickpaton on 2006-10-25
What is the make model of the modem?

---

### Post by UnknownVariable on 2006-10-25
Network Guy: I haven't had to reboot it once while switching the cable between laptop and desktop and it's still worked just fine. I'll test it out in a minute just in case, however.

nickpaton: The modem is a SURFboard SB4100 Cable Modem. :)

---

### Post by UnknownVariable on 2006-10-25
Results: Shutdown the desktop, turned off the cable modem, connected the two with a CAT5, turned on the modem, turned on the desktop, and still no internet on it. Simply moving the CAT5 from the desktop to my laptop gives me a connection here on the laptop instantly.

---

### Post by nickpaton on 2006-10-25
I've looked up various specs on the router but cannot find its IP address.

Another way to get it - System>Administration>Network Tools>Devices

In Network Device drop down can you select Ethernet Interface Eth1.

Under IP address can you give me that address.  This is your PC's one, and the router will be close to that to within a digit or two.

The router could be something like 192.168.0.1 or 10.0.0.1

Can you open a browser and type in the number you think it may be and see if you can get into the router.

I'm frankly clutching at straws here.  I feel you are V close to solving it though.

---

### Post by UnknownVariable on 2006-10-25
I don't own a router right now, nick, sorry. :) It's just this:

```
Cable Modem <-[---cat5---]-> Ethernet Port on Desktop
```

Would you like me to post the information that *is* present in that tab, however?

---

### Post by nickpaton on 2006-10-25
Sorry M8 my error - when I say router I mean modem!!

Yeah please if you could post the details

---

### Post by Henry Rayker on 2006-10-25
One foolish question...when you open your network manager, it is trying to connect using eth1, correct? I used a live cd on my desktop and had a similar situation...ethernet port is identified as eth1, but the network manager was trying to connect on eth0.

---

### Post by UnknownVariable on 2006-10-25
No problem. :) I thought I had mis-posted something along the line. :lol:

See the attachment for the screenshot. :mrgreen:




**Edit:**
Henry: It identifies and tries to connect to "eth1" :)

---

### Post by NetworkGuy on 2006-10-25
Unknown:  Who is your ISP?

---

### Post by UnknownVariable on 2006-10-25
NetworkGuy: Cox Communications in Rhode Island. :)

---

### Post by NetworkGuy on 2006-10-25
Has this Internet connection always worked with the laptop?   

I'm not familar with Cox but I have seen some ISP's setup their network so that only network cards known to it can get an IP address. (But it's been a while)  The ISP looks at your cards MAC address as it attempts to get an IP address and if it isn't on the servers list, you don't get anything.

---

### Post by UnknownVariable on 2006-10-25
I've connected dozens of random laptops and desktops direct to the modem and all have received an internet connection, including the desktop I'm having a problem with now. Of course, they all had windows installed as the OS though.

I'm more than sure Cox isn't sniffing at my MAC addresses. :mrgreen:

If it's of any relavance, the desktop is older than the laptop and therefore has been getting an internet connection through the modem for a much longer time than the laptop has. It worked previous to ubuntu-installation, so I assume that there's something up with the network card through ubuntu. Just a guess though.


Also, I'd like to thank everybody for taking the time to help me with this. :) I appreciate it.

---

### Post by NetworkGuy on 2006-10-25
Next Question

Did this network card work when it was Windows XP?  [COLOR="Magenta"]oops - I re-read your last post - That answered this question[/COLOR]

I don't believe you stated what type of network card it is.  That might have something to do with your problem.  For instance:  Broadcom cards look like they should work, but the linux drivers aren't quite ready for prime time and you usually end up having to install the Windows drivers with NDISWrapper to get them working.

---

### Post by nickpaton on 2006-10-25
> **UnknownVariable said:**
> No problem. :) I thought I had mis-posted something along the line. :lol:

See the attachment for the screenshot. :mrgreen:




**Edit:**
Henry: It identifies and tries to connect to "eth1" :)

The screen shot doesn't show a connection to the modem; my modem router's address is xx.xx.xx.02, and when I have a look at network devices it lists it as xx.xx.xx.03, which is the laptop's address.

There's nought listed in your screenshot, which seems to point more at a problem between the PC and the modem.

I have found this post which may be worth working through.  It is for a particular network card, but others have reported that it works on other makes as well.

[http://www.ubuntuforums.org/showthread.php?t=186430]("http://www.ubuntuforums.org/showthread.php?t=186430")

Unfortunately I have to go to bed, but good luck and hope you'll be up and working V soon.

---

### Post by nickpaton on 2006-10-25
@ Network Guy: he listed it on page one when he did a lspci as:

0000:00:0c.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet  10/100 (rev 11)

---

### Post by UnknownVariable on 2006-10-25
I have two network cards here (one I had taken out though).

Both are linksys. The one that's currently in reads as follows:
```

LINKSYS
Model No.:LNE100TX
Version 5.1

```
And the second one which is currently out of the slot reads as follows:
```

LINKSYS
10/100/1000 Gigabit Network Adapter
Model No: EG1032 ver.2

```

:)

---

### Post by nickpaton on 2006-10-25
Try swapping the cards over as you yourself suggested earlier (it's too exciting to go to bed!!LOL)

---

### Post by UnknownVariable on 2006-10-25
NetworkGuy: Also, yes, I'm sure these cards worked under Windows XP. One card was preinstalled when the computer was purchased. I assume drivers for it were already installed and / or located on the Windows restore disc. The second card was bought separately and did not include a disc with any drivers, strangely. It still worked OOTB though.

Nickpaton: Thanks for the link, I'll read through it in a bit. I checked the devices tab on my laptop and while it doesn't show an IP address of the modem itself, it does show my outside IP address (something that doesn't happen on the desktop). Just thought I'd include that as a tidbit of info. :mrgreen:



**Edit:** lol nickpaton. :) Just a second, I'll post the results.

---

### Post by NetworkGuy on 2006-10-25
OK, did a google search.  

It appears that this card uses a "tulip" driver which should be in the kernel automatically.  One thing I am not is a kernel expert.  

I've also googled people having problems getting this board working.  Weird errors that never seem to get solved.

Unknown:  Do you have another network board you could use?  - [COLOR="Red"]OK, I'm a step or two behind both of you in this thread[/COLOR] :)

---

### Post by nickpaton on 2006-10-25
For information only but could be useful.

The way to read what your modem's IP address is, if it's connecting to it:

```
sudo gedit /etc/resolv.conf
```

Should get a single line with "nameserver xx.xx.xx.xx"

It does seem to be one of those weird faults.

Is it easy for you to simply to a reinstall of the distro when connected to the modem?

---

### Post by UnknownVariable on 2006-10-25
I swapped the cards, and now the tan-yellow light is blinking, the green one is **completely off**, and there's no internet connection. System > Administration > Networking recognizes the ethernet card. Networking Tools does not display my IP address (laptop does though).

I seem to collect install discs of Ubuntu, so a reinstall while connected to the modem would be easy enough to do. :) I'm not sure how long you guys want to hang around and wait for it to be finished though. :lol:


nickpaton: I did the command as you said, but the document is empty. I double-checked to make sure I was grabbing the right file from the right directory as you stated, and I am. A bit odd, I'd say. :lol:

---

### Post by nickpaton on 2006-10-25
Did you reboot both the PC & modem?

The empty box indicates no connection to the modem.

I'd honestly say that a reinstall would be best.

I'll be around in about 10 hours time if I don't go to work (looking that way in any case!!), so I will check then, but yeah I'll be around until the end no worries!

Cheers and good luck and good night to you all  Nick

---

### Post by UnknownVariable on 2006-10-25
Rebooted both the PC and modem and gave it another go, resolv.conf is still empty, unfortunately. 

Thanks for the help though, Nick. Looks like I'll be seeing you in about ten hours. :lol:

---

### Post by macdo on 2006-10-25
Just a thought, born of my own (very different) trials with a network connection...

Try this :
```
sudo ifdown eth1
sudo ifup eth1
```

You could also try disabling IPv6 - that shouldn't help, but having read the whole thread, I'm at a loss to see what would.

Since you've started having probs, have you ever managed to connect with that network card?

---

### Post by UnknownVariable on 2006-10-25
No internet on it yet.

The network card did work with windows xp, but this is the first time trying to get it to work with ubuntu. :)

---

### Post by UnknownVariable on 2006-10-25
Bumping from the third page of threads. :)

---

### Post by NetworkGuy on 2006-10-25
Hmmm..  Is this new card still using eth1.

What does a ifconfig show.   Maybe the card is eth0 or eth2 and just needs to be "up'ped"

---

### Post by UnknownVariable on 2006-10-25
Since swapping the two network cards, it's now recognized as eth0.

---

### Post by NetworkGuy on 2006-10-25
How about activating the card with sudo ifup eth0?   (You probably already tried that right? )

---

### Post by UnknownVariable on 2006-10-26
I did try that already, yes. It says it's active in the networking panel, as well. :)

( Sorry for the delay, I had to go to sleep, and now I'm at class. I should be home in two hours from this post. ;) )

---

