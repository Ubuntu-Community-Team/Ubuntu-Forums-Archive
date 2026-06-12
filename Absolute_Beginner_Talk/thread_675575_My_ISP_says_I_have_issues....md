---
title: "My ISP says I have issues..."
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by myolbug on 2008-01-22
Well Duplex mismatch issues, that is.

I was told that I should buy a switch or hub, as my computer is on a different setting than my mode, or something to that effect.  This is why I have a lot of lag while the DNS is getting resolved.  However, in a terminal, if I type in the actual numbered address, then it will go there immediately.

Any ideas?  Is there something I can change on my PC?  It is an old PC, circa 2000 or earlier, and I am running Ubuntu 6.06

Thanks

---

### Post by sports fan Matt on 2008-01-22
Im shooting in the dark, but you said your pc was circa 2000 or older..How much ram is in that puppy?  From what you are describing you are trying to connect to the internet?  And what DNS?  For example I have the dns from my network connection..I assume you are refferring to that

---

### Post by myolbug on 2008-01-22
The computer has 1 gig of ram with a 733mhz Coppermine processor.  My ISP said that due to the number of collisions, see here:
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:11 txqueuelen:1000
          RX bytes:15509861 (14.7 MiB)  TX bytes:2389909 (2.2 MiB)
          Interrupt:5 Base address:0xd400
Anyway, he said that I must be having issues with my computer having a different setting on 10/100 card than my modem?  Or something to that effect.  He said that the switch or hub would allow them to sync together at the same speed.
My collisions are only 11 right now, but before I rebooted, it was a much higher number.

---

### Post by dcstar on 2008-01-23
> **myolbug said:**
> The computer has 1 gig of ram with a 733mhz Coppermine processor.  My ISP said that due to the number of collisions, see here:
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:11 txqueuelen:1000
          RX bytes:15509861 (14.7 MiB)  TX bytes:2389909 (2.2 MiB)
          Interrupt:5 Base address:0xd400
Anyway, he said that I must be having issues with my computer having a different setting on 10/100 card than my modem?  Or something to that effect.  He said that the switch or hub would allow them to sync together at the same speed.
My collisions are only 11 right now, but before I rebooted, it was a much higher number.

The **ethtool** package will allow you to change the 10/100 settings on your card:

[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

---

### Post by wormser on 2008-01-23
It sounds like you are plugging directly into the isp's modem.  You should buy a router.  It is much safer to have a router between your computer and the internet.  Go to a pc recycle place to get one cheap if money is an issue.

---

### Post by myolbug on 2008-01-25
I have a Belkin 802.11g router, but I can't get Ubuntu to even recognize it.  I have never used one, how do I install?

---

### Post by wormser on 2008-01-25
> **myolbug said:**
> I have a Belkin 802.11g router, but I can't get Ubuntu to even recognize it.  I have never used one, how do I install?

Are you connecting with ethernet?  Who is your isp?  Unplug your ISP's modem, router and turn off your computer.  Plug the modem first. Next connect the router with ethernet and plug the power in.  Finally plug your computer into the router and turn it on.  Your computer should pick up an IP address from the DHCP server in the router.  Now you should be online.

---

### Post by myolbug on 2008-01-25
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
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000c5 (197)
        Link detected: yes
I tried the link above, but this is all I could get after altering the commands a little, but I was kind of guessing.
Better directions?

---

### Post by Zack McCool on 2008-01-25
> **myolbug said:**
> I have a Belkin 802.11g router, but I can't get Ubuntu to even recognize it.  I have never used one, how do I install?

Ubuntu doesn't need to recognize it.  Read the documentation.  Plug the Internet port of the router into your modem.  Plug your PC into one of the router's switch ports.  Boot the PC, and it will get an IP address.  Your router's manual should have directions for getting into the web configuration interface for it (IP address, password, etc.) so you can configure the wireless properties...

---

### Post by myolbug on 2008-01-25
I downloaded the maual from Belkin, but I must have a bad router, because nothing works.
I guess I'll have top buy a new one.

In the mean time, can I get some help with the info on the link above?  I will be buying a new computer soon, and i will just get a router until then...
I will have to rely on the firewall I have for now, I guess.

---

### Post by wormser on 2008-01-25
> **myolbug said:**
> I downloaded the maual from Belkin, but I must have a bad router, because nothing works.
I guess I'll have top buy a new one.

In the mean time, can I get some help with the info on the link above?  I will be buying a new computer soon, and i will just get a router until then...
I will have to rely on the firewall I have for now, I guess.

You should not have to use the link above.  Ubuntu works by default unless you have a hardware issue.  I doubt your router is broken.  It should work.  Did you do the steps in my other post?  Can you also answer the questions in that post.

---

### Post by myolbug on 2008-01-26
Anyone have better directions for a noob on getting the link working?
[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

---

### Post by mortsahl on 2008-01-26
If nothing else works, do a search on how to turn off ipv6 in ubuntu ... your modem might not support it and will cause the slow down problems you're seeing.

---

### Post by myolbug on 2008-01-26
I tried that, as that was recommended in a question I posted earlier.  It didn't make a difference.  I know that my eth card is set to half, though I don't understand the difference.  It is also set at Tbase 10, so, to the uneducated, it seems that it is set at it's lowest setting.
I could get part of the instructions to work, but it seemed to be assuming I had some understanding, which I guess I don't.  It seemed to be missing something.

If anyone can please piece it together for me, I would be really grateful.

Thanks

---

### Post by Tteddo on 2008-01-26
In my experience, when a network card is behaving like yours it is going bad. Ubuntu is pretty good about "just working" with wired cards. Do you have another network card you could try? Since it could be the cable modem also, is there another computer you could try it with?

---

### Post by myolbug on 2008-01-27
> **wormser said:**
> Are you connecting with ethernet?  Who is your isp?  Unplug your ISP's modem, router and turn off your computer.  Plug the modem first. Next connect the router with ethernet and plug the power in.  Finally plug your computer into the router and turn it on.  Your computer should pick up an IP address from the DHCP server in the router.  Now you should be 
online.

My ISP is Montana Digital, a very small company.  I have DSL 1.5 down, 512 up.  I am connected via ethernet.
I tried your suggestions and nothing.  I even tried to restart the router and the modem and nothing.  Whenever I try to use this I don't get through it, unless I am being a total idiot, and it is not working because I am trying to use it as a wired router, for only one computer, instead of having a wireless card.
Dunno what else to try.

---

### Post by swoll1980 on 2008-01-27
Set your dns settings manually make sure your router or modems ip address isn't included in the list then do this 
sudo chattr +i /etc/resolv.conf this will fix your problem this will lock your settings if you ever have to change dns use the same command but use -i instead of +i

---

### Post by kerry_s on 2008-01-27
> **myolbug said:**
> My ISP is Montana Digital, a very small company.  I have DSL 1.5 down, 512 up.  I am connected via ethernet.
I tried your suggestions and nothing.  I even tried to restart the router and the modem and nothing.  Whenever I try to use this I don't get through it, unless I am being a total idiot, and it is not working because I am trying to use it as a wired router, for only one computer, instead of having a wireless card.
Dunno what else to try.

have you tried using the reset switch on the back of the router? to connect to it type " 192.168.2.1 " you should get the log in screen (see pic1) just click login, the default there is no password. you should then be at the status screen (see pic2), you want to make sure it says connected (see pic3).

---

### Post by halitech on 2008-01-27
this may seem like a dumb question but after hooking up your router, did you check your IP address and confirm you have an IP from the router and not for some reason holding onto the old one from your ISP?

I don't think the fact you are using it wired with 1 computer has anything to do with it. I had 1 computer for a while and used the router with a wired connection and it worked fine.

---

### Post by myolbug on 2008-01-29
Okay,
I had my bro log into my computer and he found that , 1. I need to get a new NIC.  2.  My modem is only TBase 10, so, I guess i am a bit throttled htere.

The good news is that i got my router working, so that seems to be helping my original issue of "Looking Up ww. ...

I accomplished this by:
I opened networking and took a look there.
  Then I opened System-Admin-Networking Tools.  It was set to loopback interface, which I changed to Ethernet, then I hit configure, which I then changed it to DHCP.  I then went into Networking, and deactivated/reactivated networking, and viola.  It works

---

### Post by rkd on 2008-01-29
It is good to read that you've solved some of the problems.  Good going!

I wonder why your brother came to the conclusion that you need to replace your NIC.  That might be correct. He could have seen something that indicates it should be replaced, but none of the information you have showed us here in this thread definitely points to a problem with your NIC.  At least I don't notice anything that definitely points to a problem.

NICs are cheap ($10 to $15), so you it won't cost very much money to get a new one to see whether that fixes whatever problems you still have. Certainly go ahead and do that, if you'd like to try it.  But if you would like to investigate your current setup a little more before doing that, we certainly could do that.

The ethtool output you posted says that your NIC is operating at 10 megabits per second, which matches what you said your modem is.  That is good. Your DSL is 1.5 down / 512 up -- that means 1.5 megabits per second for transfers from the internet to you and 512 thousand bits per second for transfers from you to the internet.

Notice that 10 megabits per second is MUCH faster than your DSL connection, so your NIC's basic speed cannot be slowing down your network access.  

I'm dubious about the claim by the ISP's tech that your problem could be duplex mismatch or 10/100 mismatch. I see that ethtool output that you posted shows that your NIC supports any combination of 10/100 speed and half/full duplex, and supports auto-negotiation.  This means that your NIC will negotiate with the device at the other end of the network cable to work at the best settings that they both can support.

If the NIC is malfunctioning in some way, that could be causing problems, but none of the things the ISP's tech said seem to me to be the problem.  It would be interesting to hear what your brother found that makes him say you need a new NIC.

The fact that when you enter an address in the number form, it works well, and only is slow when you enter an address in the name form (which requires a DNS lookup to obtain the proper number form to use), seems to me to be a strong indication that the problem is that the DNS that your ISP is providing is the culprit.  They'd never admit that, of course.  There is a free alternate DNS that you (or anyone) can use. If you would like to try changing your configuration to use that alternate DNS, ask and I'll tell you how to do it.  It is not difficult (and it is easy to switch back if you decide not to continue with it).

Collisions are normal occurrences on an ethernet. They are a problem only if they reach excessive levels. You said that before you rebooted, the number of collisions was much higher than 11. To know whether that was a problem, we'd need to know what the higher number was AND the numbers in the TX packets line. I hesitate to condemn the ISP's tech outright, but sometimes they are pressured to handle calls quickly, and seize on any fact, relevant or not, to blame for the problem. I have a feeling that is what happened here. The tech could tell you are unfamiliar with the details of network connections (as most people are), so engaged in a little bafflegab to make you think there was something wrong with your equipment. Let me temper that by admitting that I'm not there and can't see what is going on, so there might be some indications of an actual problem with your equipment.  But that's not the way to bet.

So what do you want to do?

Do you want to try that free alternate DNS?

Do you want to get a new NIC?

Do you want to work on getting your wireless router working?

Are things working well enough that you are happy and don't want to fiddle with it any more?

One other thing: You mentioned in one of your posts that you would be buying a new computer soon. If you plan to do so because of the difficulties you mention in this thread, it could easily turn out that the new computer makes no difference. If you are buying a new computer for other reasons, then that doesn't matter.  

If you plan to use Ubuntu on the new computer, try to check that all the various components in the computer are easily supported by Ubuntu. That could prevent a lot of headaches in getting the new computer set up. The main components that are problematic are the video adapter, the sound adapter, the wireless adapter, scanners, and some printers. If you aren't sure how to check on the components, asking in the forums is a good start.

---

### Post by apostate on 2008-01-29
IF I May, a 10/100 mismatch should not ever be an issue in Ethernet, you can go from 10 to 1000, the latest Ethernet spec is still backward compatible. The network will work at the speed of the slowest node. A duplux mismatch should also be hard to get, unless you have a very new and powerful NIC and somehow set it to full, all home networks should just default to half, which is the prevailing ethernet architecture, a one lane country road.  You could have bad cables? Bad terminators might cause signal bounce I guess, but this seems unlikely in an Ethernet situation. Try new cables? If that doesn't help, I'm gonna speculate and say that indeed, your NIC is jacked up. It should "just work" as other posters have said.

---

### Post by myolbug on 2008-02-03
RKD and everyone else,
I apologise for the long delay in answering the help you've given.

I am interested in getting the alternate DNS. 

 Also, I may just be hanging on to this ol machine for a bit more.  When I go to Network tools i notice that the network Device is on Loopback Interface (lo) and I am given the option of Ethernet Interface (Eth0).  What does this do?  I can select (Eth0) from the pull down menu, but it doesn't seem to do anything, as it is defaulted to (lo).
On the Eth0, I can configure the connection settings to DHCP, which as posted above, I have, enabling my router, but Network Settings are always loopback interface.

Can anyone explain the difference if there is one?  Does this have anything to do with the occasional  looking up issue?  Also, is necessary to change the default to Eth0, or is it a seprate setting?
Also, since I have been using the router, my collisions are 0.  

I have so much to learn...:confused:

---

### Post by myolbug on 2008-02-03
One website that I ALWAYS get the  dreaded "Looking UP..." from is [www.answers.com](www.answers.com) no matter how often I go there.  Is anyone else affected by this?

---

### Post by rkd on 2008-02-03
The long delay answering is fine with us -- we don't try to hold you to any schedule.

The interface name that appears when you open Network Tools is not important -- it just makes a list of the interfaces it knows about and displays the first one by default. It has nothing to do with how the interfaces are being used for networking.

If you want to try the alternate DNS, do this:

Open a Terminal and enter these two commands:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
gksu gedit /etc/dhcp3/dhclient.conf
```
The first command will just make a copy of the file we are about to change, in case some accident while editing messes it up. The second command opens the file for editing. If you prefer a different editor, use your preference.

When /etc/dhcp3/dhclient.conf is open, go to the very end of the file and add the following line:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
Now save the file and exit the editor. Then in the Terminal, enter these commands:
```
sudo ifdown eth0
sudo ifup eth0
```
Wait a moment after the first command for it to finish taking down the connection, then enter the second command.

If everything has gone properly, you now will be using the alternate DNS. You can check that by opening the Network configuration tool (System -> Administration -> Network). Note, this is not the Network Tools tool. When Network opens, click on the DNS tab and you should see 208.67.222.222 and 208.67.220.220 as the first two lines in DNS Servers. You probably will see a third address below those two. That is one of your ISP's DNS servers, and name lookup will try to use it if the first two don't respond, but that probably won't happen because the alternate DNS is pretty good about keeping their response time up.  I don't remember whether I explained it, but this alternate DNS is called OpenDNS and is free for anyone to use. They make their money by selling additional services on top of this basic one and give away the basic service as advertising.

If after making this switch, you don't notice any improvement in speed, then perhaps I have misdiagnosed the problem and we'll have to look at it some more.

If you find you have more problems after the switch, just remove that one line from the end of the file and do the ifdown and ifup commands again and you will be back to your original state.

I just tried visiting [www.answers.com](www.answers.com) and it opened quickly for me (and I'm using the alternate DNS).

It is true that there is a lot to learn if you want to know everything needed to set up the operating system, but once you get things set up and working, you don't really have to understand it (or at least you shouldn't have to understand it). It is just like a car. You can use the car very well without knowing all the stuff the mechanic does to keep it running. You just have to have a computer mechanic to consult when you need help. We are your computer mechanics.

---

### Post by myolbug on 2008-02-07
RKD,
Thanks so much for the info.  I couldn't get it to work, the way that you said, but in looking at the DNS tab in Networking, I noticed that it had a provision for adding DNS addresses.  I simply clicked on the add button, then typed in the addresses you provided.  Then, I clicked on the new address, and drug it to the top.  It wouldn't go to the top level that way, but I was able to drag the top one under it, thereby placing the new one in first position.  I did this with the second address you gave me, and then used the Deactivate/Activate in the Networking window.  I then went to [www.answers.com](www.answers.com), and it INSTANTLY connected.\\:D/
I use that website a lot, in getting definitions to words, etc, and it has always been a major wait! No longer.
Again, thanks, I mean it, as my ISP was right in a way, that it was my machine.  I can't wait till the ground thaws, and I can get Cable Internet with 15Mbps, instead of 1.5:mad:

---

### Post by rkd on 2008-02-07
You're welcome, of course.

But setting up the alternate DNS in the Networking DNS tab is only a temporary setup.  Those settings will disappear the next time you boot the computer (assuming that you have specified DHCP in the properties on the Connections tab, which is the normal way to do things).

If you want to make the change permanent, describe what problem you had when following the directions I wrote, and I'm sure we can figure out what was wrong with the directions.

By the way, your ISP was not right -- the problem was not in your computer. The problem is that the DNS your ISP provides you is slow. Now that you are using the alternate DNS, instead of your ISP's DNS, things are working quickly. 

Getting 15 Mbps will be nice, but don't expect everything to be 10 times faster. Many things won't be any faster because the bottleneck is at the web site, not in your local connection. But, overall, 15 Mbps will be nicer than 1.5, for sure.

---

### Post by myolbug on 2008-02-07
This is the first message I get when I enter line two of the first set of commands:
(gedit:19986): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
After a bit of time, the editor opens.  However, in the terminal, the [email]randy@randy.ubun[/email]tu: never returns, so thatt I am not able to enter more commands.
So, I close he trminal, and re-open.  
When I entersudo ifdown etho, I get this message:

ifdown: interface eth0 not configured

When I go to bring the network back up, (it never went down) I get this:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:e0:18:0d:a2:64
Sending on   LPF/eth0/00:e0:18:0d:a2:64
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
mv: cannot move `/etc/resolv.conf.dhclient-new' to `/etc/resolv.conf': Operation not permitted
bound to 192.168.2.2 -- renewal in 945085706 seconds.

I can use networking to turn networking on/offf, but is this different?
When I go into network tools, and use lookup for the address given, 198.168.2.2 I ge the following info:
See attachment

---

### Post by rkd on 2008-02-07
Oh, it looks like you followed the suggestion back in post #17 to use chattr to make the /etc/resolv.conf file unchangable. So your manual DNS settings will not get replaced at every boot, and maybe we should just let it be that way. The changes I had described were to get the DHCP setup to put the alternate DNS addresses into effect on every startup.

I don't know why you got the error when trying to start gedit. Could it be that you have a Kubuntu system or some other flavor than the usual Ubuntu?

I also don't know why the ifdown command said eth0 wasn't configured -- it shows up plain as day in the messages about the DHCP startup.  Did you type eth0? That's a zero, not an o?

Turning networking off then on is roughly the same as ifdown and ifup, so that was a good substitute.

The messages that appear when you start the network are normal, except for the one that says mv: cannot move ...  That one is the result of the chattr command that made /etc/resolv.conf unchangable, so in your system, it is now normal, too.

Address 192.168.2.2 is an address within your local network (actually, the address DHCP gave to your computer), and so there should be nothing to be found by Networking Tools Lookup. I'm surprised it shows anything, but I believe whatever it shows is meaningless. I believe Lookup can only give meaningful results about public addresses, though there is a chance that I don't completely understand something about that.

So, given that you had used chattr to lock /etc/resolv.conf, my warning that it would be reset on every startup is wrong, so I think you don't have to do anything more to your PC to get it to use the alternate DNS permanently.  Do try to remember that you did that chattr command and how to undo it should you ever need to go back to using the DNS provided by the ISP.  For instance, you might want to try the cable's DNS when  you get the new service, to see whether it is better than the alternate DNS.  (It might be better; it might not.)

Looks like you are all set.  Enjoy using it!

---

### Post by MarkX on 2008-02-07
Maybe not relevant but I had a problem where I couldn't get any of the search engines on Ubuntu (but lots of "normal" sites) but could in XP from the same computer. After days of fuffing I updated the firmware on my Draytek router and that solved the problem. There is clearly something in Ubuntu networking that it can't cope with as well as XP can.

---

### Post by fatdadkev on 2008-02-16
Its not clear who your ISP is or how your connected to them.

As an example on the previous NTL/Virgin Cable boxes such as Teryon 210 they only link at 10mb on the internal network to the PC, you cannot get them to work any quicker.

Your settings are exactly what I would expect to see i.e autosense is on and to all intents the card is capable of 100mb but the ISP modem/router is not.

When I noticed this with my NTL modem I checked the specification on the manufacturers web site and it confirmed this as being 10mb only.

If you put a hub in or replace an ADSL modem with a combined ADSL router then you will link from your PC to the router at 100mb but your internal link to the final modem end may still be limited.
Bear in mind if your on an 8mbit ADSL for example your throughput is divided by 8bits so your maximum network speed will be about 1MByte/s so a 10mb network connection is fine as this would offer 1.25MByte/sec.

On NTL 20mb cable for example you need to perform the same calculation and divide 20 by 8 to get a true approximation to the throughput in MBYTES - this turns out to be 2.5MBYTES/sec, in this case a 10mbit network link is not sufficient to allow full use of the internet bandwidth available.

It's most likely your modem/router is 10mbit link so check that on the manufacturer web site first, then work from there - I can't see any reason your card won't link at 100mbits but bear in mind it won't speed up your internet unless your using 20mbit link at full speed.

---

### Post by rkd on 2008-02-16
fatdadkev:

You seem not to have read the thread all the way through before posting.

The name of the ISP was given in post #16.

There never was any hardware problem, at least as far as I could tell -- it was all misunderstanding and/or misdirection by the ISP's tech. The slow response was caused by sluggish DNS provided by the ISP. Switching the computer to use OpenDNS cured that problem.

You are correct that 10 Mbps ethernet is more than fast enough for a 1.5 Mbps DSL line, but that was explained in the thread two weeks ago.

---

### Post by myolbug on 2008-03-08
Has anyone had problems with OpenDNS?  I took the addresses off my computer when Google said that I was searching using terms that were common for spam or something to that effect.  I'll prolly try it again.  As soon as I removed the OpenDns addresses, I no longer got the error.

---

### Post by rkd on 2008-03-08
There have been many kinds of malicious software (viruses, etc.) that changes the DNS settings on a computer to misdirect your web browsing to look-alike sites in the hope of capturing sensitive information that you enter, such as account numbers, PIN numbers, etc.  

I haven't seen any reports that OpenDNS was connected in any way with that kind of activity.  Something might have happened recently that I've not seen yet, but I think that is unlikely.

You say that you are getting messages from Google that say you were searching for terms that were common for spam.  As far as I know, Google can't tell what DNS you are using on your computer, so it really puzzles me that you associate getting those messages from Google with using OpenDNS.  Was there something in the messages that pointed you to the use of OpenDNS as the problem?  Did you just decide on your own to drop OpenDNS as an experiment to see whether that affected the messages from Google?  Something else that led you to OpenDNS?

I've been using OpenDNS for a long time and I don't remember ever seeing a message from Google that would make me think OpenDNS is a problem.  Once in a while, when I click the link to go to a new page of results, Google will give me a page that says something about my pattern of usage makes it look like it isn't a human using Google, but an automated program.  I've never figured out what triggers that, but it happened to me before I started using OpenDNS, and hasn't been any more or less frequent since I switched.

I suppose the warning message might be text that your ISP is adding to the Google result page. (Since everything passes through your ISP's computers, they can modify the pages in any way they please.  They usually pass the pages through unchanged, but I have seen reports that some ISPs add things to some of the pages they handle.)  It could be that your ISP has noticed that DNS requests from your computer are not going through your ISP's DNS and they are just assuming that some virus has changed your DNS to a malicious location.  If your ISP is making such a check, it probably isn't making any attempt to distinguish between legitimate alternate DNS and malicious ones.  They probably figure that if you know enough to intentionally change your DNS, you'd be able to recognize that their warning didn't apply to you.

I imagine that since you stopped using OpenDNS, your web browsing has slowed down again, like it was before you tried OpenDNS.  If it actually is performing well now, then maybe your ISP has fixed whatever problem its DNS was having and you can just go on using it.

But if your web browsing is slow again, and you would like to use OpenDNS to speed things up, I think it is perfectly safe to resume using OpenDNS.  If you do, and you start getting those warning messages from Google again, either write down the message, or use your mouse to copy the message, or capture an image of the screen using the PrtSc key, then post exactly what it is saying and maybe we can pick up a clue that you aren't noticing.

---

