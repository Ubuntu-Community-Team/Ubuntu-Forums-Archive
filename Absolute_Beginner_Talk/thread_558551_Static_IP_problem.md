---
title: "Static IP problem"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-09-21
i connect to my wireless Lan successfully and surfing the internet is ok, but i want to set a static IP rather than a dynamic one, where when i set it as appear in the attached screenshot the internet become not accessible, so how to set the static IP? if there is away using interface dialog  rather than command line it will better for me.

---

### Post by finer recliner on 2007-09-21
it looks like you're trying to set it to 192.168.1.25

by default, most routers start handing out IPs starting at 192.168.1.100, so you need to change the last number to something over 100

you can confirm this by checking the admin settings of the router
(go to 192.168.1.1 in an internet browser)

---

### Post by akkad on 2007-09-21
i changed to something above 100 but still the same :( , do u think the settings i did in the screenshot are enough ??

---

### Post by Dr Small on 2007-09-21
All of my static IP addresses are under 100. Example... 192.168.0.56, 192.168.0.16, and they all work.

Once you set up your configuration for the IP addresses that you want, run this command in the terminal:
```
sudo /etc/init.d/networking restart
```

And then try and see if your IP address has changed to the static one you tried changing it to. :)

Dr Small

---

### Post by akkad on 2007-09-21
i performed the command given, but when i ping my ip it give a 100% successful packets but when i ping the gateway itself or other machines on the WLAN 0% packets success, so i cant see other machines on the network?????

---

### Post by akkad on 2007-09-23
so no one gonna answer me :(   ???

---

### Post by akkad on 2007-09-24
am connecting to a WLAN, with the dynamic IP everything will be fine but with Static IP i can only ping myself where i cant access the internet or ping other computers on the network, idea plz??

note : after setting my IP i use this command from the forum to refresh my network settings :
sudo /etc/init.d/networking restart

---

### Post by ravenwere on 2007-09-24
Without any more detail it would indicate you are using a duplicate IP address to another PC on the network.

---

### Post by akkad on 2007-09-24
actually i would like to show u how did i set the static IP which appears in the attached screen shot, is what appear in the image all what i need to set a static IP or should i perform extra settings ??

---

### Post by ravenwere on 2007-09-27
The easiest way to check your configuration is to connect to the network dynamically then check the configuration settings using the command```
ifconfig
```at the command line.

---

### Post by HermanAB on 2007-09-27
Well, you need a number of things.  The IP address is only one of them:
IP address
Netmask
Gateway address
DNS addresses (at least 2)

Cheers,

Herman

---

### Post by akkad on 2007-10-06
hi, i have another two posts for this problem but it is still unsolved :( :
[http://ubuntuforums.org/showthread.php?t=558551](http://ubuntuforums.org/showthread.php?t=558551)
[http://ubuntuforums.org/showthread.php?t=556365](http://ubuntuforums.org/showthread.php?t=556365)

i cant set my static IP where here is what i did tell now with some outputs:
- with auto configuration everything is ok but with static it is not.
- this command is not useful : sudo /etc/init.d/networking restart
- note the driver for my wireless card(Intel Pro wireless) appears in the restricted drivers. 
- here is the output for /etc/network/interfaces :
[COLOR="DarkOrange"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid menhaaath
wireless-key s:steveashakkadrakan

auto eth1[/COLOR]


- here is the output for ifconfig:[COLOR="DarkOrange"]
eth0      Link encap:Ethernet  HWaddr 00:15:C5:C0:C9:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:D7:AF:A3  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:1051 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2566112 (2.4 MiB)  TX bytes:443126 (432.7 KiB)
          Interrupt:16 Base address:0xc000 Memory:efcff000-efcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28600 (27.9 KiB)  TX bytes:28600 (27.9 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.81.1  Bcast:192.168.81.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.82.1  Bcast:192.168.82.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/COLOR]


i hope these info help solving this problem .

---

### Post by lintoon on 2007-10-06
If you can't ping your router I would guess you are either on a different subnet, have an IP conflict  or are not associated with the wireless router.

It doesn't matter what IP addresses your router is handing out (eg over .100) as long as whatever you set doesn't conflict with another system or the router (.1) or the broadcast address (.255)

If you change back to DHCP does it work still?  If so can you post the result of "ifconfig" while you are connected using DHCP.

---

### Post by louieb on 2007-10-06
Check your routers **Lan IP configuration **My router a Netgear  allows me to assign an IP based on the network cards MAC address (HWaddr in ifconfig).  Works for both wired and wireless cards.  Thats how I assign IP address on my home network. Simple and easy. Now  your PC can use DHCP and they will get the same IP every time they connect.

---

### Post by julian67 on 2007-10-07
Perhaps you didn't set a DNS server. If you use static IP address you have to set this manually. You can do it through the gui nm-applet>manual configuration>dns and then run the command sudo /etc/init.d/networking restart

Looking at your posts I guess you should use 192.168.1.1 for your DNS

---

### Post by akkad on 2007-10-07
ok ok i noticed something but i still need ur help, my encryption i set for my WLAN is WPA Personal where when i set static ip it allows me choose WEP(hex) or WEP (ascii) , there is no option for WPA in the drop down as appears in the attached screen shot

---

### Post by akkad on 2007-10-07
ok ok i noticed something but i still need ur help, my encryption i set for my WLAN is WPA Personal where when i set static ip it allows me choose WEP(hex) or WEP (ascii) , there is no option for WPA in the drop down as appears in the attached screen shot

---

### Post by julian67 on 2007-10-07
I can see you are trying to address this problem in 2 (or maybe more) threads simultaneously. Not such a great idea. 

I'm reluctant to get into an issue while there are other threads in progress on the same subject...I don't want to have to read 2 or 3 threads to know what is happening, so I'll just tell you what I know and what I would do and leave it at that:

I have 2 Intel wi fi adapters, an ipw2200 and an ipw3945 and I know that they both work with static IP, WPA and are fully compatible with network-manager. But I don't know which version of Ubuntu you use. I'm going to assume you use Feisty 7.04 with network-manager and that your router is configured to work with WPA and that you know the key. 

Start over:

Remove any old or erroneous keys from the gnome keyring

edit the file /etc/network/interfaces so it looks like this

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

Now run the command ```
sudo /etc/init.d networking restart
```

Click on the network manager applet and it should show you your network. Click to connect and it should offer automatically ask you for your WPA password. Enter it and wait, you should then be prompted for the password for your keyring, enter that and wait. The applet should then advise you that you are connected. This of course is all with DHCP. But now you know that WPA works you can click on network-manager applet again and select manual configuration and edit your wireless adapter's IP address and DNS address. 

again ```
sudo /etc/init.d networking restart
```

and you should be connected with static IP, working DNS and WPA encyption.

---

### Post by bodhi.zazen on 2007-10-07
Please do not start multiple threads on the same topic. It leads to confusion and duplication of effort in trying to help.

/bodhi merges threads. I will look over your situation once I have finished ...

---

### Post by akkad on 2007-10-07
ok, regarding the WPA i believe its working with my wirless Ethernet, when i choose my WLAN it prompts me to enter the network password where by default it select WPA Personal from the drop down so by default it detected my network encryption, but when i want to set statically as u have seen in the previous  screen shot i have no option to choose WPA , only WEP is there , by the way i went step by step with u wanted me to do but still unable to set.

plz take a good look to the previous screen shot, and tell me if am editing the static ip correctly, what i did that i unchecked the enable roaming mode, then choose my network name, then the password type where two options only available WEP(hex) and WEP(ascii), then network password, then the ip settings, is there anything else????

---

### Post by akkad on 2007-10-07
ok, regarding the WPA i believe its working with my wirless Ethernet, when i choose my WLAN it prompts me to enter the network password where by default it select WPA Personal from the drop down so by default it detected my network encryption, but when i want to set statically as u have seen in the previous  screen shot i have no option to choose WPA , only WEP is there , by the way i went step by step with u wanted me to do but still unable to set.

plz take a good look to the previous screen shot, and tell me if am editing the static ip correctly, what i did that i unchecked the enable roaming mode, then choose my network name, then the password type where two options only available WEP(hex) and WEP(ascii), then network password, then the ip settings, is there anything else????

---

### Post by akkad on 2007-10-07
sorry for the duplicating threads, its a matter of finding a solution.

---

### Post by akkad on 2007-10-07
julian67 would u like to vnc my laptop so u can take a look at my problem??

---

### Post by julian67 on 2007-10-07
> **akkad said:**
> julian67 would u like to vnc my laptop so u can take a look at my problem??

No but you can post it to me :lolflag: If i were you i wouldn't ask complete strangers to remotely take control of your PC. It is tempting though.....

Here's a suggestion, I think someone else made it already in one of your previous threads. You don't need to configure a static address on your PC. You can do it on the router. You assign a static address in the router config to the MAC address of your wireless adapter. You can be 100% sure this will work because you know now that WPA is recognised by network manager. The big advantage for you will be that your laptop will effectively have static Ip at home and still be set up to easily connect  to other networks if you use it in different places.

---

### Post by Whiffle on 2007-10-07
> **julian67 said:**
> 
Here's a suggestion, I think someone else made it already in one of your previous threads. You don't need to configure a static address on your PC. You can do it on the router. You assign a static address in the router config to the MAC address of your wireless adapter. You can be 100% sure this will work because you know now that WPA is recognised by network manager. The big advantage for you will be that your laptop will effectively have static Ip at home and still be set up to easily connect  to other networks if you use it in different places.

Thats what I would and do do.

What kind of router do you have?  Some don't like static IP addresses in a certain range.  I know my linksys back home has to have them above 150 for the last number if i remember right.

---

### Post by akkad on 2007-10-08
my gateway is also linksys, i will try the MAC address solution may be it will work.

---

### Post by vexorian on 2007-10-21
I tried the gutsy live CD and I couldn-t set up an static IP , unlike the past (Feisty / Breezy /  Dapper)

Just doing:

IP: 192.168.1.2
Mask: 255.255.255.0
Gate: 192.168.1.1

Used to work fine (also on windows) right now I cannot get an internet connection by just doing that.

I have to use console and :

```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gateway 192.168.1.1
```


And edit "/etc/resolv.conf" to add my two fav DNS servers.

PS: The reason I know about these commands is that in an old version Slax live.cd had an issue with it ignoring static IP configuration...

---

### Post by julian67 on 2007-10-22
> **vexorian said:**
> I tried the gutsy live CD and I couldn-t set up an static IP , unlike the past (Feisty / Breezy /  Dapper)

Just doing:

IP: 192.168.1.2
Mask: 255.255.255.0
Gate: 192.168.1.1

Used to work fine (also on windows) right now I cannot get an internet connection by just doing that.

I have to use console and :

```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gateway 192.168.1.1
```


And edit "/etc/resolv.conf" to add my two fav DNS servers.

PS: The reason I know about these commands is that in an old version Slax live.cd had an issue with it ignoring static IP configuration...

/etc/resolv.conf is probably being overwritten by network-manager. It's easier for you to check this than for me as I don't have a Gutsy install. While you have network-manager installed then you really *must* use it for setting your ip and dns addresses*. If you have network-manager installed and try to use traditional methods to configure and bring up/down your interfaces then your network interfaces are unlikely to work and network-manager will also cease working! 

* an exception is that if you use DHCP but also want to use specific DNS then you can edit the file /etc/dhcp3/dhclient.conf  and change the line that starts with "prepend" so that it reads ```
prepend domain-name-servers yourdns1, yourdns2;
``` and then you can have your IP address, subnet, route and gateway assigned by DHCP but *your* choice of DNS always used.

My experience is that beginning with Feisty Ubuntu's network-manager + applet can handle everything extremely well with supported cards, can assign static IP to one card and DHCP to another, allow multiple interfaces to run simultaneously and so on,  and there is no longer any need to edit config files by hand for normal use. If you want/need to edit them then you should uninstall network-manager.

---

