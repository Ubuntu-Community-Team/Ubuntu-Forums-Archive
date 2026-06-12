---
title: "Airport Extreme Connection, iBook G4...please help!"
date: 2007-05-26
forum: Apple PPC Users
---

### Post by TonySmash on 2007-05-26
I've spent the last 5 hours trying to make this work, and I'm about ready to just go back to OSX, but I'm determined to give Ubuntu a try. I'm trying to make my Airport Extreme Card (Broadcom BCM4306) connect to my Linksys WRT54G Router. No WEP protection, very simple, but I can't make it work. So here's what I can figure so far:

I first tried the fwcutter method, which worked, somewhat. It allows Ubuntu to recognize the AE card and transfer data at 11mbps, which is nice, but not what I need. My router is G-only (54mbps) not B-compatible (or so I believe). So while fwcutter worked fine in that it made it so that the system could recognize the card and use the card, I still can't connect to the router because the card is broadcasting at B-only and the router is G-only. Right? So then...

I tried the ndiswrapper method. I did everything exactly as I was told to ([Ubuntu Docs - Broadcom / ndiswrapper stuff]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?action=show")), even starting with a clean feisty install. It all went smoothly until I tried doing Step 5 in that article - extract and install ndiswrapper using make. When I did user@ubuntu:~/ndiswrapper-1.28$ make , i got an error saying it couldnt install it. From what I've gathered in my hours of hunting and reading, this is because ndiswrapper doesnt work on PPC, only x86. Well.....crap.

So, to recap, I need to have the airport extreme card inside my iBook work at 54mbps, G, and not just 11mbps, B. However, I can't make this work using the fwcutter method, and the ndiswrapper method gets all bungled up every time I try it. So please, someone, anyone.....help me?

---

### Post by stmiller on 2007-05-26
ndiswrapper does not work on PPC Linux, as I guess you found out. It emulates a windows driver, and needs x86 hardware. Uninstall ndiswrapper. See the PPCFAQs below to get wifi going with PPC.

---

### Post by TonySmash on 2007-05-27
stmiller-

i went to the ppcfaq's and did what was instructed under "will my wireless work?"; i did the "sudo apt-get install bcm43xx-fwcutter" command and got this error message:

E: Couldn't find package bcm43xx-fwcutter

now i'm worried. after posting my original message i again did a clean install of feisty just to make sure i wouldnt have any problems, and suddenly there's this new error when the bcm43xx stuff is supposed to be built in to feisty. is there another way to install this package that doesn't involve terminal? like using synaptic? keep in mind i'm brand new to linux, and while i'm starting to follow along, i could use some *gentle* guidance. thanks for your help though! the ppc faq is extremely useful.

---

### Post by stmiller on 2007-05-27
You have to enable all feisty repositories. 
Applications>Add/Remove>Preference button at bottom

Then make sure all 4 top options for 'Ubuntu Software' are checked.

--------
Broadcom support IS built in to Feisty. If you do a lsmod from a clean install you will see the driver running. 
The problem is the non-open source license around the firmware of the driver. Ubuntu Linux cannot legally include this firmware. So doing that 'sudo apt-get install bcm43xx-fwcutter' fetches the firmware for the driver.

---

### Post by TonySmash on 2007-05-27
stmiller-

okay, went through the add/remove programs panel, did all the stuff you said, did sudo apt-get install bcm43xx-fwcutter, rebooted aaaaand......i'm right back where i started. yes, feisty has detected and is running the airport extreme card. yes, i can see my home wifi network when i click on the network icon. BUT.....i still can't connect, and from what i gather, its because feisty is using wireless-B and my network is G-only. so we're back to my original problem....how do i make feisty use the G aspect of my airport card?

thanks for your continued help!

---

### Post by tcrroadie on 2007-05-27
Hi TonySmash,

I feel your pain and confusion as to why the broadcom wireless card in our ibooks does not like to work with wireless G networks.  My ibook will also not connect to my Linksys WAP54G if it is configured for wireless G networks only.  But my ibook works perfect when my WAP54G is configured to use B&G networks.  

Your Linksys WRT54G does support B as well as G network standards.  you may need to log onto your router to enable wireless B support.  I looked up the user guide for you found at Linksys's website.  See the link below to view your routers user guide online.

[Linksys WRT54G User Guide]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0034939789B01")

Configure your router for a mixed network (B&G).  That should get you going.  Wireless encryption will also work on your ibook.  I just use WEP on my network since it is easy to configure and suits my needs just fine for my location.  

To see the status of your wirelesss network using your ibook, run this command in a terminal.
```

iwconfig
```

You should recieve output similar to mine.  eth0 is the wired ethernet card, and eth1 is your wireless network card.

```
kris@ibook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Homer"  Nickname:"Homer"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:12:17:A9:E3:EC   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=-29 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:341  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kris@ibook:~$ 
```

As you can see my WAP is configured for both B & G networks.  To see if your ibook has recieved a network address, run this command.

```
ifconfig
```

Your output should look similar to this
```

kris@ibook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:51:30:94:1E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:41 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:14:51:80:67:EB  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:51ff:fe80:67eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19033 errors:0 dropped:3888 overruns:0 frame:0
          TX packets:15211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19298698 (18.4 MiB)  TX bytes:3739457 (3.5 MiB)
          Interrupt:52 Base address:0x4000 

eth0:avah Link encap:Ethernet  HWaddr 00:14:51:30:94:1E  
          inet addr:169.254.4.45  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:628 (628.0 b)  TX bytes:628 (628.0 b)

kris@ibook:~$ 

```

As you can see for my wireless network card eth1, my ibook has received a network address via dhcp of 192.168.1.101.You can also use the tool "iwlist" to scan for all available networks.  The network "Homer" is my WAP.
```

kris@ibook:~$ sudo iwlist eth1 scanning
Password:
eth1      Scan completed :
          Cell 01 - Address: 00:12:17:A9:E3:EC
                    ESSID:"Homer"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-62 dBm  Noise level=-73 dBm
                    Extra: Last beacon: 120ms ago
          Cell 02 - Address: 00:18:F8:B2:20:B0
                    ESSID:"Maillet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:8
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=62/100  Signal level=-83 dBm  Noise level=-256 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 6024ms ago
```

As you can again see, my network is configured for both B&G, my WAP is set to channel 9, and my encryption is enabled.  I wrote this entire post using my ibook g4 wirelessly.  You can do it hang in there.  Please post back and let us know how your are doing.  :D

---

### Post by TonySmash on 2007-05-27
tcrroadie-

THANK YOU SO MUCH!!! i had completely overlooked the possibility that my router could be configured to run a mixed network *bangs head against wall*

now i have the internet up and running, even if it is only at B (which is fine for me). thank you again!!

---

### Post by tcrroadie on 2007-05-27
Great, 

Happy to hear you got it working.  :D

---

