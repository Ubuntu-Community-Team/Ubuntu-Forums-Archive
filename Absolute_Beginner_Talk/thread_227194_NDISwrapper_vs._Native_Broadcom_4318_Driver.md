---
title: "NDISwrapper vs. Native Broadcom 4318 Driver"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Bruhthakuga on 2006-08-01
Ubuntu Friends,
     I have a Compaq V2570NR (V2000 series) notebook that I have installed Ubuntu on.  I want to get my Broadcom 4318 wireless card up and need information so that I can make a decision on what method is best for me to use:  What are the Pros and Cons of using the NDISWrapper and the native driver methods of getting my wireless card up?
     Please use text book like lanquage as I do not know Linux or the IT slang nor chat talk.  I thank you in advance for you clear concise answers.
Sincerely Bruh.
P.S. What you know and what you suspect are both wanted but please, I need to know which is which.

---

### Post by bcl on 2006-08-01
I'm running the native bcm43xx driver on my V2401 (Compaq Presario) with Ubuntu 6.06 LTS and it works -- most of the time. I had to use fwcutter to extract the firmware code from the windows driver (I dual boot, so this wasn't too much trouble) and I had to customize the bootup.

In /etc/network/interfaces I changed the eth1 entry to look like this:

```
auto eth1
iface eth1 inet dhcp
    pre-up /usr/local/bin/setup_802.11

```

And setup_802.11 looks like this:

```
#!/bin/bash
/sbin/ifconfig eth1 up
sleep 1
/sbin/iwconfig eth1 ap any
sleep 1
/sbin/iwconfig eth1 rate 11M
sleep 1
/sbin/iwconfig eth1 mode managed
sleep 1
/sbin/iwconfig eth1 essid linksys
sleep 1

```

I am still not sure if all those sleeps are needed, but it works more reliably since I added them. 

I previously used ndiswrapper under Fedora Core 4 on this laptop and never had any problems with it. If the native setup continues to cause problems I will try ndiswrapper under Ubuntu.


Brian

---

### Post by Jagot on 2006-08-01
The native drivers never seemed to work with me, so I blacklisted them to use ndiswrapper:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by Bruhthakuga on 2006-08-01
You trying to blow my brain cell?  I am having trouble with the fwcutter thing.  I know I can learn this Linux thing but I need clear lanquage.  Most of the help I find on the Linux subjects I look for is usually in a lanquage That is not conducive to a newbie learning easily.  IT slangs, chat talk and missing words make it tough.  from what I gatter when people talk about "Code" they mean to enter it into the "Terminal".  It seems to be the equivilant of the "command Prompt"?  I can do that.  It is somewhat like BASIC computer lanquage or dos.  The fwcutter thing is something else, how do I do that?  exactly where am I extracingt the firmware code from?

---

### Post by MarkSheely on 2006-08-02
I would avoid the native driver and messing with firmware.  Instead, try the method below:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

It is written in very plain language - you shouldn't have much trouble following it.

--Mark

---

### Post by MarkSheely on 2006-08-02
Sorry, accidentally double posted.

--Mark

---

### Post by Bruhthakuga on 2006-08-11
[SIZE="4"][COLOR="DarkOrchid"][FONT="Times New Roman"]I tried everything to get the native driver to work, heck, i even went outside naked put my thumbs under my arm pits walked in circle with my nees bent and walking, quacking and flapping like a duck and still it didn't work, so I switch to GENTOO.  I'll tell you one thing about GENTOO, it'll teach you a lot about Linux and PCs.  Needless to say I am back to try some more.  NDISwrapper or Bust[/FONT][/COLOR][/SIZE]

---

### Post by spd106 on 2006-08-11
If you need specific pointers or just want to find more information on these two differnet methods please have a look through the hardware networking and wireless subforums.

From what I've seen it depends very much on which card revision you have and just how lucky you are. 

NDISwrapper is a more general driver helper since it uses the windows driver that comes with every card. So for most people it is a lot easier to use and performs better at the moment.

BCM43xx appear to need more technical knowledge and is currently restricted to 802.11b speeds. However it should allow better support for your card as development progresses.

---

### Post by msak007 on 2006-08-11
I have a card with a Broadcom 4306 chipset, but just wanted to give another vote to using ndiswapper. I'm using it instead of the native driver for the reasons spd106 already stated - the native driver is restricted to 802.11b speeds, whereas ndiswrapper allows me to use the card at 802.11g speeds. Ndiswrapper is also easier to set up.

---

### Post by Bruhthakuga on 2006-08-12
I have just done a fresh install of Ubuntu then I 
Updated Synaptic Package Manager
Run Update Manager
Install NdisWrapper-utill
Copy bcmwl5.ing & bcmwl5.sys  from /media/hda1/Program Files/Broadcom/Broadcom 802.11/Driver and place them on the Desktop.  Next I entered the following code and got the following results.
[COLOR="Blue"]n@n-laptop:~$[/COLOR] **ifconfig**[COLOR="Blue"]
	eth0      Link encap:Ethernet  HWaddr 00:16:36:2C:7D:F2
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe2c:7df2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:971888 (949.1 KiB)  TX bytes:235604 (230.0 KiB)
          Interrupt:217

	lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)[/COLOR]

I noticed that there is no listing for “eth1 above so I check the network Monitor and get an ereor message, “SIOCGIFFLAGS error: No such device”.  I then check the Network Setup and there is a icon for the wireless card, eth1 but it is not active.  I check the “interfaces” file in the /etc/network folder with a text editor it says:
[COLOR="Blue"]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/COLOR]
I am just going to read a lot stuff before I finish up. I have been getting bits of info from differant post and that just don't seem good. I noticed a few of people are giving bad advice.  It would be nice if I could have someone on the phone or a messenger during my configuration process.  I understand the impulse to give instruction in a relaxed manor, kinda makes you feel like you got it going on but computers are an exacting machine, exact syntax are needed to get things right.  Some guys don't give code that can be cut and pasted, they just give a quick answer, not good.  I can learn this as well as any normal person. I am a newbie and if you remember that is a cloudy time, you know you can do it is just getting some basics to found your progress on. Fellas, re-read you instruction a time or two before you post them, make sure that they are sinple and clear for the newbies or at lease put the simple clear on the end.

---

### Post by MarkSheely on 2006-08-12
I would suggest following the method outlined here:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

In that thread, a method is outlined step-by-step in plain language that you won't have any problem following.

If you continue to have problems, send me a pm and I'll help you out over the phone.  I'm sorry you haven't gotten your wireless working by now - I know it is frustrating -

--Mark

---

### Post by Bruhthakuga on 2006-08-17
Friends,
     I know why I have not gotten my Broadcom 4318 wireless card to work not matter what I do.  My cooling fan is not working and it was causing all kinds of problems.  I have installed Ubuntu many times and it didn't work the same after each install.  This is the second time I had to send it back to get the fan working since I've bought this Compaq Presario V2570NR Notebook.  The first time they sent it back with a down graded CPU, I sent it back and they sent it with a CPU upgraded from the original.  I believe that the fan not working is a motherboard thing and so I may end back up with the original tourion ML-32, bummer.

---

### Post by leohart on 2007-10-07
I used the native driver for a long time (about 6 months + some more on another computer) and although it does work most of the time, it is kindda on and off. My campus wireless network has multiple APs with the same ESSID. This cause the native driver to work inconsistently. I got dropped and then on and then dropped and then on again. 

I switched to ndiswrapper today and haven't experienced a single issue since. So I have to say that ndiswrapper is actually doing quite well :-) Just my 2 cents.

---

### Post by euler_fan on 2007-10-07
I've always used ndiswrapper and the only issue is occasionally after switching AP's with the same name I can't connect.

---

