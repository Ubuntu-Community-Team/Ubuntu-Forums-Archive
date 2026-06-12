---
title: "PRO/Wireless 2200BG Wireless not working"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by unknown user on 2007-12-04
Hi guys,
I am a total new person to Linux (Ubuntu), but I have been thinking of moving from the evil (W) operating system for a long time now and finally taken the jump.  I must admit that I do like the look and feel of Ubuntu and on the whole, I am really happy.
However, and you know there was going to be one lol.  I have been having a right game with wireless and not being able to see any networks.
When I was running from the Live CD it was ON as my HP NC6220 with a PRO/Wireless 2200BG Wireless card had the Windows OS and driver on it and it worked fine.  However, when I installed Ubuntu and cleaned of Windows, the driver went too.  I was hoping that I could just install the driver and all would be sorted.  No that is not the case.  I have found something called “isw2200” I think, but it didn’t run like I am used to.  There was a few files, but no direction.
Can anyone help me out get my wireless work?  Please remember that I am totally new here and I have just about got to entering codes in the Terminal window.:confused:
Cheers,

---

### Post by skymera on 2007-12-04
ok is it pci or usb?

also what did you install the driver with?

---

### Post by unknown user on 2007-12-04
Hi there,
The card is a pci (built in one).  The light comes on with it all OK.
I have not installed any drivers with it to tell the truth as when I tried to install the one from the HP site the .exe I was told that Ubuntu does not support .exe files.
Cheers,

---

### Post by hyper_ch on 2007-12-04
open a terminal, run

```

lspci

```

and

```

ifconfig

```

and

```

iwconfig

```

and

```

cat /etc/network/interfaces

```

and post the result in here ;)

---

### Post by daengbo on 2007-12-04
I've seen the case too many times where the wireless button was off. Can you check that, as well?

---

### Post by unknown user on 2007-12-04
Thanks for this I will run the code when I get home and post the results.

I know it is down to the drivers for the card, but I do not know how to install them on Linux.

Lol yep the button is on and the nice blue wireless light is shining nice and bright.

---

### Post by quandary on 2007-12-04
Hi!

I'm also running Intel PRO/Wireless 2200BG. Mine works well.

However, after i compiled and installed Linux Kernel 2.6.23.1, it didn't work anymore.
I had to download, compile and install the latest drivers, and it worked well again. Perhaps you should try the same.

You can find the latest drivers & firmware at:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by hyper_ch on 2007-12-04
you did compile your own kernel?

---

### Post by unknown user on 2007-12-04
Hi there,

Thanks for the advice so far guys.  Hyper_ch I will run the code tonight and post the screens that I get.  However, I did run something like this last night and the interface screen was blank.  When you say “you did compile your own kernel?” I am going to show how new I am by sating that I have no idea what you mean here sorry.  

Quandary, this is the file that I have already downloaded onto the desktop, but I had no idea what to do with it from here as it didn’t open like the .exe files I have dealt with in the past.  I have since read that there is an instruction file on it and that I need to follow this.  However, I am not sure how to access this.  Any clues?:KS:lolflag:

Cheers,

---

### Post by paolo.c on 2007-12-04
> **quandary said:**
> Hi!

I'm also running Intel PRO/Wireless 2200BG. Mine works well.

However, after i compiled and installed Linux Kernel 2.6.23.1, it didn't work anymore.
I had to download, compile and install the latest drivers, and it worked well again. Perhaps you should try the same.

You can find the latest drivers & firmware at:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

Ok, I've installed Gutsy from a live Cd, and I need to update ipw2200 but how can I do after downloading  the new drivers? Look ... I'm an absolute beginner ... nothing with compiling a new kernel ...

---

### Post by hyper_ch on 2007-12-04
my last post was pointed at quandary... he said he did compile a kernel...

---

### Post by burn84 on 2007-12-04
Hi guys, sorry to butt in, but i dont want to start another thread. Having a similar problem, my PCI card is built in, same model PRO/Wireless 2200BG on my Acer Aspire 1680. 

The button usually blinks RED (searching for networks to connect) and stays RED once connected. This is usually how it works in Windows XP, I dont have it anymore, fully converted to Gutsy now. 

On Gutsy, it doesnt Blink or turn ON anymore and whenever I type "iwconfig" in Terminal, it comes up as Radio OFF, even after pressing the button n typing iwconfig AGAIN, still says OFF. It says its connected (Using WIFI RADAR) but it wont surf the net.

I tried several guides online, installing using NDISWRAPPER+WIndows .INF and it still doesnt work...any help?please....

---

### Post by unknown user on 2007-12-04
Hi Burn84,
Not a problem at all the more the merrier if you know what I mean.  This is what mine says too.

Here are the messages that i get back:

**_ lspci_**
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
10:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

**_ ifconfig_**
eth0      Link encap:Ethernet  HWaddr 00:14:C2:DD:19:74  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:c2ff:fedd:1974/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2255509 (2.1 MB)  TX bytes:307906 (300.6 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:15:00:3A:81:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x6000 Memory:d0400000-d0400fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**_ iwconfig_**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

*** cat /etc/network/interfaces***
auto lo
iface lo inet loopback

Hyper_ch I hope that this is of use to you.

---

### Post by hyper_ch on 2007-12-05
do you use WPA on your network and do you understand German? If so, I've found this:

[http://wiki.ubuntu-forum.de/index.php/Intel%C2%AE_PRO/Wireless_2200BG](http://wiki.ubuntu-forum.de/index.php/Intel%C2%AE_PRO/Wireless_2200BG)

If you don't understand German, I can translate it (or try to) but I'll need some time.

---

### Post by GSF1200S on 2007-12-05
> **burn84 said:**
> Hi guys, sorry to butt in, but i dont want to start another thread. Having a similar problem, my PCI card is built in, same model PRO/Wireless 2200BG on my Acer Aspire 1680. 

The button usually blinks RED (searching for networks to connect) and stays RED once connected. This is usually how it works in Windows XP, I dont have it anymore, fully converted to Gutsy now. 

On Gutsy, it doesnt Blink or turn ON anymore and whenever I type "iwconfig" in Terminal, it comes up as Radio OFF, even after pressing the button n typing iwconfig AGAIN, still says OFF. It says its connected (Using WIFI RADAR) but it wont surf the net.

I tried several guides online, installing using NDISWRAPPER+WIndows .INF and it still doesnt work...any help?please....

Please look at the results of:

```
iwlist scanning
``` (Can you post these results as well please?)

Whichever result says "no scan results" take note of the interface (ath0, eth0, etc...)

Now, plug that in to the following command- we'll say your wireless interface is ath0...

```
sudo ifdown ath0
```
and then
```
sudo ifup ath0
```

Tell us what it says...

**EDIT** Unknown User.. try this as well and give us the results.. Im not sure if it will help, but it seems as if the card isnt broadcasting. Ive never had this problem, but its interesting to note that the switch for my wireless card doesnt work in Linux. I can still use the wireless card with the switch in the off position, and im wondering if you may be able to do the same- it may just need the interface itself up'd first. Once you guys try the last two commands, check iwlist scanning again and see if it shows any results..

---

### Post by unknown user on 2007-12-05
hyper_ch cheers for this you are a star, if you could turn into English that would be great.
GSF1200S I sure will do this tonight when I get home and post the replies.
Does anyone know what I need to do to install the isw2200 drivers for the PRO/Wireless 2200BG card as I have this sat on my hard drive, but not done anything with it.  Lol with any instructions on this, just remember that I am a windows runaway.

---

### Post by GSF1200S on 2007-12-05
> **unknown user said:**
> hyper_ch cheers for this you are a star, if you could turn into English that would be great.
GSF1200S I sure will do this tonight when I get home and post the replies.
Does anyone know what I need to do to install the isw2200 drivers for the PRO/Wireless 2200BG card as I have this sat on my hard drive, but not done anything with it.  Lol with any instructions on this, just remember that I am a windows runaway.

I think Ubuntu should support this card out of the box.. its a pretty common card. Dont take my word for it, my two lappies use an Atheros card and a Broadcom (PITA in Linux BTW). Well see what the terminal spits out.. If nothing else, it should help Hyper_ch if it doesnt help me...

---

### Post by hyper_ch on 2007-12-05
Actually:

> 
eth1 radio off ESSID:"" 


Did you activate the wifi in your network manager?
And are you going to use WPA? If not, I don't know if the German guide would be of any use.

---

### Post by GSF1200S on 2007-12-05
> **hyper_ch said:**
> Actually:



Did you activate the wifi in your network manager?
And are you going to use WPA? If not, I don't know if the German guide would be of any use.
Good call.. Just plug in eth1 to those commands and post the results. In your case eth1 is the interface. The other poster may have a different interface.  Ensure that wifi is activated as hyper_ch said, and if it is, try the other commands... thanks hyper, dont know why I missed that one...

---

### Post by hyper_ch on 2007-12-05
I missed it also the first time I read through it ;)

---

### Post by unknown user on 2007-12-05
hyper_ch - I am sure that I have activated the wifi in the network manager, but will check again later just to make sure.
It sure is WPA that I am running :KS

---

### Post by hyper_ch on 2007-12-05
> **unknown user said:**
> It sure is WPA that I am running :KS
Why sure? I run, for protecting myself, no encryption at all on my wifi ;)

---

### Post by unknown user on 2007-12-05
Sorry wrong use of words, yep I am using WPA and Wifi is enabled.

---

### Post by burn84 on 2007-12-05
GSF1200S:

Hey dude thanks for replying. Here is what comes up in terminal:

burn@Burn:~$ iwlist scanning
^[[3~lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      No scan results

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

burn@Burn:~$ sudo ifdown eth0
[sudo] password for burn:
ifdown: interface eth0 not configured
burn@Burn:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
burn@Burn:~$

---

### Post by unknown user on 2007-12-05
Hi there,
We must have the same laptops in a former life lol as mine says this:

*** iwlist scanning***
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

*** sudo ifdown ath0***
[sudo] password for unknown:
ifdown: interface ath0 not configured

 sudo ifup ath0
[/B][/I][/B]Ignoring unknown interface ath0=ath0.

---

### Post by unknown user on 2007-12-05
Oh I forgot to say that when I press the wireless button on the Bluetooth icon comes up and I can search for devices all ok.  Thought this may help.

---

### Post by quandary on 2007-12-05
> **hyper_ch said:**
> 
my last post was pointed at quandary... he said he did compile a kernel...


yes i did. took me something in between 1.5 to 2.5 hours...

For how to install the drivers:
[http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL)


to compile and install driver & firmware:
Download: 
Latest wireless tools:
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/wireless_tools.29.tar.gz](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/wireless_tools.29.tar.gz)
Drivers:
[http://sourceforge.net/project/downloading.php?groupname=ipw2200&filename=ipw2200-1.2.2.tgz&use_mirror=kent](http://sourceforge.net/project/downloading.php?groupname=ipw2200&filename=ipw2200-1.2.2.tgz&use_mirror=kent)
Firmware image:
[http://ipw2200.sourceforge.net/firmware.php?fid=7](http://ipw2200.sourceforge.net/firmware.php?fid=7)

For howto install & compile follow the instructions in the install or readme files. To open them:
On console type: 
sudo gedit /path/to/your/directory/readme

---

### Post by GSF1200S on 2007-12-05
> **unknown user said:**
> Hi there,
We must have the same laptops in a former life lol as mine says this:

*** iwlist scanning***
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

*** sudo ifdown ath0***
[sudo] password for unknown:
ifdown: interface ath0 not configured

 sudo ifup ath0
[/B][/I][/B]Ignoring unknown interface ath0=ath0.


You have to plug in the wireless interface, not use the one I used as an example. In your case:

sudo ifdown eth1
sudo ifup eth1

And tell us what 

iwlist scanning

says following those two commands...

---

### Post by unknown user on 2007-12-06
Not too sure what you mean when you say "You have to plug in the wireless interface".  I take it you do not mean physically plug it in?

---

### Post by unknown user on 2007-12-06
I done the line that you said "sudo ifdown eth1" and the reply after entering my password was eth1 not configured

iwlist scanning
lo    Interface doesn't support scanning.
eth0  Interface doesn't support scanning
eth1  No scan results

Guys any ideas what I do here as I have no idea.

---

### Post by Whiffle on 2007-12-06
do

"sudo lsmod | grep ipw2200"

sounds like the module isn't loaded

---

### Post by unknown user on 2007-12-07
Whiffle - I sure will do this when when I get home tonight and let you know what the outcome of it is.  Really hope that it works as I would love to use Ubuntu for good and move away from the devils OS.

I was having a look around my system and I noticed that I have the isw2200 driver on my system in the SYS folder I think it was.  So now I am thinking that it came with the Ubuntu build, but I need to activate it in some way.  That is why I read your reply with great interest.

Cheers,:):)

---

### Post by hyper_ch on 2007-12-07
The translation of that wiki entry in German. Its aimed at Feisty Fawn (but it should also work on gutsy I think):

Check if you have the Wireless 2200BG card:
```

lspci | grep 'Wireless 2200BG'

```
Something like this should appear:
```

02:0d.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

The card should run out of the box, so the following command should return the following output:
```

dmesg | grep ipw2200

```
Output:
```

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
ipw2200: Copyright(c) 2003-2006 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Radio Frequency Kill Switch is On:
ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels) 

```

In order to use WPA you'll have to install the wpa_supplicant package:
```

sudo apt-get install wpa_supplicant

```

The network managers provided by gnome/kde are sometimes troublesome. So deinstall them:
```

sudo apt-get remove --purge network-manager knetworkmanager

```

No check on what interface the wifi card listens. It varies from system to system:

```

sudo iwconfig

```
That should return something like this:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
         Mode:Managed  Channel=0  Access Point: Not-Associated
         Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
         Retry limit:7   RTS thr:off   Fragment thr:off
         Encryption key:off
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
In this case the interface is:  eth1

Check if you have your wireless access point in range:
```

sudo iwlist eth1 scan

```
This returns something like that:
```

eth1      Scan completed :
         Cell 01 - Address: 00:01:02:03:04:05
                   ESSID:"Zimmer"
                   Protocol:IEEE 802.11bg
                   Mode:Master
                   Channel:6
                   Encryption key:on
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                             11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                             36 Mb/s; 48 Mb/s; 54 Mb/s
                   Quality=37/100  Signal level=-78 dBm
                   IE: WPA Version 1
                       Group Cipher : TKIP
                       Pairwise Ciphers (1) : TKIP
                       Authentication Suites (1) : PSK
                   Extra: Last beacon: 156ms ago

```
If you don't get any output similar to that, then you'll have to check whether you're too far away or whether the router is running or or or or....
The line below "Quality" returns the the encryption details.

Now you set the basic network settings. You'llhave to decide if you want a static or dynamic IP [personal note from hyper_ch: I prefer static devices - it makes it easier to access....]
Depending on what you chose you'll have to differently setup your network settings.

Edit with your interfaces file
```

gksu gedit /etc/network/interfaces

```
Or with a command line based editor:
```

sudo nano /etc/network/interfaces

```

If you use a static IP make the settings similar to this:
```

auto eth1
iface eth1 inet static
address 192.168.178.11
netmask 255.255.255.0
network 192.168.178.0
broadcast 192.168.178.255
gateway 192.168.178.1

```
The address is that static IP that you give yourself. I presonally use 10.0.0.x for my network. Most often (as far as I've seen) the default is 192.168.0.x. You'll have to know what your address is.
Change the address, network, broadcast and gateway accordingly. Netmask is usually 255.255.255.0.

For a dynamic IP address enter this into the interfaces file:
```

auto eth1
iface eth1 inet dhcp

```

To circumvent unnecessary waiting time, comment all lines, except the ones posted above and the 2 following lines:
```

auto lo
iface lo inet loopback

```
You comment them by adding a # at the beginning of the line.

If you use a static IP you'll also have to set nameservers:

Edit the file /etc/resolv.conf and add a line like this:
```

nameserver 192.168.178.1

```
Of course if your router has a different IP address, change it accordingly. (Mine is nameserver 10.0.0.1).

Restart the network:
```

sudo /etc/init.d/networking restart

```

The basic network-settings are done yet, now it's time for the wpa_supplicant conf.

Edit the /etc/wpa_supplicant.conf and use the following settings:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1
network={
ssid="zimmer"
scan_ssid=1
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
#psk="test1234"
psk=e409a4206c4d6118231f2611f6c0607d21a069401349e49b2a1523dc85e90e24
}

```
It's important, taht the line starting with ssid is set correctly. The ESSID can be shown by issuing the command 'sudo iwlist eth1 scan' - if the ESSID is broadcastet at all. If it's not broadcastet, cahnge the line ap_scan= and set the value to '2' instead of '1'.
The psk line can be generated with the following command:
```

sudo wpa_passphrase 'YOUR_ESSID' 'YOUR_WPA_PASSWORT_IN_PLAINTEXT' 

```

-->
```

network={
       ssid="zimmer"
       #psk="test1234"
       psk=e409a4206c4d6118231f2611f6c0607d21a069401349e49b2a1523dc85e90e24
}

```
For more information consult the wpa_supplicant documentation.

Now you can test if wpa_supplicant can connect. Issue this command:
```

sudo wpa_supplicant -Dwext -ieth1 -c /etc/wpa_supplicant.conf -w

```

You should now get this output:
```

Trying to associate with 00:02:03:04:05:06 (SSID='zimmer' freq=0 MHz)
Associated with 00:02:03:04:05:06
WPA: Key negotiation completed with 00:02:03:04:05:06 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:02:03:04:05:06 completed (auth) [id=0 id_str=]

```

If that works, you're connected.

Check now your internet connection:
```

ping www.heise.de

```
And if you get this output:
```

PING www.heise.de (193.99.144.85) 56(84) bytes of data.
64 bytes from www.heise.de (193.99.144.85): icmp_seq=1 ttl=246 time=25.0 ms
64 bytes from www.heise.de (193.99.144.85): icmp_seq=2 ttl=246 time=25.1 ms
64 bytes from www.heise.de (193.99.144.85): icmp_seq=3 ttl=246 time=25.0 ms
64 bytes from www.heise.de (193.99.144.85): icmp_seq=4 ttl=246 time=25.0 ms

--- www.heise.de ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 25.052/25.083/25.133/0.161 ms

```
It works. Stop the pinging with  ctrl+c.

If that all works, the last step is to autostart wpa_supplicant.
Edit the file '/etc/network/interfaces' and add below the iface eth1 ..... line the wpa-conf line. It should look like this (on a static ip):
```

iface eth1 inet static
wpa-conf /etc/wpa_supplicant.conf

```

Reboot your computer and check if it works.

If you have issues post the output of these commands in the forum:

sudo ifconfig

sudo iwconfig

sudo iwlist scan

cat /etc/network/interfaces

cat /etc/resolv.conf

cat /etc/wpa_supplicant.conf

sudo route

---

### Post by unknown user on 2007-12-07
If anyone is having this issue have a look at this site as I found it to be good

[http://forums.suselinuxsupport.de/lofiversion/index.php/t46299.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t46299.html)

I went into the Bios and then set it back to default settings

---

### Post by unknown user on 2007-12-08
Guys, I would like to thank you all for your help regarding this and the time that you spent helping me.  I am so glag that I have now got my wireless working and I can complete this update from the laptop in question whilst sat in my front room :):)

Hyper_ch I will still run the lines that you said to see what I get.  Last night before I reset the Bios, I run the codes that you listed abouve and I was getting different results from what you posted, so this time I will run them again and see what I get back, will post it on the results.

---

### Post by unknown user on 2007-12-08
I did notice something though after I done the reset, the screen settings and Bluetooth has stopped working.  It will not search for any devises and now the bluetooth icon has gone missing from the top of the screen.

Any ideas guys?

---

### Post by quandary on 2007-12-21
just install the latest drivers, and don't play around your config files when you don't know what you're doing, for heaven's sake !

---

