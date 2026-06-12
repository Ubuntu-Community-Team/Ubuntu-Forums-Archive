---
title: "How to get Wifi running on my nc4010"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by arjungandhi on 2007-06-11
Hey guys,

I am completely new to linux, and have very little experience with it. I decided to try running Ubuntu off Wubi and while I can get internet to work of the ethernet cable, I cannot seem to get my wifi to connect to my router. In the manual configuration page, it seems to recognize my router  since i can see the router name, but when I type my passcode in and click 'ok' nothing happens. I believe the wifi card in my laptop is Atheros AR5212, but I am not 100% sure. Any help would be greatly appreciated. 

Thanks in advance,

Arjun.

---

### Post by ugm6hr on 2007-06-11
> **arjungandhi said:**
>  I believe the wifi card in my laptop is Atheros AR5212, but I am not 100% sure. Any help would be greatly appreciated. 


You can check for certain by entering in Terminal:
```
lspci
```
Look for the Netowork Controller entry

Other info thats helpful:
```
ifconfig
```
```
iwconfig
```

What security do you use on your network?  Does wifi connect to your router from the same laptop in  another OS (e.g. Windows)?

---

### Post by arjungandhi on 2007-06-11
I typed the codes you gave me in the terminal. The first one 'lspci' confirmed that is is the wifi card I thought it was. Now the other two is where I am not sure. I dont know quite what to make of this since i am new to codes, but I shall pase what i found on here.

arjun@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:12:79:3D:1E:B3  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:79ff:fe3d:1eb3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:11:85:88:78:B8  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:85ff:fe88:78b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27295752 (26.0 MiB)  TX bytes:1536106 (1.4 MiB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32567 (31.8 KiB)  TX bytes:32567 (31.8 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-12-79-3D-1E-B3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10300 errors:0 dropped:0 overruns:0 frame:26209
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:679440 (663.5 KiB)  TX bytes:27875 (27.2 KiB)
          Interrupt:5 


[U]
'iwconfig'[/U]

arjun@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"gladiator"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:10185  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And as to the other questions, first it does connect seamlessly to windows. Also it is WEP with a password on it. I hope that helps.

---

### Post by lazyart on 2007-06-11
You're getting an IP address on ath0, so that is good.  Try this:```
sudo ifdown ath0
sudo ifup ath0
``` and see if that helps.

---

### Post by ugm6hr on 2007-06-11
When you click on your SSID (presumably on the icon in the top-right corner), and it asks for your password - what type of encryption options does it offer?

I found that you have to use a HEX key for WEP, since ASCII and passkey options misbehave.

PS: Other thing to try is (briefly) turn off WEP (i.e. leave network open) to see if you connect - that way you know that you're heading in the right direction.

---

### Post by arjungandhi on 2007-06-11
> **lazyart said:**
> You're getting an IP address on ath0, so that is good.  Try this:```
sudo ifdown ath0
sudo ifup ath0
``` and see if that helps.

Well I tried both and this is what I get 

arjun@ubuntu:~$ sudo ifdown ath0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
arjun@ubuntu:~$ sudo ifup ath0
arjun@ubuntu:~$ 

When I first typed in sudo ifdown ath0 it asked me for a password. Not knowing which password to type in i typed in my Ubuntu login password. That may have been wrong but I do not know what to do. After the first try, they all give that message.

---

### Post by arjungandhi on 2007-06-11
> **ugm6hr said:**
> When you click on your SSID (presumably on the icon in the top-right corner), and it asks for your password - what type of encryption options does it offer?

I found that you have to use a HEX key for WEP, since ASCII and passkey options misbehave.

PS: Other thing to try is (briefly) turn off WEP (i.e. leave network open) to see if you connect - that way you know that you're heading in the right direction.

It was on Hex, not on ASCII. As well I turned of WEP ( enable roaming) and it does not do anything.

---

### Post by ugm6hr on 2007-06-11
> **arjungandhi said:**
> It was on Hex, not on ASCII. As well I turned of WEP ( enable roaming) and it does not do anything.

Need to clarify something here - do you have enable roaming ticked in the "manual setting"?  I would suggest you try with it ticked - then right-click on the network manager icon top-right - tick enable networking and wireless, then left click same icon - it should bring up a list of SSIDs - then click on yours.

To turn off WEP - you need to edit the settings on your router (not on your computer settings).

---

### Post by arjungandhi on 2007-06-11
> **ugm6hr said:**
> Need to clarify something here - do you have enable roaming ticked in the "manual setting"?  I would suggest you try with it ticked - then right-click on the network manager icon top-right - tick enable networking and wireless, then left click same icon - it should bring up a list of SSIDs - then click on yours.

To turn off WEP - you need to edit the settings on your router (not on your computer settings).

Ok, In manual configuration for wireless and wired I have roaming enabled, and I turned of WEP. When I right click on the manager icon on the top right, it gives me some options, with wireless networks. I tried to connect my inputting all the information, and now, it shows that it is at 30% connetion speed with 'gladiator' (my router name' even when the router is a foot above me. But what really baffles me is that it still does not connect me to the internet.

---

### Post by ugm6hr on 2007-06-11
Hmmm... I'm a bit confused now too.

Try iwconfig again - to see whether you are genuinely connected - it should give you a bit rate and authentication MAC code (in ath0):
```
Mode:Managed  Frequency:2.437 GHz  Access Point: *XX:XX:XX:XX:XX:XX *  
Bit Rate:11 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
```

As for the 30% status - don't worry about it - my Atheros5005G never manages more than 30% either, but works everywhere in my house.

---

### Post by arjungandhi on 2007-06-11
> **ugm6hr said:**
> Hmmm... I'm a bit confused now too.

Try iwconfig again - to see whether you are genuinely connected - it should give you a bit rate and authentication MAC code (in ath0):
```
Mode:Managed  Frequency:2.437 GHz  Access Point: *XX:XX:XX:XX:XX:XX *  
Bit Rate:11 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
```

As for the 30% status - don't worry about it - my Atheros5005G never manages more than 30% either, but works everywhere in my house.

arjun@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"gladiator"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:10185  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Hmm, there does not seem to be a bit rate, so I dont think it is genuinely connected

---

### Post by ugm6hr on 2007-06-11
I'm afraid I'm out of ideas.  It might be worth searching this forum for your Atheros chipset to see if anyone has found a solution.  A quick search on madwifi (who provide the atheros linux drivers) suggests that the HP card misbehaves):
[http://madwifi.org/wiki/Compatibility/HP](http://madwifi.org/wiki/Compatibility/HP)

Try the button the front - can't do any more damage...  If it doesn't work - I'm stumped.  Perhaps ndiswrapper is an option?

EDIT: ndiswrapper does seem a possibility:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/) (search for W400)

---

### Post by arjungandhi on 2007-06-11
> **ugm6hr said:**
> I'm afraid I'm out of ideas.  It might be worth searching this forum for your Atheros chipset to see if anyone has found a solution.  A quick search on madwifi (who provide the atheros linux drivers) suggests that the HP card misbehaves):
[http://madwifi.org/wiki/Compatibility/HP](http://madwifi.org/wiki/Compatibility/HP)


Try the button the front - can't do any more damage...  If it doesn't work - I'm stumped.  Perhaps ndiswrapper is an option?

EDIT: ndiswrapper does seem a possibility:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/) (search for W400)

Alright, thats not a problem; I guess that this is my goal for the summer. I just want to thank you anyway for constantly replying to my posts. Peace out.

---

### Post by Bablefish on 2007-06-11
I am sorta in the same pickle as you. My laptop is a HP NC6000 and I just could not find wifi drivers that would work. After checking MADWIFI myself I found that there drivers should and I repeat should work. In fact the easiest way to download them is through the Synaptic Package Manager. But besure it's set to install your download as for the set up and I an unsure it actually works is go in to the Terminal and type in Can you send the output of these commands:

dmesg | grep ath0

and when in range of a wreless router enter in range of wireless router  enter this



iwlist ath0 scanning

I was told this would get it up and running

---

### Post by arjungandhi on 2007-06-12
Ok, I am not sure how this happened, but yesterday following what some of you guys told me got my card up and running without having to use any other drivers. I guess it needed a night to figure itself out or something hell I dont know. All I do know is that this morning when I turned on Ubuntu
and checked the settings it recognized my network, asked me to type in the key, and a password and away I went. This post is done through wireless. Thanks to all that gave comments, I really appreciate it.

---

### Post by ugm6hr on 2007-06-12
Glad it came good.  Be nice to know what the actual solution was for future reference though....

Maybe the reboot?  Or maybe unplugging the wired ethernet cable when booting?

Ultimately, what's important is that you're now free to roam :)

---

### Post by paddyponchero on 2007-07-10
The nc4010 has a 'wireless button' which actually disables the cards radio - don't touch it. After a cold boot the card should be operational.

---

### Post by ionFreeman on 2008-05-30
Hi! I've also got an nc4010. The wireless worked in Windows. I installed Dapper Drake (the CD came with my ZaReason laptop) and the wireless worked grade. I upgraded to Gutsy Gibbon, then to Hardy Heron.

Wireless no longer works. I can click on my ESSID, and I get the first green dot and "attempting to join the wireless network 'MDZ'", but I never get the second green dot or the bar chart. My network's open (like [Bruce Schneier's!)]("http://www.schneier.com/blog/archives/2008/01/my_open_wireles_1.html")

iwlist eth1 scanning

shows 17 cells, but running it doesn't fix my wireless access. In an unrelated (?) problem, I seem to have lost my ability to be root, so that's my first concern. But, I would like to get the wireless working.

OK, as a tip? Don't create a user called 'admin' using users-admin. So, I'm back to needing my wireless fixed. 

I've got NDISwrapper from Synaptic, and I'm trying to download the driver files. I'll let you know how it goes.

---

### Post by ionFreeman on 2008-05-31
So, I can now access [my neighbor's wireless]("http://xkcd.com/341/"). I tried several things, but I think getting Windows Driver Restore DVDs out of their protective packaging frightened my laptop into something like compliance -- I had only found the drivers I needed online at a site festooned with pornography, which seemed a little dicey. I created a "Manual Configuration" to my ESSID using network-admin, then switched back to roaming mode.

This let me access somebody else's wireless network (not the one I created a configuration for; I had been trying that network all along.) I'd still like to access my own, but I'm content for now.

Back to getting Celtx up and running....

---

### Post by ionFreeman on 2008-06-10
Whatever updates I got today -- probably the new kernel -- allowed the wireless card to work. So, it's back to work on the SyncMaster 204B.

---

