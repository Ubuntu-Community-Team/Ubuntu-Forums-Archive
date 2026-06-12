---
title: "madwifi install problem - FATAL: module wlan in use"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by stuck on 2007-05-22
Hello, and sorry to bother you busy people again, but my own research (google) has failed me again :(

I am having to use MS for this, and its a bit of a pain booting and rebooting from this to Ubuntu.

So here goes.

Ive got the latest version of Ubuntu, I downloaded and reinstalled 2 days ago(dont know why, the last version was ok, I guess I'm a sucker for punishment)

Ive tried to follow the madwifi instructions but I cant get any further than this:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")


ifconfig ath0 down
ifconfig wifi0 down
ifconfig eth0 down -------(did it anyway, not sure if i needed to)

here's from memory.

madwifi-unload.bash ----i was in the scripts folder

then i get:

FATAL: Module wlan_scan_sta is in use.
FATAL: Module wlan is in use.

Just as well I live in the UK, or the laptop would have been shot by now.

Any help greatly appriciated. Pointers in the right direction, or hand holding.

Thank you.

PS

Also tried the various different HOW TO documents here. And can't connect to the net at all with Ubuntu.

---

### Post by RomeReactor on 2007-05-22
HI. I don't know anything about madwifi, but it seems to me that the problem is that your wireless interface (wlan) is still running when you run the script. Open a terminal (Applications-->Accessories-->Terminal) and enter the follwing:
```
iwconfig
```
It should tell you which one is your wireless interface (probably wlan0, wlan1, etc.); Then you should do:
```
ifconfig **CARD** down
```
where **CARD** is the interface you find with the iwconfig command, before running the **madwifi-unload.bash** script.

---

### Post by stuck on 2007-05-22
No help. But thanks for the reply.

iwconfig gives me this: (allmost)

eth0      no wireless extensions.

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So when I did the initial "ifconfig ath0 down" that should have been it.

Also before trying to install madwifi I clicked the little monitor/network icon  and told it to disable connection. (sorry if terminology isnt right, but i have to keep switching between MS and Ubuntu)

Also I had a little circuit board pop up saying something about restricted modules.

ATHEROS .......HAL....(I un-checked enabled) STATUS--in use.

Dont know if this is any more help.

---

### Post by h0ax on 2007-05-22
you need to have that module enabled, even though it says restricted.
This is your driver for your wifi card, which sounds to be proprietary.

---

### Post by stuck on 2007-05-22
> Re: madwifi install problem - FATAL: module wlan in use 

--------------------------------------------------------------------------------

you need to have that module enabled, even though it says restricted.
This is your driver for your wifi card, which sounds to be proprietary.

?????????????????


Brand spanking new install of Ubuntu. I have installed nothing else. My problem now seems even worse. Before I could see wireless networks but not connect to them. Now I've just finished formating and re-installing Ubuntu and I cant even see networks anymore. And there are at least 2 more above and beyond mine. And still cant install madwifi.

:(  :(

---

### Post by stuck on 2007-05-22
Problem resolved.

I dont know how or why, but I gave up on the madwif, and can now connect to the net using Ubuntu.

---

### Post by tughlas on 2008-03-17
Hello gang,
I am facing the same problem now as stuck..
Let me give you a run through so far:

1- I have a Kubuntu Gutsy Gibbons 7.10 installed on my Thinkpad T61 (so an atheros card)
2- I could initially detect wireless networks and connect to them with ease.
3-  When I initially installed KUbuntu, on checking the default interface settings for ath0, I saw that it was neither automatic nor manual was checked. 

Today, I don't know what nut came off my brain, I checked automatic and it has stopped showing me wireless networks ! 
But I can see 

[I]ath0      Link encap:Ethernet  HWaddr 00:1C:26:62:06:A3
          inet addr:192.12.89.182  Bcast:192.12.89.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe62:6a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20440 (19.9 KB)  TX bytes:48424 (47.2 KB)[/I]

.....

[I]wifi0     Link encap:UNSPEC  HWaddr 00-1C-26-62-06-A3-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:426703 errors:0 dropped:0 overruns:0 frame:147720
          TX packets:975 errors:82 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:42182794 (40.2 MB)  TX bytes:83451 (81.4 KB)
          Interrupt:17

[/I]
when I do an ifconfig (when I do an 
*$ifconfig ath0 up*)

I am trying to reinstall the madwifi drivers (I don't know if it is the right thing to do) and I am getting the same error 
[I]
FATAL: Module wlan_scan_sta is in use.
FATAL: Module wlan is in use.[/I]

when I run :
[I]./madwifi-unload.bash
[/I]inside the scripts directory ....

Could someone please throw some light ? 
I am extremely sorry if this question has been posted under a wrong thread. Its just that I saw this error when I was googling it and realized its the same one as I am getting,

-chakravarthy

---

### Post by Ohioan on 2008-03-18
tughlas, I too am getting this error.  Can anyone help us?
this is what happens when I try and follow the how-to.  

> odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ sudo ifconfig ath0 down
odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ sudo ifconfig wifi0 down
odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ ./madwifi-unload.bash
FATAL: Module wlan_scan_sta is in use.
FATAL: Module wlan is in use.
odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ 


---

### Post by Ohioan on 2008-03-19
Anyone?

---

### Post by Ohioan on 2008-03-20
bump

---

### Post by Ohioan on 2008-03-21
i'm starting to think no one has a clue.

---

### Post by Junglizer on 2008-03-21
> **Ohioan said:**
> tughlas, I too am getting this error.  Can anyone help us?
this is what happens when I try and follow the how-to.

odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ sudo ifconfig ath0 down
odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ sudo ifconfig wifi0 down
odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ ./madwifi-unload.bash
FATAL: Module wlan_scan_sta is in use.
FATAL: Module wlan is in use.
odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"" Nickname:""
Mode:Managed Channel:0 Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power:16 dBm Sensitivity=1/1
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=0/70 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

odellz@odellz-laptopcomputerthatsitsonadesk:~/madwifi/madwifi-0.9.4/scripts$


What seems to be the issue? The prior code listing of iwconfig looks correct. You would want to use iwconfig to associate with an AP: ```
iwconfig ath0 essid "home"
``` then retrieve and ip address ```
dhclient ath0
```.

---

### Post by Junglizer on 2008-03-21
Or rather more specifically why are you trying to  unload that module? Seeing as how it can't unload it but iwconfig still seems to be working. Do you really need to unload it?

---

### Post by Ohioan on 2008-03-21
I'm following the instructions to install updated madwifi drivers to see if it helps with the crappy signal i get.

i need to unload all of the module so i can remove the old drivers an install the new.

at any rate, i' just trying to folllow the instructions

---

### Post by Neo0351 on 2008-03-21
I use madwifi on my laptop and its always just worked for me.  It's included in the restricted modules.

---

### Post by openflame06 on 2008-04-23
Hey guys - i think a bit of confusion happened on this post. The original post was about not being able to install mad wifi because of receiving this:

FATAL: Module wlan_wep is in use.
FATAL: Module wlan_scan_sta is in use.
FATAL: Module wlan is in use

The reason you cant get passed this step is because the above modules are still loaded - and you cant rmmod any of them.

If you type sudo rmmod wlan however, it will tell you each module relying on wlan.

 sudo rmmod ath_pci
 sudo rmmod ath_rate_sample
 sudo rmmod wlan_scan_sta
 sudo rmmod wlan_wep
 sudo rmmod wlan

The above commands allowed me to run the script, im running 7.10 gutsy with an atheros card.

After you run the second step of mad wifi you should finally be able to get through to the end of the guide 

Hope this helps :-)

---

