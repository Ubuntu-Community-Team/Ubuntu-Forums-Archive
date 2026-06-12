---
title: "[SOLVED] Unable to connect to wireless router with Ubuntu 7.10 Server"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by MyrddinWyllt on 2008-01-08
Hello. I am trying to get a computer running Ubuntu 7.10 Server to connect to my wireless router. I have (as far as I know) the drivers properly installed (using bcm43xx-fwcutter). lspci reports that I have a Broadcom Corporation BCM4306 wireless lan controller, its a Linksys card. I used the tutorial here to get wpa_supplicant working: [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

ifconfig shows (cut out the eth0 and lo0 stuff):
> 
eth1 Link encap:Ethernet HWaddr XXXXXXX
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b) TX bytes:462 (462.0 b)
       Interrupt:11 Base address:0x8000


iwconfig shows:
> 
eth1 IEEE 802.11b/g ESSID:off/any Nickname:"Broadcom 4306"
       Mode:Managed Frequency=2.437 GHz Access Point: Invalid
       Bit Rate=1 Mb/s Tx-Power=15 dBm
       RTS thr:off Fragment thr:off
       Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
       Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries:0 Invalid mist:0 Missed beacon:0


Using iwlist I can see the router (sudo iwlist eth1 scanning). The only thing I notice wrong the frequencies are a mismatch, 2.437 on the card and 2.422 on the router. 2.422 should be channel 3.

The router is set for WPA-PSK.

My /etc/wpa_supplicant.conf:
> 
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="myID"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=a really big long string
}


The psk here matches the one I got from wpa_passphrase

My /etc/network/interfaces (minus the lo and eth0 stuff):
> 
auto eth1
iface eth1 inet dhcp
wireless-essid myID
gateway 192.168.1.1
wireless-channel 3
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


We have MAC filtering enabled on the router, but I have the MAC entry in the table, so that should be clear. eth0 is my wired connection, I commented out #auto eth0 so that it does not come up.

I cannot ping the router.
> 
user@compy:/etc/network$ ping 192.168.1.1
connect: Network is unreachable


If I missed any info you need, please let me know. Thanks in advance for any help!

---

### Post by macogw on 2008-01-08
If I recall correctly, that card only does unencrypted or WEP using the Linux drivers.  Ndiswrapper + Windows drivers might be the way to go for this one.

---

### Post by MyrddinWyllt on 2008-01-08
> **macogw said:**
> If I recall correctly, that card only does unencrypted or WEP using the Linux drivers.  Ndiswrapper + Windows drivers might be the way to go for this one.

Do we have a second on this? I fought with this thing for a while trying to get it to work, I'd hate to switch to ndiswrapper and have it turn out that fwcutter could be made to work with something simple...(not saying you are wrong, just really hoping..)

If I do have to go ndiswrapper, does anyone know of a good walkthrough? THere is one here: [http://ubuntuforums.org/showthread.php?t=492358](http://ubuntuforums.org/showthread.php?t=492358) and it is for the same chipset I have, but I would like maybe to have one with a successful outcome...

I swear, WPA is more trouble than it is worth sometimes...I've run into a ton of devices that don't support it. Other folks on this network, however, so I really can't just blow out WPA in favor of WEP (and would much prefer the added security, anyway...)

---

### Post by ayenack on 2008-01-08
According to this the card does support wpa.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28bcm43xx%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28bcm43xx%29)

There's also a ink that leads to a page that help with setup, might be useful.

---

### Post by MyrddinWyllt on 2008-01-08
> **ayenack said:**
> According to this the card does support wpa.



I have used the card under windows with WPA, so the card supports it with windows drivers. I'm just hoping that it works under linux..

---

### Post by ayenack on 2008-01-08
Have you tried connecting to the router with your wired connection? Just wondering if the gateway address is correct as it says access point invalid and you can't ping it. You're sure it's set to the correct channel? Also not sure if this is relevant but might be worth trying sudo dhclient.

---

### Post by MyrddinWyllt on 2008-01-09
> **ayenack said:**
> Have you tried connecting to the router with your wired connection? Just wondering if the gateway address is correct as it says access point invalid and you can't ping it. You're sure it's set to the correct channel? Also not sure if this is relevant but might be worth trying sudo dhclient.

I connected to the router with a wire and successfully ran apt-get update and upgrade, as well as installing the fwcutter modules. I checked the router, and it is set to channel 3, and iwlist also shows it on channel 3. I can't confirm that the card is looking on channel 3, especially since it is reporting a different frequency than channel 3. The mac sitting next to the ubuntu machine is on the wireless and can ping 192.168.1.1. I ran sudo /etc/init.d/networking restart and picked up an address for IPv6, but still have no real address that I can use. Unsure where the v6 addy came from.

sudo dhclient reports this:
> 
No DHCPOFFERS reveived.
No working leases in persistent database - sleeping


I would just leave the computer on the wired connection, but it is in a totally different part of the house, and isn't an option, unfortunately.

Is my configuration correct?

---

### Post by MyrddinWyllt on 2008-01-09
One thing I've noticed, the ubuntu machine is using 255.255.255.255 as a net mask, while the mac is using 255.255.255.0. I'll look into changing that later, could be the problem....

Any other thoughts?

---

### Post by aeiah on 2008-01-09
does the lack of gaps in this line affect the command?
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
as opposed to:
pre-up wpa_supplicant -B w -D wext -i eth1 -c /etc/wpa_supplicant.conf?

also, you should probably try and connect with WEP or open to see if WPA is really the problem, if possible.

maybe try changing your ssid in ifconfig from off/any to myID too, just to make sure its not that too.

---

### Post by ayenack on 2008-01-09
> **MyrddinWyllt said:**
> One thing I've noticed, the ubuntu machine is using 255.255.255.255 as a net mask, while the mac is using 255.255.255.0. I'll look into changing that later, could be the problem....

Any other thoughts?

Well spotted. For sure that'll make a difference. Should change net mask to 255.255.255.0 might fix the problem. As far as I can tell everything else looks correct.

Still strange that it's reporting the wrong frequency though.

Just read your first post again. I'm curious about the card you have because it's reporting as a Broadcom BCM4306 yet you say it's a Linksys card? So I'm a little bit confused about that.

---

### Post by ayenack on 2008-01-09
kevdog has a pretty useful page that you should take a look at.

[http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless)

---

### Post by MyrddinWyllt on 2008-01-09
I was under the impression that the ssid="myID" in my wpa_supplicant.conf and the wireless-essid myID in the interfaces file set the ssid from off/any to the correct thing. Between the fact that the ssid is still off/any, and the channel is still wrong, I am thinking possibly that there is a syntax error in my setup or there is something I have not updated that is preventing it from working.

I will look up and fix the netmask upon my return home, hopefully that fixes it...

edit: I have a linksys wireless card, it has a broadcom 4306 chip on it, as far as I can tell.

---

### Post by ayenack on 2008-01-09
> **MyrddinWyllt said:**
> 
edit: I have a linksys wireless card, it has a broadcom 4306 chip on it, as far as I can tell.

That just doesn't sound right to me. I'll do a bit of hunting around on the net to see if this is the case. can you give me the model and/or part number actually written on the physical Linksys card to make things a bit easier.

EDIT: You know what the later versions of the Linksys WMP54G and related cards do seem to have the Broadcom BCM 4306 chip-set.

In the mean time. Suggested something like this earlier but this is slightly different. In terminal.

**gksu nano /etc/rc.local**

When the file opens add this to the bottom.

**dhclient eth1**

Then reboot and cross your fingers. If that does not work try. Open terminal and try this to get it going. It has the added eth1 that I'm guessing you did not add when you tried it earlier.

**sudo dhclient eth1**

If this works it's entirely possible that you will have to type this every time the network is restarted.

Another thought occurs to me have you got hidden ssid on your router? If you have then that will also stop you from connecting using Linux.

---

### Post by MyrddinWyllt on 2008-01-09
There is definitely some funkiness going on.

I added:
netmask 255.255.255.0

to my /etc/network/interfaces file, and

dhclient eth1

to my rc.local file, and rebooted. dhclient is still looking to 255.255.255.255 when scanning. The essid of eth1 has finally changed to the correct essid, and the frequency has also changed to be correct, but I still have no connection. I did use sudo instead of gksu, I am running without X, and gksu is not installed, and in order to install it I'd have to move my computer back down to by the router. Unsure if this is a problem.

I am using a Linksys WMP54GS card, unsure of the revision, but lspci reports it as a broadcom.

The router is set to broadcast ssid, I read a few things saying hiding it wasn't all that much more secure (someone claimed it was even less secure..) and not broadcasting was causing issues with other PCs.

On a side note, I have to hit enter after the computer boots up to get the login screen, it stops after it runs the "local boot scripts", which I see now is the rc.local. rc.local has an exit 0 at the end of it, will removing this make it go straight to login?

---

### Post by MyrddinWyllt on 2008-01-09
I notice that the entirety of my /etc/dhcp3/dhclient.conf file is commented out. It appears to be a sample file. The one section mentions an "option subnet-mask" and its value is 255.255.255.255, if I add some things to this file, specifically this option on eth1, might that help? I tried, but was just sort of winging it and it threw an address mismatch error, obviously I wasn't doing something right.

---

### Post by MyrddinWyllt on 2008-01-10
Do I have any hope of getting this working? Or should I just give up?

Somewhere recommended disabling IPv6, that didn't work.
I changed some things according to the kevdog post, but it still doesn't work.
I tried forcing iwconfig to see my access point with the ap flag, no dice.
dhclient now loops endlessly....

Is there a way to get the restricted and other repositories on CD? If I could just download an ISO, I wouldn't have to physically move my computer every time I wanted to try and install a new package until I get my wireless working. 

I'm considering trying ndiswrapper, and maybe installing Gnome etc to get the graphical interfaces for network configuration, I can always just set the computer to boot to runlevel 3 and not worry about graphical overhead later.

---

### Post by ayenack on 2008-01-10
Apparently others have got this card to work but all of these were on desktop and not server as far as I can tell. Don't think you can use the restricted drivers on server install BTW. Different kernel.

It seems like you have everything right to me so I'm stumped.
Have you posted on kevdogs thread at all or on the original tutorial thread, they might see something we've missed. 

As for ndiswrapper seems like a good idea to me but may need to do a fresh install to get a clean system.

I've also read that on desktop install some have been able to install the drivers fairly easily basically by downloading the restricted drivers and wpa_supplicant I think, there might even be a script somewhere for this. Also on desktop you can stop gnome from loading so you have a command line system and a less hungry system by doing this.

**sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm**

It renames the original file preventing it from booting. You'd reverse it to get it working again.
Or you could install bum (Boot Up Manager) to edit your boot. It's in the repo's.

Also if you want to get restricted drivers on cd/dvd you could use aptoncd it's in the repo's but again I think this will only work on desktop and not on sever. You could also set up your own apt repository on a spare comp on the network but that's not much good as you wont be able to connect to it. Not to sure it's a good idea to install gnome onto the server install probably better to install desktop and set it up to your liking.

One last thought is it possible to move the router to the server and use the wired connection?

---

### Post by ayenack on 2008-01-10
Have you got anything like this in your /etc/dhcp3/dhclient.conf file?

[B]request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;[/B]

If you haven't add it.
If you have it can sometimes be better not to and just have the "request" statement alone.

You could also try adding something like this to dhclient.conf. If the above does not work it's worth a try.

[B]alias {
  interface "eth1";
  fixed-address 192.168.1.100;
  option subnet-mask 255.255.255.0;
}[/B]


> On a side note, I have to hit enter after the computer boots up to get the login screen, it stops after it runs the "local boot scripts", which I see now is the rc.local. rc.local has an exit 0 at the end of it, will removing this make it go straight to login?

Don't know. As far as I know the "exit 0" has to be there. I would think it would be more like an option ie. "exit 1" or something alike but no idea really.

---

### Post by MyrddinWyllt on 2008-01-10
> **ayenack said:**
> Have you got anything like this in your /etc/dhcp3/dhclient.conf file?

[B]request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;[/B]

If you haven't add it.
If you have it can sometimes be better not to and just have the "request" statement alone.

You could also try adding something like this to dhclient.conf. If the above does not work it's worth a try.

[B]alias {
  interface "eth1";
  fixed-address 192.168.1.100;
  option subnet-mask 255.255.255.0;
}[/B]


I do have the request string in there, but that is about it. I tried the alias thing earlier, without the fixed-address part, as I'm using dhcp. Is that address for the router, or for the device?

I might give it a whirl on ubuntu desktop. I'm pretty sure I have the restricted drivers for my card working, if I can see the router with iwlist it stands to reason I have at least some functionality with my card. I'll try posting on kevdogs thing and see if anyone can help me there. Thanks!

---

### Post by gbold on 2008-01-10
I had a problem with my Dell laptop (Intel Pro Wireless) and I went into my /etc/network/interfaces file and deleted evrything but the first 2 lines (about the LO connection).  Rebooted and viola!
Greg

---

### Post by ayenack on 2008-01-10
Having the fixed address doesn't matter when your using "alias" what it does is use dhcp network but will always try to get the dhcp server to give it that address that's why I set it high at 100 because that address will never be in use on a small dhcp network and it makes it easier to troubleshoot. After all we are using dhclient.conf ;)

> Is that address for the router, or for the device?

It'd be the device address on the router. So say you routers default address is 192.168.1.1 the first address given by the DHCP server on the router to a network client would be 192.168.1.2 and so on.

Think it's a good idea to post on kevdogs thread he's seem really clued up on these specific cards.

---

### Post by ayenack on 2008-01-10
> **gbold said:**
> I had a problem with my Dell laptop (Intel Pro Wireless) and I went into my /etc/network/interfaces file and deleted evrything but the first 2 lines (about the LO connection).  Rebooted and viola!
Greg

Wouldn't work in this instance Greg I don't think. He's running server and he's also using a script. I guess you were running desktop and had used Network Manager to set up the card. Maybe also set to roaming.

Thanks though.

---

### Post by ayenack on 2008-01-10
If you're going the desktop route I have got a good bit of news for you. Have a look at this thread and scroll down to the 7th post. There's a .deb driver that you can just download and double click to install then reboot and you should be able to connect.

[http://ubuntuforums.org/showthread.php?t=428099&highlight=Linksys+WMP54GS](http://ubuntuforums.org/showthread.php?t=428099&highlight=Linksys+WMP54GS)

Seemed to work for the user hope it'll work for you.

---

### Post by MyrddinWyllt on 2008-01-10
Tried Greg's approach, just because I'm rapidly running out of options to save this install (I just commented them out, not delete). Backtracked a bit, so oh well, cost me all of 2 minutes.

Added the alias entry, now I have an eth1 and an eth1:0 entry under ifconfig (not iwconfig, however).

I am pulling down a desktop ISO as I write this, if all else fails I'll throw the desktop on there and move myself back down to the wired connection. Ubuntu is lovely when dealing with adding packages, so it should be a piece of cake to grab LAMP. It works SO much better with a network connection, however...

---

### Post by ayenack on 2008-01-10
There's the link above for the .deb file that should do the job on desktop.

Not sure if you need this. Here's a great tutorial on installing LAMP on desktop.

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by MyrddinWyllt on 2008-01-10
One thing I just noticed with that .deb...its a different chipset, any idea if that will make a difference?

---

### Post by MyrddinWyllt on 2008-01-11
I have ubuntu desktop installed, hopefully the rest will go a lot smoother. Unfortunately I'm skipping out of town for a few days, so I can't finish the install...gah!

Thanks for the help, I will post here again with results, rain or shine.

---

### Post by ayenack on 2008-01-12
Hadn't noticed the driver was for a different chip-set. It seems that people with the same card and chip-set as you have used it successfully. You could also try the Restricted Driver Manager to install the driver but I'm not sure how well it works.

> Thanks for the help, I will post here again with results, rain or shine.

No probs. Not sure I've ben that much help but it's alway handy to have someone to bounce ideas off I suppose. I'll check back in couple of days see if thinks have gone well or not.

---

### Post by MyrddinWyllt on 2008-01-26
So, I have a clean install of Ubuntu 7.10 Desktop, plugged into the wired connection, updated all my installed packages (I love synaptic...), and then downloaded and installed that .deb.

Everything worked beautifully until I tried to get on the wireless. I unchecked the roaming setting and put in my WPA key and all that jazz, but still no love. I noticed my connection was looking at the wrong channel, so I fixed it, but still nothing. If I run iwlist it shows that I can see the router, but I still can't seem to get it to work. 

Really getting irritated here. I like linux, I've used it at school in labs and in my room, but this wireless thing is just a pain in the rear end. As much as I hate to admit it, this situation is definitely a sign of why Linux isn't really desktop ready...(not bashing it...at least it isn't a terminal disease like Windows...and OS X has plenty of its own issues)

If there isn't anything that anyone can suggest, I don't really know what I'm going to do. I intended on running this as a server for a web page (probably just gonna be for my household, as my verizon connection probably blocks port 80...)

Any further suggestions?

---

### Post by MyrddinWyllt on 2008-01-26
Well, I have a pseudotemporary solution. I have the computer plugged online via a wired connection, so until I figure out this wireless thing I at least have it working. Its in a bit of a awkward place, so if anyone can help out with the wireless it would be much appreciated

---

### Post by ayenack on 2008-01-27
Hello MyrddinWyllt.

Thought you'd given up. If you can see the router at least that shows that the card is working so it's either a problem with the WPA Encryption on Ubuntu or maybe with the way the router is set up.

Can you try this for me see if it works. In terminal.

**gksu gedit /etc/network/interfaces**

Add this to it and comment out any other entries for the wireless card.

[B]
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up[/B]
**pre-up iwconfig wlan0 essid** SSID here
**pre-up iwconfig wlan0 mode managed**
**pre-up iwpriv wlan0 set AuthMode=WPAPSK**
**pre-up iwpriv wlan0 set EncrypType=TKIP**
**pre-up iwpriv wlan0 set WPAPSK=**Your WPA PSK Key here
**pre-up iwpriv wlan0 set SSID=**SSID Here

You might have to change the **wlan0** to the name of your card i.e. **rausb0** or whatever. This is how I connect to a WPA protected network.

Reeboot.
Sometimes after you do this for the first time you need to run the commands bellowto get a connection after reboot. Run these commands in terminal.

**sudo ifconfig wlan0 up**
**sudo iwconfig wlan0 essid** Network Name
**sudo iwconfig wlan0 key** Your WPA key
**sudo dhclient wlan0**

If that doesn't work I'm stumped.

---

### Post by MyrddinWyllt on 2008-01-28
Nope, haven't given up yet. I'm rather stubborn.

I'll give that a try as soon as I can. The machine is running headless connected via ethernet, its basically blocking a whole bunch of shelves, so I'm hoping to get it out of there as soon as I can. I'd try your suggestion right now, but I'm sshing in from my mac in a different room, but as soon as I can get in there to work on it some more, I'll give it a whirl.

Thanks for all your help, I really hope this works :)

---

### Post by MyrddinWyllt on 2008-01-31
When I run 
sudo iwconfig wlan0 key Your WPA key
I get an error saying
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "thisismywpakey".

Should the key be in clear text or in the massive hex gibberish?
Thanks

---

### Post by MyrddinWyllt on 2008-01-31
Now that I can SSH into the box via the wired LAN, I can give you a more verbose output from all the things

ifconfig:
> 
login@COMPY:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:28yaddayadda  
          inet addr:192.168.1.36  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::204:75ff:fe9c:2948/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61478 (60.0 KB)  TX bytes:34314 (33.5 KB)
          Interrupt:19 Base address:0x2800 

eth1      Link encap:Ethernet  HWaddr 00:12mmmMACD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:30 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:7307 (7.1 KB)
          Interrupt:11 Base address:0xc000 

eth1:avah Link encap:Ethernet  HWaddr 00:MACMACMAC2D  
          inet addr:169.254.4.113  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


iwconfig:
> 
login@COMPY:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"myssid"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.422 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


my interfaces file
> 
login@COMPY:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet dhcp
pre-up ifconfig eth1 up
pre-up iwconfig eth1 essid myssid
pre-up iwconfig eth1 mode managed
pre-up iwpriv eth1 set AuthMode=WPAPSK
pre-up iwpriv eth1 set EncrypType=TKIP
pre-up iwpriv eth1 set WPAPSK=mywpakey
pre-up iwpriv eth1 set SSID=myssid
wireless-channel 3

#iface eth1 inet dhcp
#wireless-channel 3
#wpa-psk hexgibberish
#wpa-driver wext
#wpa-key-mgmt WPA-PSK
#wpa-proto WPA
#wpa-ssid myssid

#auto eth1


---

### Post by ayenack on 2008-02-01
OK I'm stumped by this. Let me have a think for a bit. The WPA Key should be entered in clear text. I take it you're entering eth1 and not wlan0 as you put in the above post when trying to enter WPA Key? May be an idea also to try it without the channel listed try commenting it out and see what happens. It should find the channel automatically. I'm sure this shouldn't be this hard you know.

Also don't forget that if you have your wired connection connected at the same time as the wireless chances sre that one or the other will not work. The way around this is to either edit iptables manually or install Firestarter firewall open it and go to Preferences>Network_Settings> and then enable internet connection sharing and enable DHCP Server for local network then set the IP Address of the DHCP Server range for me in iptable this is set to 192.168.1.2 to 192.168.1.254 your's is different if I remember correctly. All this can be done in Firestarter if installed. But not hard to do in any case.

---

### Post by MyrddinWyllt on 2008-02-01
my card displays in ifconfig as eth1, I can try replacing it with wlan0 and see what happens. I have been leaving the wired enabled to avoid lugging a monitor around (only one I got for it is a 17" CRT...sucker weighs a ton). What is the best way to disable the wired connection?

I swear I must be doing something wrong, or changed a setting or something. Things just seem to get more complicated when I am working on them. Can't seem to get my router to forward http requests either...but thats a different story

---

### Post by ayenack on 2008-02-02
Theres an obvious problem with disabling eth0 and that's if you do you may well not have access to the box unless it's physically in front of you. But worth the effort just to see if the wireless will connect or not?

Best way to disable wired is to ssh into the box then.

**sudo nano /etc/network/interfaces**

And comment out "auto eth0" or all of the eth0 config then press "ctrl o" to save and "ctrl x" to exit. I would just comment out the "auto eth0" to stop it coming up then Reboot. To do this over ssh do this.

**sudo reboot** (And hope that wireless connects)

You can bring network interfaces up and Down with the bellow commands. 

**sudo ifconfig eth0 up** (to bring it down just change "up" to "down")

BTW. When I said about wlan0 I was referring to this.

> When I run
sudo iwconfig wlan0 key Your WPA key
I get an error saying
Error for wireless request "Set Encode" (8B2A) :
invalid argument "thisismywpakey".

You have put wlan0 rather than eth1 but I'm sure you did not do this when trying to config the card. Have you checked back on any of the other HOWTO's to see if there's anything we're missing.

---

### Post by Chuckels550 on 2008-02-05
I used a version of what you are trying to set up running my wireless connection for Ubuntu 7.04 Desktop and MythTV box.  However, for whatever reason, that approach wouldn't work for Ubuntu 7.10.  The networking interface seems to have changed and I don't know how.  What did work for me, but not automatically as part of the boot process, was to replace Network Manager with wicd.  

To install wicd, add the following repository to your Synaptic repositories, reload Synaptic and then install wicd.

deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras

When you launch the Wicd Manager, remember to refresh the list of wireless connections available.  Then just find your essid, highlight it and configure the preferences as well as the properties.  The next step is to restart the networking in a terminal instance.  After the networking restarts, connect to the desired wireless connection.

 By the way, if I were you I would try a connection with no encryption mode first and then only if successful try with the encryption mode.

---

### Post by ayenack on 2008-02-05
Have just found this which seems to solve the problem for most. Might have to remove all the other config files:(

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Not sure about this but if wicd is installed don't you have to "sudo apt-get purge network-manager & gnome-network-manager" for it to work?

EDIT: Reading through the thread this should defo work with your card. Easy to.

---

### Post by MyrddinWyllt on 2008-02-05
> **ayenack said:**
> 



You have put wlan0 rather than eth1 but I'm sure you did not do this when trying to config the card. Have you checked back on any of the other HOWTO's to see if there's anything we're missing.


Yeah, I used eth1. It seems I needed to specify that I was using an ascii key, it takes

sudo iwconfig eth1 key s:mywpakey

---

### Post by MyrddinWyllt on 2008-02-05
I don't appear to have any eth0 entries in my /etc/networks/interfaces file. Odd, as I am connected to the computer via a wired lan, using eth0.

The plot continues to thicken. That thread you posted mentions that it won't work under Gutsy, and they were right, got a nice seg fault when I tried.

I will move the monitor again and just unplug the computer from the wired connection, with any luck that will kill the eth0 connection (maybe a reboot will help it).

Nothing like a little wireless networking to make you feel like you are doing everything wrong. I've successfully set up NFS+ between ubuntu and red hat machines before, configured network printing, and a pile of other stuff...why is this so difficult?? 

I blame microsoft. Despite there being no good reason, it seems to make everyone feel better when they do :)

---

### Post by ayenack on 2008-02-05
This is driving me mad btw. Thought I saw people who were using 7.10 with that driver AGggrrrr...

Just a thought when you unplug the wired connection try the original config and comment out the one I suggested I have a feeling that that may not work now.

I blame Microsoft.... I do feel better :)

---

### Post by MyrddinWyllt on 2008-02-05
Right, so new twist. I unplugged the cable, and obviously the computer didn't have a network connection. It had a handy little dialog that allowed me to enter my wpa key to connect to the router, that it saw, which was the correct one. I tried, it failed. My router, however, lists the computer under its wireless clients, but as "authenticated" rather than "authorized," as the others on the network are. The routers help dialogue informed me oh so helpfully that that particular piece of information shows the status of a client. Not what that status means.

Using the old interfaces still doesn't work. eth0 still insists on coming up at boot, despite the lack of eth0 entries in my interfaces file. 

editing while I am still typing this post...I just switched back to the new interfaces, I have a nice signal strength bar showing 0% signal, but still no IP.

I am tempted to think that maybe it is my router causing the issues, but as far as I can tell everything is the same for this computer in there as for the others on the network. And I've checked to make sure I have the right MAC in the filter about 3000 times. Just in case...

I will keep fiddling...maybe I will fix it by accident

---

### Post by MyrddinWyllt on 2008-02-05
any word on why eth0 insists on coming up?

---

### Post by MyrddinWyllt on 2008-02-05
So, on a whim I tried installing that thing again, and it worked.

However, it still is weird. ifconfig shows nothing. ifconfig eth1 up fails, saying there is no such thing as eth1. wicd fails silently. 

I first used the app to back out the firmware, then installed ndis + windows drivers. It installed, but I got nothing. I then used it to install wicd, still nothing. And then the firmware. Still nothing.

---

### Post by MyrddinWyllt on 2008-02-06
I am wondering if I mucked something up. Whenever I get around to playing with the computer again trying to fix it I will (unless someone has a suggestion) do a clean install of Ubuntu 7.10 Desktop, pull down the installer from a few posts up, and run it. With any luck, any weird thing I broke will unbreak, and life will be golden. If not, I will attempt to restrain myself from going all office space on it with a baseball bat.

---

### Post by ayenack on 2008-02-06
I think that's your best bet. I'm totally stumped by this now. Am I correct in thinking that 7.10 has a restricted driver for the card now from restricted drivers manager or am I just imagining things? More important if there is does it work.

I suppose you could go back to Feisty and use the guide I posted earlier this is what I had to do with a server on my network using wired to connect to the network and wireless (D-Link DWL-G122 rev B1) to connect to internet for updates because I could not get it working on Gusty.

Post back whatever and let me know what the score is anyway.

One last thing I think I read somewhere that your card might come up as eth0 and not eth1 so might want to take that into consideration when trying to work out why eth0 keeps coming up. So might be worth trying ifconfig eth0 up also.

---

### Post by MyrddinWyllt on 2008-02-06
I am pretty sure 7.10 can get a restricted driver. I will try without installing any restricted anything first, just install, run an aptitude update and upgrade, pull down that installer and let it fly. 

Though I likely won't be buying anything now, and hopefully in the future will have a wired connection for servers, what kind of wireless cards seem to work best under linux?

---

### Post by MyrddinWyllt on 2008-02-06
got wicd running...had a feisty repository in synaptic, used the gutsy one that was posted above (should have read that first...don't work on stuff while frustrated, heh)

the script does not install ndiswrapper for some reason, I am attempting to install it myself...

ndiswrapper and wpasupplicant are installed. 

I can't get wpasupplicant started, though. It explodes with a lot of output. 

wicd doesn't even recognize the fact that I have a wireless card.


Thoughts? Or should I just roll back to Feisty...

---

### Post by ayenack on 2008-02-06
I'd say roll-back to Feisty if it works for sure with your card which it's meant to by all accounts. There's not that much difference between Feisty and Gusty. As always the ideal for a server is a Gigabit connection to a Gigabit hub or router but then there's those pesky cables:(

As for wireless card for Ubuntu check out the Ubuntu Documentation [here]("https://help.ubuntu.com/community/?action=fullsearch&context=180&value=wireless+cards&titlesearch=Titles"). There's a list of cards and how well they are supported.

There's also [this]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28%28HardwareSupportComponentsWirelessNetworkCardsLinksys%29%29") more or less same as above but a bit more info.

---

### Post by ayenack on 2008-02-07
I want to track down exactly what revision of the card you have can you do this in terminal.

**sudo lspci -v**

The sudo is just so it'll give the capability of the card also. If you scroll down to the Broadcom Corporation BCM4306 (rev ??) or something similar section it should show the rev might help to solve this.

You'll be looking for something like this.

00:0b.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T **(rev 01)**
        Subsystem: Micro-Star International Co., Ltd. Unknown device 590c
        Flags: bus master, fast devsel, latency 32, IRQ 16
        Memory at dfffa000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

---

### Post by MyrddinWyllt on 2008-02-07
I'll get you the output from lspci at some point today, forgot to reinstall the ssh server...oops

Should I still go ahead with the feisty install?

---

### Post by ayenack on 2008-02-07
[QUOTE=MyrddinWyllt]Should I still go ahead with the feisty install?[/QUOTE]

Not just yet if that's OK by you. Unless you know for sure that you can make it work on Feisty, then there's no reason not to I should think. Save a hell of a lot of head scratching on both our parts. :) 

I'm sure this card can be made to work on 7.10. Doing it is another thing altogether though.

---

### Post by MyrddinWyllt on 2008-02-07
I had heard 7.10 was better with wireless stuff, so I figured it would be a breeze, like most stuff in Ubuntu. I'll hold off on the Feisty install, when I left for work this morning there was 14 hours left in the download (must have picked a slow mirror...you'd think I'd get a blazing fast connection from Argonne lab...though they may have old images hosted on someplace with a slower connection, since there probably isn't many downloads from them), so it won't be hard.

I'm sure there is just some stupid little .conf entry or something I'm forgetting to do or goofing up that is making this not work. Do you know of a good tutorial for ndiswrapper and wpa_supplicant? Maybe the ones I've been reading have been leading me astray. Everyone else can get their 7.10 on wireless, so I should be able to as well...

---

### Post by ayenack on 2008-02-07
I'll try to find something on ndiswrapper and wpa supplicant but I've been looking at a lot of howto's about your card and they seem to contradict each other. One will say they used ndiswarpper no problem at all and another will say that ndiswrapper is a no go and that you have to use this driver or that driver. It's strange. That's why I want to know the exact revision of your card, might make things a bit clearer. So when you get a chance sudo lspci -v and see what rev it is.

I've also seen that the card simply will not work on Linux at all but this clearly isn't true because people are posting that they have it working.

I have to say that I never use ndiswrapper and have always found it to be a bit of a hack to be honest. I suppose you could go out and buy a wireless card that will defo work with 7.10. Probably cost about $20-$30. Shouldn't have to though IMO.

---

### Post by MyrddinWyllt on 2008-02-07
It seems I have a revision 3 card.

> 
$lspci -v -nn | tail -n5
02:0d.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
        Subsystem: Linksys Unknown device [1737:0015]
        Flags: bus master, fast devsel, latency 32, IRQ 11
        Memory at feaf6000 (32-bit, non-prefetchable) [size=8K]



It is a Linksys WMP54GS. [Here]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1115416826820") is the product page

edit: forgot to run it with sudo, but the output is the same anyway

---

### Post by MyrddinWyllt on 2008-02-07
> **ayenack said:**
>  As always the ideal for a server is a Gigabit connection to a Gigabit hub or router but then there's those pesky cables

Why use 1000Base-X when you can use [100GBase-X]("http://en.wikipedia.org/wiki/100_gigabit_Ethernet")? 

 bus speeds aren't up to snuff yet...and there's always that pesky bottleneck called "the speed of light"

oh well...

---

### Post by ayenack on 2008-02-07
So that means you should be able to use Restricted Drivers Manager from System menu to install the firmware and then use this thread to config it.

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

It shows you how to install wpa supplicant and pretty much walks you through the set up. It's an excellent post that covers the whole shebang. You'll need a clean install I would think.

---

### Post by ayenack on 2008-02-07
> **MyrddinWyllt said:**
> Why use 1000Base-X when you can use [100GBase-X]("http://en.wikipedia.org/wiki/100_gigabit_Ethernet")? 

 bus speeds aren't up to snuff yet...and there's always that pesky bottleneck called "the speed of light"

oh well...

LOL.

T1 anyone?

---

### Post by MyrddinWyllt on 2008-02-07
Peachy, I'll definitely check that out when I have a chance.

T1 lines are so old fashioned, 100GBase-X is >650x faster :) 

Of course, speed isn't everything...

---

### Post by MyrddinWyllt on 2008-02-08
The thing STILL isn't working, after a clean install and running through that walkthrough. It detects my router just peachy. The router has it listed as "associated" instead of "authorized" like the other wireless clients. I will post my wpa_supplicant.conf and interfaces file at some point, I have to get ssh working again and stuff to copy it and I'm tired. 

The only thing I really can think of is the fact that I have MAC filtering enabled on the router. The walkthrough you posted just above said to have MAC filtering disabled (I would try, but I need to write down the MAC addresses in our filter, can't remember if it clears them when you turn it off). Would that make a difference? I can't see how it would, but maybe there is some arcane weird thing that happens that I don't know about...

I will also post on that thread when I get a chance. Probably Sunday or Monday.

This is getting really, really irritating

---

### Post by ayenack on 2008-02-08
Thing is it is working because it connected it sees the router the router see it. It's bloody frustrating.

MAC filtering might make a difference. I remember I could not connect to a network once that had MAC filtering when it was turned off I could connect with WPA1 no probs so may well be part of the problem amybe all of it.

Don't forget that it's best not to have wired connected while trying to set-up/use wireless unless you set iptables to handle it which is impossible until you can actually set-up your wireless.

Let me know what happens on the other thread. If you solve it post what the problem was and how you get round it if you don't mind.

---

### Post by HebrewTheHammer on 2008-02-08
Wow

I belong to another forum that has to do with video games.

Many gamers use Linksys Routers as well.

I am not surprised to see they cause trouble in areas other than gaming. 


Easily put, linksys are crap...even if you do get it working, it'll stop and its not ubuntus fault.
I know you have no reason to listen to some on their first cup of ubuntu. but trust me your linksys is going to give you trouble for the rest of its existence. 

Ubuntu is renowned for being stable, your putting your stable OS on an unstable crutch. i would suggest getting another type of router.

I use a Encore router and have had no problems yet. i have a sort of network setup in my house i can share wirelessly with all my other devises through mediatomb.

---

### Post by MyrddinWyllt on 2008-02-08
> **HebrewTheHammer said:**
> Wow

I belong to another forum that has to do with video games.

Many gamers use Linksys Routers as well.

I am not surprised to see they cause trouble in areas other than gaming. 


Easily put, linksys are crap...even if you do get it working, it'll stop and its not ubuntus fault.
I know you have no reason to listen to some on their first cup of ubuntu. but trust me your linksys is going to give you trouble for the rest of its existence. 

Ubuntu is renowned for being stable, your putting your stable OS on an unstable crutch. i would suggest getting another type of router.

I use a Encore router and have had no problems yet. i have a sort of network setup in my house i can share wirelessly with all my other devises through mediatomb.

I'm not using a Linksys router. I wish I was, we have one that my sister swiped for her apartment, and managing it is 500x easier than the PoS Westell I'm using now. Some people have issues with Linksys, I've used a number of their products and have never had a problem. Likely the reason you hear so much about their problems is the percentage of households that use Linksys. We use two of them at work, and usually when there is an issue with our wireless connections it is either the fault of our servers, or PEBKAC.

I've also heard of massive amounts of problems with D-Link, Netgear, Motorola, every other major player in the market.

---

### Post by MyrddinWyllt on 2008-02-08
> **ayenack said:**
> Thing is it is working because it connected it sees the router the router see it. It's bloody frustrating.

MAC filtering might make a difference. I remember I could not connect to a network once that had MAC filtering when it was turned off I could connect with WPA1 no probs so may well be part of the problem amybe all of it.

Don't forget that it's best not to have wired connected while trying to set-up/use wireless unless you set iptables to handle it which is impossible until you can actually set-up your wireless.

Let me know what happens on the other thread. If you solve it post what the problem was and how you get round it if you don't mind.

I wish I could figure out why eth0 (my wired connection) insists on coming up even when there is no cable plugged in and no eth0 entries in my interfaces file.

I will try disabling MAC filtering and giving that a whirl, unfortunately if that is the problem I'm pretty boned, as I can't really leave it that way.

I will definitely post here again if I do or do not get a fix from the other thread.

Thanks for your help!

---

### Post by ayenack on 2008-02-08
> **MyrddinWyllt said:**
> 
I've also heard of massive amounts of problems with D-Link, Netgear, Motorola, every other major player in the market.

This is absolutely true. After all most manufacturers share the same chip-sets i.e. Ralink, Atheros, Prism, Realtek, Broadcom etc.

Hope you get it sorted MyrddinWyllt. I'll check back here and see what the score is. If I find out anything new or have any more ideas I'll post back here and PM you.

ayenack.

---

### Post by MyrddinWyllt on 2008-02-11
Good news and bad news.

Good news, my problems are definitely tied to the fact that I have MAC filtering enabled on the router. I disabled it and immediately got a connection.

Bad news. I don't think I can leave it disabled...I turned it off, found out I could get a connection, then re-enabled it.

Any idea if there is a way around this?

---

### Post by MyrddinWyllt on 2008-02-11
Okay...I turned MAC filterinf back on and restarting the computer, and I'll be damned but I am writing this message from my Ubuntu machine on the wireless network. I don't know what changed, but something did.

Hopefully this stays working...I've read a few things of intermittent problems with connection with MAC filtering on. Here's to nothing going wrong...

edit: Computer moved and successfully connecting in my room, where I intend it to stay. My guess is with MAC filtering disabled, it had no issue assigning an IP to that MAC address. When the filter was re-enabled, I restarted the computer and when it requested an IP, the router said, hey, I know you, you are this address, and re-assigned it. Meaning I probably will lose connection in 99 days when the lease expires. Oh well, worries for another day.

---

### Post by ayenack on 2008-02-12
YUHOOOOO great stuff. Shouldn't be like that but hay it works so that's bloody great. Mark as solved so all the other poor souls out there can maybe get some help from your experience. 

Well I've definitely learned something from this thread. Do the simple things first. It was the router not allowing the connection all along and once it established an connection without MAC filtering it obviously was able to keep the cards IP Address and allow it as a client afterwards. I think this is the same with Microsoft Windows as well come to think of it.

Well that's that done and dusted so I'll see you in the forums.

ayenack. ):P

EDIT: And keep the IP Address of course. Don't think you'll lose the connection it should be re-assigned automatically by the router. Begs the question of if this would work with server? LOL

---

### Post by MyrddinWyllt on 2008-02-12
> **ayenack said:**
> YUHOOOOO great stuff. Shouldn't be like that but hay it works so that's bloody great. Mark as solved so all the other poor souls out there can maybe get some help from your experience. 

Well I've definitely learned something from this thread. Do the simple things first. It was the router not allowing the connection all along and once it established an connection without MAC filtering it obviously was able to keep the cards IP Address and allow it as a client afterwards. I think this is the same with Microsoft Windows as well come to think of it.

Well that's that done and dusted so I'll see you in the forums.

ayenack. ):P

EDIT: And keep the IP Address of course. Don't think you'll lose the connection it should be re-assigned automatically by the router. Begs the question of if this would work with server? LOL


I had checked the settings on the router a hundred times...never thought to change a setting on the router though....its always just worked, and I've connected PSPs, Palms, OS X machines, Windows Machines, printers...at least its working now. Really wish I understood fully why it is so.

As for trying with Server...eh...ain't no way I'm touching any settings unless I have to on this thing. I'll just run some walkthroughs getting LAMP set up on Desktop, and figure out how to get it to boot to runlevel 3 (or just telinit there and leave it...)

I'll hopefully be around, I keep peeking at the beginner thread looking for ones I can solve, but those I can, someone is always faster :)

Thanks again for all your help

---

