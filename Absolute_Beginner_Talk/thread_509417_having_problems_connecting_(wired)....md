---
title: "having problems connecting (wired)..."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by ubunoobie on 2007-07-25
I need help. I've installed 7.04 and now when I plugged in my ethernet cable into my PC (from my router) it connects and disconnects repeatedly. I don't know where to go from here... I have looked at different troubleshooting documents but none describe my problem. Thanks in advance from a noobie! :)

---

### Post by ReverendJ1 on 2007-07-25
Is it possible there is something wrong with the cable? Try a different cable, or if you can, try pushing on the cable connected to the computer and router. i.e. pushing and holding both cables in to their ports, to see if it helps. I have had a couple laptops that the ethernet port on them just kind of got worn, so it would connect, disconnect all the time. Just a thought, try the easy things first. :-) Also, try holding the cables in different positions to see if it helps. i.e. Hold the cable up or down.

---

### Post by st33med on 2007-07-25
Of course, their could be a chance your ISP's messing around with you. They can turn off the connection for like, say, only 3 minutes of inactivity. Haven't had that happen to me, but I know people who have.

---

### Post by ubunoobie on 2007-07-25
> **ReverendJ1 said:**
> Is it possible there is something wrong with the cable? Try a different cable, or if you can, try pushing on the cable connected to the computer and router. i.e. pushing and holding both cables in to their ports, to see if it helps. I have had a couple laptops that the ethernet port on them just kind of got worn, so it would connect, disconnect all the time. Just a thought, try the easy things first. :-) Also, try holding the cables in different positions to see if it helps. i.e. Hold the cable up or down.

Thank you. I looked at the back on my computer and I noticed when I touch the cable the orange connection light comes on for a 5-6 seconds then turns back off. Could this mean my port is bad? I even held it and tried not to let it move, but the light still turned off in a few seconds.

---

### Post by w4ett on 2007-07-25
> **ubunoobie said:**
> I need help. I've installed 7.04 and now when I plugged in my ethernet cable into my PC (from my router) it connects and disconnects repeatedly. I don't know where to go from here... I have looked at different troubleshooting documents but none describe my problem. Thanks in advance from a noobie! :)


Check cables and connections, then check router channel (plug cable into a different port).  This is most likely a problem with the physical connections....also check your connection from the router to modem, and modem to cable  (or phone line in the case of ADSL)

If this fails, Then, turn off router and computer and modem,  start modem...wait til it syncs, start router and wait til sync, then restart computer.

---

### Post by ReverendJ1 on 2007-07-25
Could be. Do you have spare cable you could use? Or a spare network card you could try? I guess most people probably wouldn't, but I have a stockpile of about 20 laying around. :-)

---

### Post by ubunoobie on 2007-07-25
Ok, now I'm noticing that the connection light in the back of my computer (where the port is) is turning on and off by itself. It stays on for about 5 seconds, then it comes back off.

---

### Post by w4ett on 2007-07-25
> **ubunoobie said:**
> Ok, now I'm noticing that the connection light in the back of my computer (where the port is) is turning on and off by itself. It stays on for about 5 seconds, then it comes back off.

The light is an indication of connectivity with your router....doesn't always mean your eth port on computer is bad.

---

### Post by ubunoobie on 2007-07-25
> **w4ett said:**
> Check cables and connections, then check router channel (plug cable into a different port).  This is most likely a problem with the physical connections....also check your connection from the router to modem, and modem to cable  (or phone line in the case of ADSL)

If this fails, Then, turn off router and computer and modem,  start modem...wait til it syncs, start router and wait til sync, then restart computer.

Ok, I tried this... still nothing. Now it's not connecting at all. At the top right (by the clock), where the network settings are, I only have one option now... which is "Manual configuration..."

So I go there and right now I have the wired connection configured to dhcp, but still nothing. Any thoughts?

---

### Post by ubunoobie on 2007-07-25
> **ReverendJ1 said:**
> Could be. Do you have spare cable you could use? Or a spare network card you could try? I guess most people probably wouldn't, but I have a stockpile of about 20 laying around. :-)
I just bought the cable, so it's most likely not the cable... however my network card I'm not sure of. But I don't have any reason to think it's bad... I've never messed with it, it's not very old at all, and it never gave me problems when I used Windows. Any thoughts? Thanks!

---

### Post by FleetAdmiral74 on 2007-07-25
I am surprised no one has asked the brand and model of your card, and your NIC as well. Maybe you are using some unsupported set?

Never give up, trust your instincts!

---

### Post by ubunoobie on 2007-07-25
> **FleetAdmiral74 said:**
> I am surprised no one has asked the brand and model of your card, and your NIC as well. Maybe you are using some unsupported set?

Never give up, trust your instincts!
Well, where could I find this info? Here's some info about my PC. It is a Dell Dimension 4600C desktop, Pentium 4 2.8 GHz, 1GB RAM, 80 GB hard drive, um... what else? It has integrated 10/100 ethernet.

---

### Post by ubunoobie on 2007-07-25
I have never changed or messed with the network card... it's the one that came with the PC originally.

---

### Post by w4ett on 2007-07-25
To view your connected hardware (pci connected, which your Ethernet chipset is) in the terminal type
```

lspci
```

to view your network properties click on System.Administration>Network, select eth0....it should be set for "Automatic configuration DHCP"

---

### Post by ubunoobie on 2007-07-25
> **w4ett said:**
> To view your connected hardware (pci connected, which your Ethernet chipset is) in the terminal type
```

lspci
```

to view your network properties click on System.Administration>Network, select eth0....it should be set for "Automatic configuration DHCP"

Thank you. I type in the command, but I'm not sure what I'm looking for...

Also, I do have the "Network Settings" set to auto config dhcp.

---

### Post by ubunoobie on 2007-07-25
I see a few things that might be of interest:
Communication controller: Conexant Unknown device 2702 (rev 01)
Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by ubunoobie on 2007-07-25
Something else:

PCI bridge: Intel Corporation 82801 PCI Bridge (revc2)

---

### Post by ubunoobie on 2007-07-25
I really don't think this is a physical connection problem...

anyone out there have any other ideas?

---

### Post by w4ett on 2007-07-25
The [COLOR="Red"]Broadcom Corporation BCM4401 100Base-T (rev 01)[/COLOR] should work 'out of the box'.

Just for testing purposes boot your live cd if you have one and check your eth connectivity.  Possibly one of your drivers is damaged in your installation...the live cd is a easy way to check.

---

### Post by ubunoobie on 2007-07-25
> **w4ett said:**
> The [COLOR="Red"]Broadcom Corporation BCM4401 100Base-T (rev 01)[/COLOR] should work 'out of the box'.

Just for testing purposes boot your live cd if you have one and check your eth connectivity.  Possibly one of your drivers is damaged in your installation...the live cd is a easy way to check.
What do you mean? Boot from LiveCD and try to see if I can go to a website? Well, I'll try this right now.

---

### Post by w4ett on 2007-07-25
Sounds like a plan!

---

### Post by ubunoobie on 2007-07-25
w4ett, thanks for spending time here to help me! I rebooted with the livecd in but it went through to the OS on my harddrive... on the desktop it shows that the cd is in the drive however. it says "Ubuntu 7.04 i386"

I open the cd and a window opens up with a bunch of different files on the cd. I think I'm a little confused about what you sked me to do. Could you repeat that again? Thanks!

---

### Post by w4ett on 2007-07-25
Set the boot priortiy in your Bios.  f1, f2, <esc> are some of the  toggles used to get to your Bios Setup.....should be a heading called, Boot priority, or somthing similar , make your 1st boot device to your cd/dvd optical drive.

Sometime F11 will give you a boot priority list too, just not sure what is used on your unit.

---

### Post by ubunoobie on 2007-07-25
Ok, here's what's happening now. It's doing the same thing from the LiveCD as it was doing from the installed OS on the hard drive. Connecting and disconnecting. But for the few moments that it "connects," it's not really connected because I can't access any web pages. Right at this moment there is a green dot and a grey dot with something circling it... when I rest my mouse on it it says "Requesting a network address from the wired network..."

---

### Post by ubunoobie on 2007-07-25
> **w4ett said:**
> Set the boot priortiy in your Bios.  f1, f2, <esc> are some of the  toggles used to get to your Bios Setup.....should be a heading called, Boot priority, or somthing similar , make your 1st boot device to your cd/dvd optical drive.

Sometime F11 will give you a boot priority list too, just not sure what is used on your unit.

Yea, I figured that's what it was :-) stupid me...

Got it going, but still no different.

---

### Post by ubunoobie on 2007-07-25
Btw, I've tried the command "sudo pppoeconf" but I'm not sure if that's what I need to do... I have ADSL, and I'm just trying to connect, that's all! Errr.. it's kinda frustrating. But I'm not givin up! This will work.

---

### Post by w4ett on 2007-07-25
See if you can enter your router setup...type in the address bar  192.168.1.1 .....assuming you have another machine, and your attempt from your 'Buntu Box does not work, do it from  it, and make sure your lan settings are correct....and have enabled the address assignment correctly...usually this is automatic in the router, but you never know!

---

### Post by ubunoobie on 2007-07-25
> **w4ett said:**
> See if you can enter your router setup...type in the address bar  192.168.1.1 .....assuming you have another machine, and your attempt from your 'Buntu Box does not work, do it from  it, and make sure your lan settings are correct....and have enabled the address assignment correctly...usually this is automatic in the router, but you never know!
This is what my router says:> 
 DHCP Server

Your DSL Gateway will automatically assign an IP Address to each computer in your network. 

---

### Post by ubunoobie on 2007-07-25
I have to go away from my computer now for a few hours, but I will be back!

If anyone else thinks of anything while I'm gone I would really appreciate it! I'm already impressed by the speed of the help available in these forums.

---

### Post by w4ett on 2007-07-25
I'm a bit at a loss at this point..  :confused:  Router says ok,   What does your Network Tools show?

Here's mine, for reference

---

### Post by ubunoobie on 2007-07-25
> **w4ett said:**
> I'm a bit at a loss at this point..  :confused:  Router says ok,   What does your Network Tools show?

Here's mine, for reference

I'm away from my computer right now, but, my network tools, you mean my Network Settings? My network settings doesn't quite look like that, but anyway, if you mean my router configuration page, it doesn't quite look like that either. I'm quite lost as well :(

---

### Post by ubunoobie on 2007-07-25
I'm back and I still need help. I am determined to find out what the cause of my problem is, but I'm not sure where to go from here.

Thanks in advance!

---

### Post by ReverendJ1 on 2007-07-25
I'm just going to throw some ideas out here. Are you dual-booting? If so, try booting into Windows and make sure it will still connect. 
Also, try turning off your computer, then unplug your router and modem, wait about 30 seconds and then plug everything back in and turn everything on.
What lights are on on your modem?

---

### Post by ubunoobie on 2007-07-25
> **ReverendJ1 said:**
> I'm just going to throw some ideas out here. Are you dual-booting? If so, try booting into Windows and make sure it will still connect. 
Also, try turning off your computer, then unplug your router and modem, wait about 30 seconds and then plug everything back in and turn everything on.
What lights are on on your modem?
Thank you. I no longer have windows on that machine... but it worked previously on windows. I've also already tried to turn everything off and reboot/reset.

My modem/router has a power light which is on, a DSL light which is on, a Internet light which is on, and a wireless light which is on, but for the 1 2 3 4 lights (the ports), the #3 port (which I've plugged the cable for my desktop into) is flashing... and I know it should be steady if it's connecting, because I have tested that already with my other computer (the one I'm writing from now).

I just don't get why it "connects" and disconnects over and over... I'm not even touching it! I haven't seen anyone else on the forums with this problem.

---

### Post by gimpguy2000 on 2007-07-25
Just a thought, didn't see it so if posted forgive me but did you bypass the router and try hooking directly to the modem?

Paul

Edit: may require a modem reset\ pc restart

---

### Post by ubunoobie on 2007-07-25
> **gimpguy2000 said:**
> Just a thought, didn't see it so if posted forgive me but did you bypass the router and try hooking directly to the modem?

Paul

Hi, I'm not sure that it is possible for me to do that... I have a Actiontec Wireless DSL Gateway. I think it's the modem and router together. So anyway, I go from the PC straight to the back of the router... see, I'm getting connection just fine with the router, because I'm using it right now to write in this thread from my laptop. So I know I've got connection and the internet works just fine. I just don't know what the deal is with my desktop (the one with 7.04).

---

### Post by ubunoobie on 2007-07-25
I typed the command "ifconfig" and here is my result:

> ubuntu@ubuntu-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:86:83:85  
          inet6 addr: fe80::20b:dbff:fe86:8385/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:3 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13 (13.0 b)  TX bytes:21237 (20.7 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24828 (24.2 KiB)  TX bytes:24828 (24.2 KiB)

ubuntu@ubuntu-desktop:~$ 
WTH? I don't know how a smiley got in there... ignore that. Thanks!

---

### Post by gimpguy2000 on 2007-07-25
I think I see what you mean, i'm trying to visualize here...so let me ask, did your wireless come with a setup disk?  If you just setup Ubuntu, I would try to re-run the setup completely with everything connected, that's what I did and it worked better. First time, I had some issues w\o router connected during setup. Just a thought and at least Ubuntu isn't like Windows or Fedora, it sets up very quickly. If nothing else works, I would try that. 

 Paul


The smiley is due to the  : ) close together in command lines.

---

### Post by ubunoobie on 2007-07-25
I don't know if this will help or not, but here are some screenshots... you can kinda see how it is just connecting and disconnecting.

---

### Post by ubunoobie on 2007-07-25
.

---

### Post by ubunoobie on 2007-07-25
..

---

### Post by gimpguy2000 on 2007-07-25
You may want to look here..

[http://ubuntuforums.org/showthread.php?t=54886](http://ubuntuforums.org/showthread.php?t=54886)

 In my opinion though, it's the nic configuration.  I honestly think you may have to add a different nic, many onboard or add on OEMS don't support linux. Just my opinion though and sorry I couldn't be much more help.
   Paul

---

### Post by ubunoobie on 2007-07-25
> **gimpguy2000 said:**
> You may want to look here..

[http://ubuntuforums.org/showthread.php?t=54886](http://ubuntuforums.org/showthread.php?t=54886)

 In my opinion though, it's the nic configuration.  I honestly think you may have to add a different nic, many onboard or add on OEMS don't support linux. Just my opinion though and sorry I couldn't be much more help.
   Paul
No problem, thank you! I'll look there now.

---

### Post by ReverendJ1 on 2007-07-25
I am thinking the issue just has something to do with DHCP. Why it won't work I don't know, it seems that all your settings are right. I just have one more idea. Try setting your IP address manually.  Open 'Network Settings' then click the properties of the wired connection. Change the dropdown to  'Static IP Address'. Set your IP address to one that is within the scope of your DHCP on your router. They may also call this a DHCP pool. You will have to log into your router to get this. If you can't find the setting, you could probably use x.x.x.10 where x.x.x are the first 3 sets of numbers of your router. Set your 'Subnet Mask' to 255.255.255.0 and the 'Gateway Address' to the IP of your router. Close network settings and test. This may require a restart, but it shouldn't.

---

### Post by ubunoobie on 2007-07-25
> **ReverendJ1 said:**
> I am thinking the issue just has something to do with DHCP. Why it won't work I don't know, it seems that all your settings are right. I just have one more idea. Try setting your IP address manually.  Open 'Network Settings' then click the properties of the wired connection. Change the dropdown to  'Static IP Address'. Set your IP address to one that is within the scope of your DHCP on your router. They may also call this a DHCP pool. You will have to log into your router to get this. If you can't find the setting, you could probably use x.x.x.10 where x.x.x are the first 3 sets of numbers of your router. Set your 'Subnet Mask' to 255.255.255.0 and the 'Gateway Address' to the IP of your router. Close network settings and test. This may require a restart, but it shouldn't.
I tried this and now it's not connecting/disconnecting anymore, but still no internet!

When I click on the two computers at the top right, now I only have one option that says "Manual configuration..."

:confused:

---

### Post by ReverendJ1 on 2007-07-25
Right. Did you try and restart? Also, try pinging the router, ```
ping 192.168.0.1
``` If you get a response then we may be on the right track.

---

### Post by t4thfavor on 2007-07-25
I have had prolblems with intel branded, and linksys branded nic's under linux (kernel 2.4/2.6) where the light on both the router, and the nic would blink very slowly, and at the same rate. The only thing I could do to fix it was either swap out the nic for a good 3com, or swap the hub/switch until I got one that worked. 

This problem has caused me all kinds of headaches, and to this day I have never figured it out.

My only advice is that you ebay yourself a 3c905-tx or a 3c905-txm they should go for insanely cheap, and are still among the best 10/100 nic's ever created.

You should be able to find one on ebay for under $10USD(Shipping included), or go to the local pc swap meet and buy them for $1.00 each:)

---

### Post by ubunoobie on 2007-07-25
> **ReverendJ1 said:**
> Right. Did you try and restart? Also, try pinging the router, ```
ping 192.168.0.1
``` If you get a response then we may be on the right track.
Thanks again. This is what is coming out (and it keeps coming out!):
```
From 169.254.7.249 icmp_seq=1 Destination Host Unreachable
```

---

### Post by ubunoobie on 2007-07-25
> **t4thfavor said:**
> I have had prolblems with intel branded, and linksys branded nic's under linux (kernel 2.4/2.6) where the light on both the router, and the nic would blink very slowly, and at the same rate. The only thing I could do to fix it was either swap out the nic for a good 3com, or swap the hub/switch until I got one that worked. 

This problem has caused me all kinds of headaches, and to this day I have never figured it out.

My only advice is that you ebay yourself a 3c905-tx or a 3c905-txm they should go for insanely cheap, and are still among the best 10/100 nic's ever created.

You should be able to find one on ebay for under $10USD(Shipping included), or go to the local pc swap meet and buy them for $1.00 each:)

I'm not sure exactly what brand my NIC is, but could you tell me how to find out? Do you think that may be the problem?

---

### Post by t4thfavor on 2007-07-25
From what you said its a broadcom based nic, but still the onboard ones are the bottom of the barrel as far as quality is concerned. I still recommend swapping out your nic, the only thing it will cost you is a few bucks, and if really can't hurt you.

EDIT: Your last post indicates the nic is working, it just does not have an address. Try "sudo dhclient eth0" from the command line, and see if you get anything from that.

---

### Post by ubunoobie on 2007-07-25
> **t4thfavor said:**
> From what you said its a broadcom based nic, but still the onboard ones are the bottom of the barrel as far as quality is concerned. I still recommend swapping out your nic, the only thing it will cost you is a few bucks, and if really can't hurt you.

Ok, thanks. I'll see what I can do about this...

---

### Post by t4thfavor on 2007-07-25
Yeah I hate when the only acceptable solution is "Buy something else" but I reckon that it will happen for a few years until linux becomes "Main stream" :)

Wireless cards are also included in this, but wired has been around for alot longer.

Did you try the command I gave you, I have a feeling that it will work.

---

### Post by ubunoobie on 2007-07-25
> **t4thfavor said:**
> Yeah I hate when the only acceptable solution is "Buy something else" but I reckon that it will happen for a few years until linux becomes "Main stream" :)

Wireless cards are also included in this, but wired has been around for alot longer.

Did you try the command I gave you, I have a feeling that it will work.

Ok, I just tried that command (didnt see it sorry), and I got this:
```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:db:86:83:85
Sending on   LPF/eth0/00:0b:db:86:83:85
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
What do you think?

---

### Post by gimpguy2000 on 2007-07-25
[http://www.linuxforums.org/forum/mandriva-linux-help/28473-no-dhcpoffers-received.html](http://www.linuxforums.org/forum/mandriva-linux-help/28473-no-dhcpoffers-received.html)
 and 

[http://forums.fedoraforum.org/archive/index.php/t-418.html](http://forums.fedoraforum.org/archive/index.php/t-418.html)

You may want a looksee there as well. Sounds very similar..

Paul

---

### Post by ReverendJ1 on 2007-07-25
If **nothing** else works, I could probably  grab one of my used NICs (only 10/100 if it matters) like Th4thefavor said, make sure it works out of the box for me and sell it to you through Paypal. $10 sounds reasonable with shipping, assuming you live in US. I wouldn't care about payment if it didn't fix it, just ask that you ship it back at your cost. I dunno, I'm not trying to make money here, just help someone out. I have a whole bunch, because I take them out of computers when we recycle them at work. Other than that I am going to back out of this thread as I have exhausted my troubleshooting abilities. PM me if you have exhausted all other options. Or buy one off ebay, my feelings won't be hurt. :-)

---

### Post by ubunoobie on 2007-07-25
> **ReverendJ1 said:**
> If **nothing** else works, I could probably  grab one of my used NICs (only 10/100 if it matters) like Th4thefavor said, make sure it works out of the box for me and sell it to you through Paypal. $10 sounds reasonable with shipping, assuming you live in US. I wouldn't care about payment if it didn't fix it, just ask that you ship it back at your cost. I dunno, I'm not trying to make money here, just help someone out. I have a whole bunch, because I take them out of computers when we recycle them at work. Other than that I am going to back out of this thread as I have exhausted my troubleshooting abilities. PM me if you have exhausted all other options. Or buy one off ebay, my feelings won't be hurt. :-)

Hey, thanks a lot! I will PM you if I decide that I need to go that route.

---

### Post by ubunoobie on 2007-07-26
going to sleep now... thanks to all for your generous help!

I will continue this later...

---

### Post by ubunoobie on 2007-07-26
I won't be around much today, but if anyone could perhaps kindly take a look at my situation (in the previous posts) and offer any help, it would be greatly appreciated!

bump

---

### Post by w4ett on 2007-07-26
Ubunoobie:  I'd try to use a replacement NIC in your machine as was recommended earlier.   After all the testing that has been done, looks like the only thing left, is to eliminate the integrated chipset, and try another one.

We've eliminated the possibility of Cables, Router, DHCP issues, and OS problems, the only other  thing that has NOT been done is to try a different Ethernet Card.  

$5 get you one shipped:

[http://www.gearxs.com/gearxs/product_info.php?products_id=3388](http://www.gearxs.com/gearxs/product_info.php?products_id=3388)

Pretty cheap fix IMHO

---

### Post by ubunoobie on 2007-07-26
> **w4ett said:**
> Ubunoobie:  I'd try to use a replacement NIC in your machine as was recommended earlier.   After all the testing that has been done, looks like the only thing left, is to eliminate the integrated chipset, and try another one.

We've eliminated the possibility of Cables, Router, DHCP issues, and OS problems, the only other  thing that has NOT been done is to try a different Ethernet Card.  

$5 get you one shipped:

[http://www.gearxs.com/gearxs/product_info.php?products_id=3388](http://www.gearxs.com/gearxs/product_info.php?products_id=3388)

Pretty cheap fix IMHO

Ok, thank you! Yea, I'm really starting to consider that... since it's not much anyway.

---

### Post by gimpguy2000 on 2007-07-26
While most think of a nic card as simply transferring information or sort of a funnel that information just pours into, "not saying you do" but there are 7 layers of communication and in order for that nic to work right, the communication layers must be able to, well, communicate. However some nics, mostly onboard or OEM versions don't support linux. As stated by others and myself , the best bet is another card. 

 If anyone can touch base on this article..

[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

 I'm not sure of the workings here but if this would be an option and someone could help you, this may work.

 Paul

---

### Post by ubunoobie on 2007-07-27
> **w4ett said:**
> Ubunoobie:  I'd try to use a replacement NIC in your machine as was recommended earlier.   After all the testing that has been done, looks like the only thing left, is to eliminate the integrated chipset, and try another one.

We've eliminated the possibility of Cables, Router, DHCP issues, and OS problems, the only other  thing that has NOT been done is to try a different Ethernet Card.  

$5 get you one shipped:

[http://www.gearxs.com/gearxs/product_info.php?products_id=3388](http://www.gearxs.com/gearxs/product_info.php?products_id=3388)

Pretty cheap fix IMHO

w4ett,

This NIC that you have linked to is guaranteed to be compatible with linux? I just want to make sure, so that I don't spend more money than necessary. Thanks again!

---

### Post by w4ett on 2007-07-27
If it doesn't work out of the box,  (and I think that  this chipset is supported out of the box) additional drivers are available. See this vendors website:

[http://www.etech4sale.com/Encore_ENL832-TX-RENT_10_100Mbps/ENL832-TX-RENT/partinfo-id-152258.html](http://www.etech4sale.com/Encore_ENL832-TX-RENT_10_100Mbps/ENL832-TX-RENT/partinfo-id-152258.html)

P.S:  Why not call the vendor...It's toll free??

---

### Post by ubunoobie on 2007-07-27
> **w4ett said:**
> If it doesn't work out of the box,  (and I think that  this chipset is supported out of the box) additional drivers are available. See this vendors website:

[http://www.etech4sale.com/Encore_ENL832-TX-RENT_10_100Mbps/ENL832-TX-RENT/partinfo-id-152258.html](http://www.etech4sale.com/Encore_ENL832-TX-RENT_10_100Mbps/ENL832-TX-RENT/partinfo-id-152258.html)

P.S:  Why not call the vendor...It's toll free??

Ok, thank you! I know this is not a "hardware troubleshooting" Dell forum, but this is getting a little more complicated than I might know how. Is this a piece of hardware that fits in any computer? Say a few years-old Dell Dimension 4600C...

---

### Post by w4ett on 2007-07-27
> **ubunoobie said:**
> Ok, thank you! I know this is not a "hardware troubleshooting" Dell forum, but this is getting a little more complicated than I might know how. Is this a piece of hardware that fits in any computer? Say a few years-old Dell Dimension 4600C...

The card will be perfect for your desktop....(you insert it into a PCI slot on the motherboard.)  See:

[http://www.ridge.com.au/pciinstall.html](http://www.ridge.com.au/pciinstall.html)

for a description of the physical installation proceedures.

---

### Post by ubunoobie on 2007-07-27
> **w4ett said:**
> The card will be perfect for your desktop....(you insert it into a PCI slot on the motherboard.)  See:

[http://www.ridge.com.au/pciinstall.html](http://www.ridge.com.au/pciinstall.html)

for a description of the physical installation proceedures.

Ok, thanks again!

---

### Post by w4ett on 2007-07-27
No problem...If you have further questions, we'll be here.   Good Luck

---

### Post by ubunoobie on 2007-07-29
I haven't sent off for a new NIC yet, but I decided to reinstall XP and run Windows and see if I could get online at all... well it turns out that I'm having the same problem with XP! I installed the necessary drivers and I can see that I have a LAN connection set up, but it keeps connecting and disconnecting repeatedly. Keep in mind that everything used to work prior to the Ubuntu installation. I'm starting to wonder if this is a NIC problem afterall... anyway I read that the Broadcom 440x is supposed to work "out of the box." Any thoughts on this? Has anyone had this happen to them, or heard of this happening? Thanks!

---

### Post by w4ett on 2007-07-29
> **ubunoobie said:**
> I haven't sent off for a new NIC yet, but I decided to reinstall XP and run Windows and see if I could get online at all... well it turns out that I'm having the same problem with XP! I installed the necessary drivers and I can see that I have a LAN connection set up, but it keeps connecting and disconnecting repeatedly. Keep in mind that everything used to work prior to the Ubuntu installation. I'm starting to wonder if this is a NIC problem afterall... anyway I read that the Broadcom 440x is supposed to work "out of the box." Any thoughts on this? Has anyone had this happen to them, or heard of this happening? Thanks!
 
I've been thinking of another possibility.  Boot into your BIOS  (Setup) and check that you have not inadvertantly disabled your onboard ethernet.  If this is not the case, then this would lead me to believe that it (the onboard controller) is bad

---

### Post by ubunoobie on 2007-07-30
> **w4ett said:**
> I've been thinking of another possibility.  Boot into your BIOS  (Setup) and check that you have not inadvertantly disabled your onboard ethernet.  If this is not the case, then this would lead me to believe that it (the onboard controller) is bad

"It is bad..." You mean the card?

p.s. I think I am going to go ahead and get another NIC anyway, since they're pretty cheap. I'm having trouble getting ahold of the gearxs.com people, so I found another card on a different website, would this work as well?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156107](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156107)

It says Linux drivers, so I figure it'll work.

---

### Post by ubunoobie on 2007-07-30
I looked in the BIOS and it's enabled... everything looks fine. I'm going to go ahead and get a new card, but what's got me a little worried is that this problem is occuring now in Windows as well, and I'm wondering if I'll get the new card and still not be able to connect. :neutral:

---

### Post by w4ett on 2007-07-30
It's based on a Realtek chipset, so it is supported out of the box.

But here's another one with the same chipset for under $5 with free shipping too:

[http://www.gearxs.com/gearxs/product_info.php?products_id=1234](http://www.gearxs.com/gearxs/product_info.php?products_id=1234)

I've ordered from this company with no problems.

---

### Post by armandh on 2007-07-30
I use a d-link 10/100 [cheap and works]
the other problem
I have one mo-bo that has a bad pci socket.
it is where the modem was at one time and the socket has a non working IRQ
I suspect static distcharge of the big variety in  the past.
drove me nuts [could be the same for an on board item.]
now with any non working plug in item I always try a different socket

---

### Post by ubunoobie on 2007-07-30
> **w4ett said:**
> It's based on a Realtek chipset, so it is supported out of the box.

But here's another one with the same chipset for under $5 with free shipping too:

[http://www.gearxs.com/gearxs/product_info.php?products_id=1234](http://www.gearxs.com/gearxs/product_info.php?products_id=1234)

I've ordered from this company with no problems.

Oh ok, got it now! The previous one you recommended to me mustve been sold out, as it didnt have the "Add to cart" button, but this one does, thanks. Yea, I rather pay less :)

---

### Post by ubunoobie on 2007-07-30
> **armandh said:**
> I use a d-link 10/100 [cheap and works]
the other problem
I have one mo-bo that has a bad pci socket.
it is where the modem was at one time and the socket has a non working IRQ
I suspect static distcharge of the big variety in  the past.
drove me nuts [could be the same for an on board item.]
now with any non working plug in item I always try a different socket

Thanks. Didn't think about that... when I opened the case, I did notice that the card was slightly out of the socket on one end, so I pushed it back down and tried again, but still nothing. Hopefully, I didnt mess anything up myself (static), anyway I'll try the other slot also and hope for the best.

---

