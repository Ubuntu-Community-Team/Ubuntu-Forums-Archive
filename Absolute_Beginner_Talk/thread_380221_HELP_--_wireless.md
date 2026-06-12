---
title: "HELP -- wireless"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-03-09
I need to know if anyone can show me how to completely start over with my wireless access

I have a Linksys WMP54G v4 which is supposed to work with Ubuntu "out of the box"

I have a ASUS M2N4-SLI mobo with a AMD Athlon dual core

Maybe I need to completely start over with the wireless card, but I am clueless as to what to do

Any help at all would be really appreciated

Thank you in advance

---

### Post by Kobalt on 2007-03-09
Hello,

Could you please post the outputs of the following command lines (just enter them in a Terminal and copy/paste the result here) : 
```
lspci
iwconfig
```
That will give us the chipset of your card and maybe if it's already set up...

---

### Post by RanShak on 2007-03-09
I JUST had that problem and all I had to do was type in the name of the network.

Go to System > Administration > Networking

If you're getting a signal, a wireless connection should be in there. Click Properties and type in your connection name (and account/password if necessary).

---

### Post by jrandolph on 2007-03-09
jacob@jacob:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
05:00.0 VGA compatible controller: ATI Technologies Inc RV370 [ATI Sapphire X550 Silent]
05:00.1 Display controller: ATI Technologies Inc RV370 secondary [ATI Sapphire X550 Silent]
jacob@jacob:~$ 



jacob@jacob:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"wilcox lumber"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

jacob@jacob:~$

---

### Post by Kobalt on 2007-03-09
Is your wireless network SSID (name) this one : > wilcox lumber? 
Your card does seem to be working well, it is only a matter of settings. Right click on your network-ma,ager icon in the top right corner of your screen and enter "ra0" as the interface to monitor. Then click on configure and fill in you WEP key and SSID. 
That should get you on wireless ride :)

---

### Post by jrandolph on 2007-03-09
Ok -- first I think that is the name -- how would I find out what the name is supposed to be

Second -- I dont see a network monitor in the top right corner of my screen

Thank you so much for all this help 
Hopefully I can get this thing going

---

### Post by Kobalt on 2007-03-09
The name of your personal wireless network is something you have to set in your router configuration. If you don't see any network icon then lets add it : right-click in the notification area and select Add to the panel... Then scroll down to the System and Hardware section and double click on the network applet. And here you go :)

---

### Post by jrandolph on 2007-03-09
Ok then it is now up there -- and it says I have 90% connection.... BUT if I turn off the wired connection I have no internet whatsoever  

I dont know  I am lost

---

### Post by Kobalt on 2007-03-09
Relax jrandolph, you're getting closer and closer :)
If you see a signal jauge then your wirless card is ready to fly. What you need now is your SSID and WEP or WAP key. So, do you know how to access the configuration of your wireless network ? Did you set it up yourself ?
If you know these, as I wrote before, click on Configure and then fill your SSID and WEP/WAP key...

---

### Post by jrandolph on 2007-03-09
I did not set this up myself 

I am sure of the passphrase to login but I dont know if its WEP of WPA if that makes any difference 

And I dont for sure know what the SSID(name) is I think I have it right but I dont know if that makes any difference either

---

### Post by jrandolph on 2007-03-09
Kobalt

I have figured out -- The SSID is definately Wilcox Lumber
And it is WEP 
It has a passphrase and I know that too

---

### Post by Kobalt on 2007-03-09
Ok then if you know the passphrase and if you're sure it's Wep then follow this lead : click on your network icon, make sure the interface is *ra0* and then click Configure. Now make sure the Roaming mode is unckecked. Fill in your SSID and choose WEP key (Hexadecimal) for your passphrase, type it in the field bellow. 
Now, I suppose you will get connected through DHCP, which means the router provides you automatically with an IP adress so, click on Automatic Configuration (DHCP) in Connection settings, and finally validate. If it still does not connect you, enter these command lines one after an other : 
```
sudo ifdown ra0
sudo ifup ra0
```

I hope you'll get flyin' with this now :)

---

### Post by jrandolph on 2007-03-09
One problem with that -- It is a static IP address --which I also know

And when I try to change it to Hexidecimal and the go back to it -- it always changes back to plain (ASCII)


This is what comes back after those commands

jacob@jacob:~$ sudo ifdow ra0
Password:
sudo: ifdow: command not found
jacob@jacob:~$ sudo ifup ra0
ifup: interface ra0 already configured
jacob@jacob:~$

---

### Post by Kobalt on 2007-03-09
Oops sorry, my mistake : I mistyped the first command, it't ```
sudo idown ra0
```
If your IP is static then select that option and fill in the required fields then try the two commands...

---

### Post by jrandolph on 2007-03-09
This is what I get again


jacob@jacob:~$ sudo idown ra0
sudo: idown: command not found
jacob@jacob:~$ sudo ifup ra0
ifup: interface ra0 already configured
jacob@jacob:~$ 


When I have a passphrase and u tell me to set it to hexidecimal
should the passphrase be all numbers or should it be crazy stuff with colons and stuff

---

### Post by Kobalt on 2007-03-09
Come on, I can't type a damn simple command correctly! I'm really sorry, I mistyped it again (I'm actually in 10 hours jet lag so I'm kinda tired). Here is the correct command : ```
sudo ifdown ra0
sudo ifup ra0
```

A wep key in hexadecimal is made of these caracters only : 0 1 2 3 4 5 6 7 8 9 A B C D E F

If you have somthing else then it's a WPA key, and it's another story... but i'm sorry I won't be able to respond to you further more, I need to rest now :) 
I hope you'll get flyin' real soon ! Keep hope jrandolph, you're close. 

See ya !

---

### Post by jrandolph on 2007-03-09
After those commands I get this


jacob@jacob:~$ sudo ifdown ra0
Password:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Function not implemented.
jacob@jacob:~$ sudo ifup ra0
jacob@jacob:~$

---

### Post by jrandolph on 2007-03-10
Can anyone tell me what the problem is -- I feel like it should be working but I still dont have a connection with my wireless

---

### Post by Kobalt on 2007-03-10
hmm ... It does seem like your key is a WPA key. Unfortunately, edgy's built in drivers for this card doesn't support WPA encryption. 
You should visit [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500"), it's all about configuring and installing the card you have. That will help you out a lot. If you still have a problem, there is a link in this page to a thread on this forum about troublshooting for your card, you'll get plenty of apropriate help out there. 

Cheerio

---

### Post by jrandolph on 2007-03-10
The other computer that connects wirelessly to the network says its WEP

---

### Post by Kobalt on 2007-03-10
Could you please post the output (but don't forget to remove you SSID and WEP key if they appear) of you /etc/network/interfaces file : 
```
cat /etc/network/interfaces
```

---

### Post by jrandolph on 2007-03-10
jacob@jacob:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface ra0 inet static
        address 67.76.157.146
        netmask 255.255.255.0
        network 67.76.157.0
        broadcast 67.76.157.255
        gateway 67.76.157.129
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid 
        wireless-key1 s:
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 67.76.157.129
        wireless-key 

iface eth0 inet dhcp













auto ra0







auto eth0
jacob@jacob:~$

---

### Post by Kobalt on 2007-03-10
There is something strange in your config file : there are two lines for your wireless key. One starts like this
> wireless-key1 s:
And the other one is as follows 
> wireless-key
After which one is your WEP key ? 

Ultimately, there should be only one line for your wireless key, that should look like this
[quote]wireless-key YOUR-WIRELESS-KEY[/code]
So I suggest you remove the line *wireless-key1 s:* and place instead *wireless-key* beneath *wireless-essid* as I described above. Use this command to edit the file
```
gksudo gedit /etc/network/interfaces
```
Save & close, then try again those commands : 
```
sudo ifdown ra0
sudo ifup ra0
```

---

### Post by jrandolph on 2007-03-10
The first command came back like this

jacob@jacob:~$ sudo ifdown ra0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Function not implemented.

The second one did not do anything

jacob@jacob:~$ sudo ifup ra0
jacob@jacob:~$

---

### Post by Kobalt on 2007-03-10
Allright, let's try something else. First, let's make a backup of your existing config file 
```
sudo cp /etc/network/interfaces /etc/network/interfaces_bak
```
Then modify your file so that your ra0 section should look like this 
> iface ra0 inet static 
address 67.76.157.146
netmask 255.255.255.0
gateway 67.76.157.129
wireless-essid YOUR-ESSID
wireless-key YOUR-WEP-KEY
auto ra0
By the way, there is a ra0 line at the end of the file, erase it so that there aren't two of them. 
Then again, after save and close 
```
sudo ifdown ra0
sudo ifup ra0
```

---

### Post by jrandolph on 2007-03-10
jacob@jacob:~$ sudo ifdown ra0
jacob@jacob:~$ sudo ifup ra0
jacob@jacob:~$ 


I did that and copied and pasted your commands
and neither one of them came back with anything
allthough the second one seemed to think for just a min then thats all

---

### Post by Kobalt on 2007-03-10
At least you have no error message anymore... But I must say I really have no idea now on what could be not working... Have you checked your IP, Gateway, etc is correct ?

---

### Post by jrandolph on 2007-03-10
Kobalt -- U are amazing

It works   -- yipeee

:guitar: :)

---

### Post by Kobalt on 2007-03-10
> **jrandolph said:**
> Kobalt -- U are amazing

It works   -- yipeee

:guitar: :)

Victory ! :)

---

### Post by jrandolph on 2007-03-10
And it was all thanks to you

---

### Post by jrandolph on 2007-03-10
Now if I could just get this other program to run I would be happy as pigs in mud

---

### Post by Kobalt on 2007-03-10
What other program ?

---

### Post by jrandolph on 2007-03-10
TN5250 -- its a telnet emulator
I have installed it and I cant seem to get it to run

---

### Post by Kobalt on 2007-03-10
Well, I don't know much about that so I can't help you out anymore today I think :) I suggest you open a new thread, you'll get some ubunteros help...

Ciao

---

### Post by jrandolph on 2007-03-10
thanks so much 
later

---

