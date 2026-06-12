---
title: "Very confused about wireless &gt;.&lt;&quot;"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by lemoniceblock on 2006-12-27
Hi all,

I only installed ubuntu (Edgy) last night onto an old laptop that was previously running on Windows XP home and it already had a working wireless card (Linksys WPC54G version 4).  I have very limited experience with command line OS's and am not very computer literate either. ;)  I read a number of tutorials/guides and am now very confused although I *think* that I did manage to use ndiswrapper to install the right drivers for the card since when I type in sudo ndiswrapper -l, it says:
wlipnds   driver installed, hardware present

But now I am very confused as to what to do next.
I am following the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") up to step 8.3 (sudo ndiswrapper -m), though to be honest, I didn't really understand all of it ^^;;

Any help would be greatly appreciated, thank you!

---

### Post by bgoody on 2006-12-27
Hi.  Just keep going with that tutorial, you're very close.

sudo depmod -a
  sudo modprobe ndiswrapper

Then ifconfig 
and iwconfig

I suspect that they will show that you're up and running.  After that you need to switch off your wired connection before you can use the wireless one with the Networking tool (System | Administration | Networking)

Brian

---

### Post by lemoniceblock on 2006-12-27
Hi,
Thanks for the reply, I'm typing this on a different computer with wired connection; I never actually thought of connecting my laptop with a wire ^^;; but I ran ifconfig and iwconfig but I'm not really sure what they mean.

ifconfig:
> 
eth0  Link encap:Ethernet HWaddr 00:02:3F:B0:E5:8F
        UP BROADCAST MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0  fram:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0b)   TX bytes:0 (0.0b)
        Interrupt:10   Base address:0x4800

lo     Link encap:Local Loopback
        inet addr:127.0.0.1   Mask:255.0.0.0
        inet6 addr: ::1/128  Scope:Host
        UP LOOPBACK RUNNING   MTU:16436   Metric:1
        RX packets:332 errors:0 dropped:0 overruns:0  fram:0
        TX packets:332 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0   txquelen:0
        RX bytes:24816 (24.2 KiB)    TX bytes:24816 (24.2 KiB)


iwconfig:
> 
lo      no wireless extensions.

sit0    no wireless extensions.

eth0   no wireless extensions.

wlan0 IEEE 802.11g   ESSID:off/any
         Mode:Managed   Frequency:2.347 GHz  Access Point: Not-Associated
         Bit Rate: 1Mb/s
         RTS thr:2347 B   Fragment thr:2346 B
         Power Management:off
         Link Quality:0  Signal level:0   Noise level:0
         Rx invalid nwid:0    Rx invalid crypt:0   Rx invalid frag:0
         Tx excessive retries:0    Invalid misc:0    Missed beacon:0


Are my iwconfig and ifconfig normal?
I was guessing that perhaps it was because my wireless network at home has encryption so that might be the problem, but normally, wireless computers at home can access other non-encrypted networks in my neighbourhood so I thought I would see if my laptop could look for and connect to those unencrypted networks so I ran iwlist scan and got this:
> 
lo      Interface doesn't support scanning.

sit0    Interface doesn't support scanning.

eth0   Interface doessn't support scanning.

wlan0 No scan results


So I think that my main problem is not with the drivers of the network card?

Thanks!

---

### Post by lemoniceblock on 2006-12-29
Update on my still :confused:  situation:
I plugged in my ethernet cable and installed wifi-radar.  After I installed it, iwlist scan showed available access points but for a while I still couldn't connect to any of them, even the unencrypted ones (couldn't get IP address).

Bluecat: my encrypted home network
Linksys: neighbourhood's unencrypted network

I manually configured Bluecat and my laptop was able to connect to that (or so it says :P ) but the problem was that it could not connect to the Internet...though it said it was connected to Bluecat with 100% strength.
I ran** iwconfig**:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Bluecat"  Nickname:"Bluecat"
          Mode:Auto  Frequency:2.457 GHz  Access Point: 00:0F:66:8A:A4:47   
          Bit Rate=6 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-34 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and **ifconfig -a**:
```

eth0      Link encap:Ethernet  HWaddr 00:02:3F:B0:E5:8F  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:243012 (237.3 KiB)  TX bytes:243012 (237.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:90:32:5E  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:fe90:325e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:14274 (13.9 KiB)
          Interrupt:10 Memory:16000000-16000800 

```

and **netstat -nr** (I only read this from some other threads, not sure why I did it though =P ):
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

The funniest thing was that I played around the wifi-radar configurations of Bluecat, specifically the IP because I really wasn't sure if I had configured it correctly in the first place or not, but every time I changed it, it still said I was connected to Bluecat with 100% strength.
Also I noticed that the MAC address of my router listed on my router page is different from the one listed on iwconfig...could that be a clue as to what's wrong?

Thanks!

---

### Post by Apple 101 on 2006-12-29
You could just install 'gnome-network' package, and its dependencies.  Then you can configure your wireless configuration from its user interface.

---

### Post by lemoniceblock on 2006-12-31
Hi, thanks for the reply, I'm still trying to work out which file to d/l, but meanwhile I'd like to confirm if I have installed the drivers for my card correctly.

I checked the list of drivers supported by ndiswrapper and since the list only mentioned wlipnds.inf that was the only one I installed although I've read in tutorials/guides/docs about instalilng one .inf and one .sys (I've tried other drivers on my CD but they all showed up as inccorect driver) and ndiswrapper -l does say 'wlipnds    driver installed, hardware present'.

I can also scan for APs and though the green bar on the navigation panel suggests that I am connected, Firefox can't actually connect to any pages.

When I run dhclient wlan0, it says 'No DHCPOFFERS received.  No working leases in persistent database - sleeping.'

Also, I don't remember encountering this problem before, but just now when I typed 'sudo ifdown wlan0' it says 'interface wlan0 not configured'.

At first I thought that the problem might be with my router, and now I'm not sure if I should go back to tinkering with ndiswrapper?

Thanks everyone, have a great new year!

---

### Post by bgoody on 2006-12-31
HI.  I believe ndiswrapper is correct and it seems the wlan is powered up but you need to disconnect from eth0 or whatever before you can connect to the wlan.

In other words your system (including Firefox) is still looking at the wired connection. OR at least that's how it looks to me...

Brian

---

### Post by lemoniceblock on 2007-01-03
Hello!
Thank you, I reinstalled Ubuntu and my wireless worked for a while...I tried disconnecting from eth0 completely too, but it still wouldn't work.  I suppose that shows that the card and drivers actually work, so I'm beginning to suspect 2 problems:

1. My router is still refusing to assign an IP (I'm still getting that no dchchp offers received message)

2. I can't configure the card well, even though iwconfig and ifconfig don't seem to show any errors (it lists the correct access point).  The network manager suggests that the networks are configured but I can't seem to configure wlan0 via command line.  When I type iwconfig wlan0 essid <essid> it gives a variety of error messages even when I'm using sudo.    Also, when I ran dmesg it said something about not finding any IPV6 Routers, and about the wlan0 device not ready?

Sorry I'm a bit vague; I'm not with my laptop at the moment :P
Thanks for the continued support!

---

### Post by Kulgan on 2007-01-03
Might also be that eth0 tries to start at boot, and steals the settings?
-K

---

### Post by jck3j on 2007-01-03
I was having huge problems with wireless with my ipw3945 card. However, i started to use the NetworkManager applet and it works so well. I'm not sure, but if you get really desperate, try the applet... it really worked for me.

---

### Post by Kulgan on 2007-01-03
> **jck3j said:**
> I was having huge problems with wireless with my ipw3945 card. However, i started to use the NetworkManager applet and it works so well. I'm not sure, but if you get really desperate, try the applet... it really worked for me.

The network manager applet - nm-applet - works well when it works, but for me it doesn't identify my network card half the time. I'm with good old command line :D

But it's definitely worth a try...

---

### Post by skinny on 2007-01-03
I'd suggest making sure you can definitely get your wireless working with unencrypted networks again (yours neighbours in this case?) before trying to get it working with encrypted networks. I had a similar problem, albeit with a different device: hardware was detected, driver (that I had installed through ndiswrapper) was detected, lights on the device went flashing etc, but I still couldn't connect to our encrypted network. I presumed that my problem lay in the configuration of wpa supplicant, but after trying a different set of drivers (older, but for the same device) everything worked perfectly.

Perhaps not the answer you're looking for but hang in there.

When you say it worked for a while, how long is a while? And how well did it work? And when did you notice it had stopped working?

---

### Post by lemoniceblock on 2007-01-06
Hi all!  Sorry for the late reply.  I decieded I had to leave my laptop alone before I lost my temper and wrecked it or something =P

@Kulgan:  I've disabled eth0 but it's still not working.  However, when I ran dmesg and grepped wlan0 and later eth0, I noticed that at some point, both had the same message" no IPv6 routers present (though eth0 while it was up as a wired connection worked perfectly so I don't think IPv6 routers is a problem here, might be wrong though =P ).  Otherwise, there's nothing in common.

@jck3j:  I've tried that applet before I reinstalled Ubuntu and it didn't work for me, but I will try that again tomorrow and I will let you know about the results.

@skinny: I've tried disabling WEP on my home network since I worried that perhaps my neightbour's signal wasn't very strong which might have caused some problems, but it's still not working.  When it worked for a bit, it was when I reinstalled Ubuntu (just because I was at my wits' end and couldn't think of anything else, and well, after a week and a half of trying, resinstalling the OS doesn't seem like such a drastic move afterall ^^), this time downloading the ndiswrapper GUI then, connecting it through ndiswrapper GUI/network manager (I think ndiswrapper GUI directed me to network manager to configure the netowrk) and testing it on my neightbour's unencrypted network.  I decided to try to connect it to my home network (which has WEP encryption) and it no longer worked.  I rebooted my laptop and tried to reconfigure wlan0 to connect back to the unencrypted network, and it wouldn't let me, giving me the error: 8BIA: 

SET failed on device wlan0; invalid arguments.  

I'm still having this problem now, even if I use sudo and turn off all encryption, I can't configure my wlan0 settings, so if anyone knows what's causing this problem or if I can configure my wlan0 settings my editing a file(?), please let me know?
The only messages that caught my attention in dmesg were:

wlan0 link not ready
ndiswrapper setting essid failed
No IPv6 routers found

Though I'm not sure if these messages are even relevant!
I would also like to ask if a key in the form of 5667812903 is ASCII or hex?

Thanks so much!

---

### Post by kvonb on 2007-01-06
I would suggest this:

Open a terminal (Menu->Applications->Accessories->Terminal) and type this in:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.original

```

Which will make a backup copy just in case!

Then type this:

```
sudo gedit /etc/network/interfaces
```

add this lot to the end of the file:

```
iface wlan0 inet static
address 192.168.1.2 #never use the .1 it is usually reserved for routers etc'
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 123.456.789.123 # change this number to your nameservers number
broadcast 192.168.1.255
wireless-essid YOURNETWORKNAME
wireless-mode managed
```

Now add a # in front of these network devices: eth0, eth1, ath0

Save and exit then reboot and see if it works

Regards, Kev :)

---

### Post by lemoniceblock on 2007-01-07
Hi all!
Thanks Kev, I didn't get to try that out though because I tried network-manager first and it actually worked ^^
My problem now though, is that I can only get it to work when my network's security is disabled.  I only have WEP encryption and made sure that everything was entered properly (it's an open key) but it just doesn't seem to let me connect to it.
Any ideas anyone?
Once again, thanks so much, I'm pretty ecstatic right now since this is at least a leap after 2 weeks, and I'm running out of ways to say thank you =P

---

### Post by Kulgan on 2007-01-07
> My problem now though, is that I can only get it to work when my network's security is disabled.

I had that in the start as well. i could connect to the non-secure routers but not the one at home. I think it has something to do with the network-manager, because it worked - and still does, of course - when I entered the details in /etc/network/interfaces and let things run their course. It might not be the same problem, though...

---

### Post by lemoniceblock on 2007-01-07
Hihi~
I'd like to confirm something before I go ahead and try it: do I edit the /etc/network/interfaces file but keep network-manager and connect using network-manager?

Right now, my /etc/network/interfaces file looks like this:
```

auto lo
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
iface wlan0 inet dhcp

```

I'm adapting this from kvonb's post since I don't think I'll need to keep my IP static if I'm going to stick with network-manager.
```

auto lo
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
iface wlan0 inet dhcp
wireless-key xxxxxxxxxx

```
Does that look right?  My wep key is 128 bit Hex.  If it doesn't look right, could you please post your file?

Thanks so much!

---

### Post by Kulgan on 2007-01-08
You need to specify an essid. This is my file:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wireless-essid home
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

```

I haven't linked wlan0 to eth1, so I treat eth1 as you would wlan0.

network-manager is basically just a frontend for the /etc/network/interfaces file (as far as I know - correct me if I'm wrong), at least, that is what it has worked as for me. What you would do after editing the file would be 
```
ifdown -a
```
to turn off all the interfaces, followed by
```
ifup -a 
```
to turn them back on again. 

That second command will take all the setting from /etc/network/interfaces and use them as it should.... well... in theory...
When it tries to start the one that has the essid set, you will get a bunch of output about DHCPREQUESTs. That is what is interesting to us. Post the output of 'ifup -a', would you?

-K

---

### Post by lemoniceblock on 2007-01-09
Hello!
Sorry, but it doesn't seem to be working; when I edited the /etc/network/interfaces file and typed ifdown -a, network-manager showed that all networks were disconnected.  Then I typed ifup -a and tried to connect to my home network.  Everything but wlan0 seemed to be fine; wlan0 had the good old message of 'no dchcp offers received'.  The same message that I had before network-manager worked.  Network-manager then prompted for the wireless key but was still unable to connect.  I'm suspecting that the WEP is somehow stopping my router from giving my laptop an IP address?  I thought that in case it was a clash with eth0, I also tried disabling eth0 but nothing seems to work yet ^^
Thanks so much for helping me stick with this though =D

---

### Post by Kulgan on 2007-01-09
hmm... stumped... I never bothered with the bit about changing to wlan0 - don't fix things that haven't broken. Or tweak them :D

It may not be the same thing as i had, but it sounded like it. Hmm... if you are not getting DHCP requests, you could always try turning off DCHP on the router. A little drastic, but perhaps it might be worth a try. And perhaps you should not take any of my fool advise...

-K

---

### Post by lemoniceblock on 2007-01-10
=P  Hey, your advise is definitely not fool!  At least I can connect to a wireless connection after 2 weeks of 0 connection it's very encouraging really! ^^  I will try that this weekend, thanks!

---

### Post by VoodooSmurf on 2007-02-06
> I would also like to ask if a key in the form of 5667812903 is ASCII or hex?

The wep should always be in Hex. whenever I got mine working, I couldn't connect to my secure router.  I found that it was sending my web in ascii, switched to hex, no more problems

---

### Post by lemoniceblock on 2007-02-24
Hey all!~ Problem got solved [here]("http://ubuntuforums.org/showthread.php?t=324967").  Thanks again for all your help ~^^~

---

### Post by chutki on 2007-07-08
i am having a problem with wireless when i go on command promt type 1spci then i get a response that the command isn't found..need help connecting to the internet i have a linksys wirelessG usb network adaptor 2.4Ghz 802.11g... what do i do... plz help...

---

