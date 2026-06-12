---
title: "Another Intel Pro/Wireless 3945abg Question..."
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Beazel on 2007-04-14
Hi there folks,

    I've just completed a rather painless Ubuntu install (easier than Windows anyday) but I'm gonna have to ask your advice on getting my Intel Pro/Wireless 3945abg working.  I think the card's recognised but I'm not sure how to set up the network.  I don't even know where to start!  Everything else seems great, I've done a dual boot system (windows still works!) and Ubuntu starts and runs like a rocket.  Great job all you developer types.

Many thanks in advance,
Beaz
(currently wandering the "How To" section)

---

### Post by Rospo Zoppo on 2007-04-14
Read this [http://ipw3945.sourceforge.net/INSTALL]("http://ipw3945.sourceforge.net/INSTALL")... If yuo have problem post here, I have same card :D

---

### Post by Beazel on 2007-04-14
Cheers, I'm on it now.  That was some lightning reply!

---

### Post by chili555 on 2007-04-14
With respect to my esteemed colleague Zoppo, I don't think you have to go through all that. With linux-restricted-modules installed, your ipw3945 should be recognized and set up through System-Administration-Networking.

Mine, the one I am posting this reply with, certainly is!

---

### Post by Beazel on 2007-04-14
Not sure about anything when I'm in Linux...  lol.
It's a bit like landing in another country and not speaking the language...  I 'think' the card's been recognised, i've seen it's name and ID stuff scroll past when I booted, but the networking program is all greek to me.  Could anyone tell me the first steps I need to take?  I'm new to linux but an old hand at computers in general (Remember the Vic 20? or am I showing my age?).  Any prodding in the right direction is more than welcome!

Cheers
Beaz

---

### Post by Bachstelze on 2007-04-14
It depends on which kernel version he's running. Some Ubuntu kernels have that driver but surprisingly, some don't.

Beazel, the first step to see if your crd is recognized is to do

```
sudo iwconfig
```

If you see something that doesn't say "No wireless extensions", you're there.

---

### Post by Rospo Zoppo on 2007-04-14
Yeah you're all right but a lot of people have to do that steps to have their wireless work, so I thought he was one of them :D

---

### Post by Beazel on 2007-04-14
Funilly enough, as you replied I was just trying that out!  yukyukyuk.

I got this:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1856   Missed beacon:0

That's a bad thing right?!
I can't figure out what the Kernel version is (the only way I know is to Restart and read things) but if it's any help I only D/L'd Ubuntu the day before yesterday...

Can I also say thanks for all your help so far?

---

### Post by mikewhatever on 2007-04-14
Can you also post the output of these
> uname -r
lshw -C network
Some report this card worked out of the box, your case seems to be similar to that of mine and others. The card is recognized and the driver loaded, but no sign of connection. Linix restricted would be a solution.

---

### Post by wjp.reg on 2007-04-14
to see the kernel version enter 

```
uname -r
```

in a terminal

---

### Post by Beazel on 2007-04-14
ok, here goes...

uname -r
2.6.17-11-generic

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:ce:4a:57
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 multicast=yes wireless=unassociated
       resources: iomemory:da000000-da000fff irq:185
  *-network
       description: Ethernet interface
       product: Intel(R) PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:61:ab:3a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 ip=192.168.1.5 multicast=yes
       resources: iomemory:dc005000-dc005fff ioport:4000-403f irq:50

Is that right?

---

### Post by chili555 on 2007-04-14
What you have there is a good thing! The drivers are in place and your wireless interface is ready to be commanded to connect! I would do:```
iwlist eth1 scan
```That will tell you the ESSID of the access point you want to connect to. Here's an example:```
chili@LAPTOP60:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 99:13:19:62:8D:F7
                    ESSID:"myrouter1"
etc. etc.

```Then tell your computer you wish to connect:```
sudo iwconfig eth1 essid myrouter1
sudo dhclient eth1
```

In 90% of all cases, if you do not have encryption, WEP, WPA, etc., you will connect.

PS- I notice your wired ethernet is connected and has an IP address. To connect wirelessly, do:```
sudo ifdown eth0
```and disconnect the wire. Then take the steps I've outlined above.

---

### Post by Beazel on 2007-04-14
Here we are:
*eth1      No scan results*

er...  I'm pretty sure THAT's bad...  lol

Answers on a postcard to the following address...

---

### Post by compmodder26 on 2007-04-14
I have the same card and I've always had the best luck if I use network-manager.  It can be downloaded from the repositories.  Just search for it in synaptic.  You'll also want to install network-manager-gnome (again in the repositories).   Once installed, type "nm-applet" in a terminal.  You should see a new icon in your gnome panel notification area. 

Right click the new icon and you should see something referencing wireless networking.  If you don't, then you need to edit your /etc/network/interfaces file (gksudo gedit /etc/network/interfaces) and comment out (place a "#" in front) everything other than the loopback section (lo).  Save your changes and try a restart and see if network-manager can work with your wireless card now.

---

### Post by chili555 on 2007-04-14
This is from ipw3945 documentation:> The wireless tools default to only waiting 2 seconds between requesting
a scan and reporting the scan results.  In some hardware configurations,
two seconds is not long enough to rotate through all of the available
channels looking for valid networks.  As such, you may find better 
results by running iwlist scan once, then waiting a few seconds and 
running it again.Wait a few soconds and run again. It might take 3-4 tries. Please prefix the command with sudo.

I have seen nothing bad in your setup so far!

---

### Post by Beazel on 2007-04-14
Badda Bing!  Got this:

eth1      Scan completed :
          Cell 01 - Address: 00:16:E3:1F:60:C7
                    ESSID:"BTVOYAGER2091-C7"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-31 dBm  Noise level=-31 dBm
                    Extra: Last beacon: 216ms ago
          Cell 02 - Address: 00:18:4D:AF:E9:92
                    ESSID:"SKY92874"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=30/100  Signal level=-91 dBm  Noise level=-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 244ms ago

Any good?  Thanks for getting me this far, I can only imagine what it's like at your end...  Are you shouting at the screen?  lol

---

### Post by Beazel on 2007-04-14
ok,  getting there I think...

Started going through the steps above and got this:

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:de:ce:4a:57
Sending on   LPF/eth1/00:18:de:ce:4a:57
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 
beazel@beazel-laptop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 7665
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:a0:d1:61:ab:3a
Sending on   LPF/eth0/00:a0:d1:61:ab:3a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67

I've had a look in system-administration-networking but nothing's lighting up...
My fault I guess, but I'm not sure what's to do next.  am I clashing with anything?  I'm using the ethernet port to type this...

---

### Post by chili555 on 2007-04-14
We're doing well so far! May I assume we are connecting to BTVOYAGER2091-C7? Notice it says 'Encryption key On'? Is this WEP, WPA or Romulan? You might go into the router's administration pages and check, and re-check the key. Then you can add to your list of commands:```
sudo iwconfig eth1 essid BTVOYAGER2091-C7
sudo iwconfig eth1 key 0123456789
sudo dhclient eth1
```This works well if you are using WEP. If you are using WPA, it might be a lot easier to use NetworkManager as suggested above.

Don't forget to ifdown eth0 and disconnect the wire first.

---

### Post by Beazel on 2007-04-14
Now, we've reached a problem...

The wireless still doesn't want to play ball and the ethernet has decided to stop working too.  (I'm typing this on my other computer...)  I've absolutely no idea what to do now!  Please help...  I don't want to have to go back to Windows!

---

### Post by chili555 on 2007-04-14
Sometimes, networking needs a boot in the seat of the pants:```
sudo /etc/init.d/networking restart
```If you have the wire connected, it should hook up.

---

### Post by Beazel on 2007-04-14
Sorry good Sir, doesn't want to do it by the looks of things...  I can't post the output here due to the lack of connection but it says No Such Device quite a lot...

Is it worth a full re install?  A bit heavy handed but it'd work...

---

### Post by Beazel on 2007-04-14
Rock and roll, got the ethernet back on, I'll have a play around with the settings for a bit, but I'm not sure what I'm looking for.  You've all been a great help, I now know how to switch the connections and I've learnt my first few commands.  Nice one, as we say in London.

Cheers,
Beaz

---

### Post by chili555 on 2007-04-14
A full re-install is not...yet...indicated. You haven't mucked up a few dozen configuration files...yet...that a re-install would wipe clean.

In preparation for any and every network interface that may be used, Ubuntu sets up 'placeholder' interfaces for wlan0, ath0, eth2, etc., etc. When you restart networking, or start it while booting, for that matter, a lot of churning goes on while networking looks for and can't find all the non-existant interfaces.

Have you got the exact encryption key from the router? WEP or WPA?

---

### Post by Beazel on 2007-04-14
Yuk yuk yuk, my first reaction to ANYTHING that doesn't work is "Re-install it".  Not needed, I'm back to where I was now.  Had a good look around and a check of a few things and I'm trying again...

The exact encryption key for the router is proving difficult to find/work out due to my lack of ability in linux.  I'm pretty sure it's WPA.  Is that the "Stronger" one of the two?  I can't recall off the top of my head...  Whichever the stronger encryption is, it's set up for that one.

Wish me luck...

---

### Post by Bachstelze on 2007-04-14
Yep, between WEP and WPA, WPA is the "stronger one".

---

### Post by chili555 on 2007-04-14
Why don't we go ahead and clean up our interfaces file. ```
sudo gedit /etc/network/interfaces
```You know you are not going to substitute some crummy USB wireless dongle for your great ipw3945, and you know you have and use your wired ethernet, so delete everything in the file that **isn't** lo, eth0 or eth1. Save the file and close gedit.

Here is my interfaces file, for example. Some details have been obscured for security, but you get the concept:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid myrouter1
wireless-key 096cxxxyyyzzze4afe
```I never use my wired ethernet, so 'auto eth0' is removed here, but until you get your wireless going, you should not remove that line. This interfaces file is fine for WEP encryption, but not WPA.

---

### Post by Beazel on 2007-04-14
I'm looking at this now,

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


Looks a bit too simple to me or is that cos I'm used to the masses of rubbish windows gives me?

---

### Post by chili555 on 2007-04-14
Looks perfect! I would leave eth0 as 'auto' for now. Add:```
auto eth0
``` above the eth0 lines. Save and close.

Any news on the encryption front? Can you get to the router's administration page? Probably [http://192.168.1.1;](http://192.168.1.1;) then look in wireless security and these details will be apparent.

---

### Post by Beazel on 2007-04-14
I'm guessing I can't get any further without the encryption.  I've got something that's mystically labelled "network key" but it looks too short.  The voyager homepage has been asking for passwords and not accepting them.  Assuming the network key is the right thing, what's the next step?

Cheers
Beaz

---

### Post by chili555 on 2007-04-14
Well, it's hard to know for sure, but let's start some detective work:
# 40-or 64-bit ASCII WEP code has five characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters 

So, does your 'network key' have 5, 10, 13 or 26 characters? If so, it's probably WEP. If not, it's probably WPA. I tend to believe it's WEP, since your scan was silent as to type, yet your neighbor, SKY92874, shows explicitly as WPA.

If your key has 5 or 13 characters, it's ASCII, add the prefix s: to your key. Add to your commands:```
sudo iwconfig eth1 key s:<your_ascii_key>
```If it has 10 or 26 characters, it's hex, so no prefix is needed:```
sudo iwconfig eth1 key <your_hex_key>
```

I would do all the commands in order: essid, key, dhclient, as outlined above. Don't forget to ifdown eth0 and disconnect the wire first.

---

### Post by Beazel on 2007-04-14
It works!  Histerical laughter at this end...  I had to re boot and try it a few times but it's on now.

When I boot up linux do I have to do the terminal stuff every time I want to get on the net?  I'm guessing there's a way to save it but it's beyond me...

I can't tell you how greatful I am...
MANY thanks!
Beaz

---

### Post by chili555 on 2007-04-14
Just *sudo gedit /etc/network/interfaces* to put your specifics in place:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid whatever1
wireless-key 096cwhateverafe
```If you are going to connect wirelessly, typically, you can remove *auto eth0* now; make sure *auto eth1* is in place. Should connect wirelessly on boot.

Good luck!

---

### Post by znoxx on 2007-04-14
Been struggling with this for 12 hours myself, im thiiiiis close to just format the ubuntu drive and go back to my windows and pretend i didnt waste _12_ hours of my life for nothing.. yes im a little pisst.. :/

It identifies the wireless card, i can see my network, but it refuses to connect at all cost.. tried all of the steps on the last pages and still it keeps me off le net..

one thing i noticed though is when i try:
```

sudo iwconfig eth1 key mykey

```

i get:
```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "mykey".

```

the scan and everything works except i cant connect. Where do u turn on WPA etc?

*counts to 20 once again* xD

EDIT: i got the same setup i think as the threadstarter

---

### Post by chili555 on 2007-04-14
Well, certainly "mykey" is not a hex key. It could be ASCII. Please try```
sudo iwconfig eth1 key s:mykey
```It may be WPA, in which case, you might look here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

You don't know which you set up in the router? Does ```
sudo iwlist eth1 scan
```tell you?

---

### Post by Ripfox on 2007-04-14
Can't he just use wicd to connect?

---

### Post by znoxx on 2007-04-14
Some info ;)

uname -r
```

2.6.17-11-generic
```

lshw -C network
```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:65:a7:4c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 multicast=yes wireless=unassociated
       resources: iomemory:8a000000-8a000fff irq:185
  *-usb
       description: Bluetooth wireless interface
       product: HP Integrated Module
       vendor: Broadcom Corp
       physical id: 1
       bus info: usb@4:1
       version: 1.00
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network
       description: Ethernet interface
       product: Intel(R) PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:34:3f:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 ip=192.168.0.130 multicast=yes
       resources: iomemory:d2006000-d2006fff ioport:3000-303f irq:74

```

sudo iwlist eth1 scan
```

eth1      Scan completed :
          Cell 01 - Address: 00:17:9A:6A:66:6B
                    ESSID:"LuringLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-88 dBm  Noise level=-88 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 2448ms ago
```

sudo iwconfig eth1 essid myrouter1
sudo dhclient eth1
```
There is already a pid file /var/run/dhclient.pid with pid 5832
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:65:a7:4c
Sending on   LPF/eth1/00:13:02:65:a7:4c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

sudo gedit /etc/network/interfaces
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1 inet dhcp
wireless-essid LuringLAN
wireless-key mykey
```

---

### Post by znoxx on 2007-04-14
> **chili555 said:**
> Well, certainly "mykey" is not a hex key. It could be ASCII. Please try```
sudo iwconfig eth1 key s:mykey
```

tried that aswell, still wont connect :/

100% sure i have wpa turned on though :) so do i have to follow that link u provided then?

Tried the WPA thingy aswell now, still keeps on returning No DHCPOFFERS received. Also restarted the network, gonna try to restart ubuntu now ;p

---

### Post by chili555 on 2007-04-14
> 100% sure i have wpa turned onMe, too!```
scan completed :
          Cell 01 - Address: 00:17:9A:6A:66:6B
                    ESSID:"LuringLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-88 dBm  Noise level=-88 dBm
                    IE: **WPA** Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 2448ms ago
```

As a previous poster suggested, often Wicd will simplify all this: [http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/) Try Wicd first.

---

