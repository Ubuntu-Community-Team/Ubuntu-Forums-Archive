---
title: "Help with Linksys wrt54G router needed!"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-10-22
Normally I try to research all threads and the internet before I post but I am desparate and am waiting for a potential employer to call me...and I ave no phone right now!

My wireless router is not working correctly.  I reset it, all proper lights are lit, my cable modem is working fine (I am connected directly to that right now).  My cables are working fine-I switched them all out and they work.  So can someone help me (a) get my router working again, and (b) help me get my phone adapter working again!  (I have Vonage).

I am running Feisty Fawn, the router is a Linksys WRT54G V2, the phone adapter is model # PAP2

---

### Post by bean77 on 2007-10-22
Forgot to mention that everything was fine until a power outage yesterday.  Usually there is no problem in getting everything back but this is new!

I read another thread and it asked for the output of

sudo lshw -C network

Here it is:

```
 *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 66:33:c0:58:66:a3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full ip=75.68.31.221 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: ioport:cc00-ccff iomemory:fdffe000-fdffe0ff irq:18
```

The output for sudo iwlist scan:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

The output for iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.
```

(Would make sense since I'm not plugged in to the router right now)

---

### Post by slackpipe on 2007-10-22
Sounds like your Ubuntu setup is fine, and your cable modem is working properly.  My guess would be that your router may have been taken out during the power surge.  I've seen this happen a lot with the WRT54G.  Plug the router into the computer and see if the DHCP assigns an ip address.  If it does, ping your gateway to see if you have a working connection between the router and the computer.

If that works, you should be able to log into the router and look at the configuration.  If your modem does DHCP (most do nowadays) make sure the router is set to get an ip off of it.  Also make sure that the router and the modem aren't both trying to use the same set of ips (192.168.1.1 for the modem and the router) you may have to switch the router over to 192.168.2.1.  Easiest way to do this would be check your gateway while your plugged into the modem, then again when your plugged into the router.  if they are the same, set the router to 192.168.2.1. (first page of the setup, about middle-ways down)  This should resolve any ip conflicts.

hope that helps

---

### Post by bean77 on 2007-10-22
> **slackpipe said:**
> Plug the router into the computer and see if the DHCP assigns an ip address.  If it does, ping your gateway to see if you have a working connection between the router and the computer.

If that works, you should be able to log into the router and look at the configuration.  If your modem does DHCP (most do nowadays) make sure the router is set to get an ip off of it.  Also make sure that the router and the modem aren't both trying to use the same set of ips (192.168.1.1 for the modem and the router) you may have to switch the router over to 192.168.2.1.  Easiest way to do this would be check your gateway while your plugged into the modem, then again when your plugged into the router.  if they are the same, set the router to 192.168.2.1. (first page of the setup, about middle-ways down)  This should resolve any ip conflicts.

hope that helps

Is this under System>Administration>Network and then highlight the "Wired Connection" and the look at the properties?  There is no IP address there.

---

### Post by bean77 on 2007-10-22
I hate to be that annoying person but can anyone chat with me over IM to walk me through this?

yahoo:  lydiaach
AIM:  lydiaacheson

---

### Post by bean77 on 2007-10-22
Als, I cannot get to 192.168.1.1

---

### Post by jon419 on 2007-10-22
The Vonage/Wireless router from Linksys usually uses the IP address 192.168.15.1 as the default IP address for the web based console for the wireless router.

I would recommend doing a hard reset of your router in order to get it set back to the defaults and reset it internally.  There should be a small hole on the back of the router with the word 'reset' written under it.  Get a paper clip (unfold it a bit) and stick one of the ends in that whole.  You will be pushing down on a little button.  Hold the paper clip in there for 15 - 30 seconds.  The lights on the front of the router should flash and it will then reset itself to factory defaults.

Then you can connect to it from your computer.  Navigate to 192.168.15.1 via wired network or wireless.  The wireless name will be linksys.  You will be asked for a username and password.  These will both be the word 'admin'.

Anyway, that is how I had to recover from a power outage once.  Once the router was reset I was able to go back in and reconfigure it.

---

### Post by gvoima on 2007-10-22
There's a known problem with the hard reseting process amongst the WRT54G.

I have version 3 and it didn't reset until I pushed the little button down about 1min, then while still pressing it, took the power cord off. And keeped pressing it about 1min after this, then left it without power for about 2-3min. Then when I plugged back in, it was reseted.

Annoying, but it wouldn't reset the way manufacturer suggests.

---

### Post by hyper_ch on 2007-10-22
First of all I'd replace the firmware of the router with  DD-WRT (I think it supports the 54G)...

---

### Post by magli on 2007-10-22
> **gvoima said:**
> I have version 3 and it didn't reset until I pushed the little button down about 1min, then while still pressing it, took the power cord off. And keeped pressing it about 1min after this, then left it without power for about 2-3min. Then when I plugged back in, it was reseted.
:confused: Hehe.Classic

---

### Post by cfaulkner on 2007-10-22
Proper hard reset of the router would be to:

As the router is powered, hold the reset button.  The power light will start to blilnk.  When this happens, count to 10.  Then unplug the power cord.  release reset button.

Plug power cord back in.  Your router should be factory reset.

Also, if you have v3 wrt54g, might I suggest using the Tomato Firmware v1.10.

[http://www.polarcloud.com/f/Tomato_1_10.7z](http://www.polarcloud.com/f/Tomato_1_10.7z)

it's a lean version but is chocked full of handy stuff.

---

### Post by bean77 on 2007-10-22
Unfortunately none of this is working.

I am working with a very kind fellow Ubuntu user who is tirelessly chatting with me on IM.  I hope we can figure it out!

---

### Post by magli on 2007-10-22
The problem seems to be that the router is failing to acquire an IP address from the modem.

Here is our AIM conversation in full:
[http://www.suedbalkon.eu/help.html](http://www.suedbalkon.eu/help.html)
Maybe someone more knowledgeable than I can have a look through this and give some feedback. I am stumped.

Also note my mistake in giving the alias "ubuntu guy needing help" - have already apologized.

---

### Post by magli on 2007-10-22
I just upgraded to the tomato firmware suggested by cfaulkner - and am very impressed. It is an enormous improvement over the original firmware, and I prefer it to the dd-wrt.

---

### Post by cfaulkner on 2007-10-22
The WRT54G default router address should be **192.168.1.1**  you stated in the AIM log **192.168.100.1**

the 100.1 address is usually the cable modem's IP Address.


Basically, what's going on here is the cable company is not releasing the IP address.  At the start of the convo, he did an ifconfig and it reported a 75.x.x.x address meaning his computer is connected directly to the cable modem.  

He probably bought the wrt54g from someone that was on a DSL connection and the hard config those routers.  It's getting an IP address but it is trying to do it through PPPoE and if your cable, that won't work.  So, what he needs to do in this order to reset that router is.

1> As the WRT54G is powered up, with a pin, hold the reset button down until the power light starts blinking.
2> As the reset button is held down and the power light is blinking, unplug the power cord.
3> release reset button
4> Plug the ethernet cord coming from the computer and plug it into ports 1-4
5> plug the ethernet cord coming from the cable modem and plug it into the "Internet" port of the WRT54G
6> Plug the power cord back in
7> After all the lights on the WRT54G settle down (i.e. power light is solid)  open up a web browser and point to [http://192.168.1.1](http://192.168.1.1)
8> should be a auth screen: username is always "admin" without quotes and all lower case,  pasword is sometimes different but could be "admin" "1234" or "password"
 *_8a> if the passwords do not work, go back to Step 1 and hold the reset button down for 30 sec AFTER the power light starts blinking and then continue with step 2_*
9> Once you get into the Firmware screen, you are looking for "Mac Address Clone" on the first settings page, click that
10> Clone your PC's Mac address and save.  Reboot router and Reboot cable modem
11> Power up Cable modem first
12> power up WRT54G

You should be good to go, do not stray away from one of these lines or get ahead.  Dont' do anything extra.. Follow it to the Letter.

---

### Post by cfaulkner on 2007-10-22
> **magli said:**
> I just upgraded to the tomato firmware suggested by cfaulkner - and am very impressed. It is an enormous improvement over the original firmware, and I prefer it to the dd-wrt.

It's not the greatest firmware, but I like it because it's simple...  :)

---

### Post by bean77 on 2007-10-22
I've got everything up to step 7.  when I get there:

Unable to connect  

      
      
      

      
        
        

          

Firefox can't establish a connection to the server at 192.168.1.1.



        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

---

