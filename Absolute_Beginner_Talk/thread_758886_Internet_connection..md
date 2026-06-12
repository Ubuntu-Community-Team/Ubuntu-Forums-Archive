---
title: "Internet connection."
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Oronsay on 2008-04-18
I am an elderly new boy to Ubuntu.     I can count the number of days experimenting from the CD on one hand before installing yesterday.     I like what I see and want to continue expanding my Linux knowledge.     But...
Naturally I have stumbled across a problem and ask the indulgence of members to solve this probably simple and stupid problem.

I have failed to connect to the internet.
My computer is dual bootable with Windows XP Home via the Grub selection.     I am using XP to place this question so that side is working OK.     My computer has an Asus Motherboard P5B de luxe  WiFi-AP which feeds into a D-Link modem model DSL 500G via a RG45 socket.     No wireless system,  all cable connected.     The MB also has two LAN sockets.
The XP program is set up employing the LAN (Marvel Yukon 88E8001/8003/8010PC1 Gigabit Ethernet Net Controller) although there is only one computer.     There is also a WAN Miniport (PPPOE).   Both these have to be enabled to connect to the 'net on XP.

I have entered the 'Network Settings' and set ET0 to DHCP without any sucess.   During installation Ubuntu stalled while proceeding through "Install System' - Configuring APT - 82%- Scanning the mirror.    Thinking it was just searching for items I left it stalled for four hours until I pulled the cable from the RG45 socket.     After the installation was completed rapidly.


Can someone please give simple steps to resolve the situation.     You will gather by this that I am not greatly familar with the workings of computers.

Thank you in anticipation of your replies.

Oronsay

---

### Post by mbadawi23 on 2008-04-18
I found a driver that may work for you here:
[http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36]("http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36")

1. download the file.
2. extract it by right clicking on it and hitting extract here.
3. open the readme file and follow the installation instructions.

Note. you may need to run the commands in the installation using the "sudo" command to execute them as "root"

---

### Post by Oronsay on 2008-04-22
Thank you for your reply,  mbadawi.

I downloaded the driver from the above site,  unzipped it, burnt it to a CD and printed the Readme instructions this was all on XP.     The CD was then loaded into Ubuntu and appeared on the Desktop;  all files appeared complete when it was opened.     Entered into Terminal as the Root User but when trying to install the Driver from the CD hit a brick wall.
> tar xfvj install-???.tar.bz2 and
 > bunzip2 -c install-???.tar.bz2 | tar xfv -  both indicated 'Cannot open: No such file or directory.     
Tried > cd DriverInstall and > ./install.sh in turn with the CD still in the unit but both with the same result as before 'No such file or directory'.   
Since then have hunted around for a solution.     I am guessing that the Driver needs to be copied from the CD into a position that the Terminal commands can easily seek, but where?    Don't really know,  just guessing really.
Any ideas anyone,  please.

Oronsay.

---

### Post by Oronsay on 2008-05-02
Well I have waited more than a few days to see whether any more help might appear but no.     

It would seem that I have two options.     One is to buy an ethernet card and install it,  then attempt to get it connected to my D-Link modem model DSL-500G.     The card that I anticipate purchasing is a D-Link DFE-530TX that according to the list of compatible cards 'works straight out of the box' and is available here.     
The second option is to return to Windows and completely forget about Ubuntu 7.10.    I am reluctant to do this but another problem has raised its head that of my year old HP Scanner Scanjet 3770, that I use a lot, but has no compatible drivers for Ubuntu Linux.   Or none that I have been able to locate so far.

Any help or suggestions would be greatly appreciated.

Oronsay.

---

### Post by bartcramer on 2008-05-02
Some hints may help, though I'm not sure :-)

Maybe a silly question: does the tar/bzip file indeed contain question marks? A question mark is used in the console as a mask, and may be the reason that you cannot unpack the archive. 

You can use Nautilus (the file manager) to copy the file from your CD-ROM to your Desktop, and unpack it using Nautilus as well. You do not necessarily need the command line for this. 

AFAI understood, you are not so familiar with the command line. 
pwd : current directory
cd : move to directory

'~' (without quotation marks) stands for your home directory, and 'cd ~/Desktop' moves your current directory to your Desktop directory. 

Hope that helps...

---

### Post by digibuy.co.uk on 2008-05-02
try [http://www.marvell.com/drivers/drive...dId=153&pId=36](http://www.marvell.com/drivers/drive...dId=153&pId=36)

[http://www.digibuy.co.uk/](http://www.digibuy.co.uk/)
[http://www.digibuy.us/](http://www.digibuy.us/)

---

### Post by brigux on 2008-05-02
Your card is pretty common I dont believe the driver is the issue here. More likely there is a problem with yout network settings.
Can you ping [www.yahoo.com?](www.yahoo.com?) Probably not, but then can you ping 69.147.114.210, which is one of the address they use. if yes, you have a dns problem, manually enter your DNS IP (use 208.67.222.222 and 208.67.220.220 if you dont know which one you should use, those are opendns)in your /etc/resolv.cnf file.
Now, is your Gateway ok? Check your ip seetings(ifconfig -a) and check the gateway. You can also check it by running netstat -ra.
Your gateway should be your modem internal IP address.
Now if nothing works, please post the result of 
```
ifconfig -a
```
and 
```
netstat -rn
```

---

### Post by Oronsay on 2008-05-02
Thank you, Gentlemen for your very quick replies.
There will now be a delay while I attempt to find my way around and implement your suggestions.
Your response is greatly appreciated.

Oronsay.

---

### Post by Oronsay on 2008-05-09
Firstly,  Gentlemen,  I must apologise for the delay in responding to your suggestions and requests.   A public holiday and domestic commitments have taken a larger toll of my time than I had anticipated.

**_Bartcramer._**
Following your question,  yes,  the tar/bzip file does contain three question marks and I then thought that it might be that the question marks should be replaced with the name of the driver.
So in both I substituted .sk98lin in both command lines that were taken from the ReadMe instructions.   The result was negative in both attempts.
I am not familiar with Nautilus and was unable to locate it so this fell flat too.

 **_Brigux_**
My attempt to ascertain if the Gateway was functioning in both instances ended in a 'Command not found' notice.
The information requested has to be copied by hand from Ubuntu to Windows,  that has the internet connection as both are on the only computer. 
 
 'ifconfig -a'is as follows:-
eth0     Link encap:Ethernet   HWaddr 00:18:F3:D0:04:B7
         inet addr:10.1.1.7  Bcast:10.255.255.255  Mask:255.0.0.0
         inet6 addr: fe80::218:f3ff:fed0:4b7/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
         RX packets: 578 errors:0 dropped:0 overuns:0 frame:0
         TX packets: 666 errors:0 dropped:0 overuns:0 carrier:0
         collisions:0 txqueuelen:1000
         Rx bytes:42358 (41.3 KB)  TX bytes:52746 (51.5 KB)
         Interrupt:20

eth1     Link encap:Ethernet  HWaddr 00:18:F3:D0:0A:EE
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX PACKETS, TX PACKETS, RX bytes, and TX bytes 
         all indicate 0      txqueuelen:1000 
         Interupt:17

lo       Link encap: Local Loopback
         inet addr: 127.0.0.1  Mask: 255.0.0.0
         inet6 addr: ::1/128 Scope: Host
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         Again RX packets, TX packets, RX bytes and TX bytes
         all indicate 0       txqueuelen:0

wlan0    Link encap:Ethernet  Hwaddr 00:15:AF:0B:F8:DF
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         Again RX packets,  TX packets, RX bytes and TX bytes
         all indicate 0       txqueuelen:1000

wmaster0 Link encap:UNSPEC  HWaddr  
         00-15-AF-0B-F8-DF-00-00-00-00-00-00-00-00-00-00 
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         Again RX packets, TX packets, RX bytes and TX bytes
         all indicate 0        txqueuelen:1000
-------------------------------------------------------------

netstat -na

         ACTIVE INTERNET connections (servers and established)
Proto Recv-Q Send-Q  Local Address  Foreign Address   State
tcp      0     0   127.0.0.1:631     0.0.0.0:*        LISTEN
tcp      0     0   127.0.0.1:2207    0.0.0.0:*        LISTEN
tcp      0     0   127.0.0.1:2207    127.0.0.1:59936  Established
tcp      0     0   127.0.0.1:59936   127.0.0.1:2207   Established
udp      0     0   0.0.0.0.0:32768   0.0.0.0:*
udp      0     0   0.0.0.0.0:68      0.0.0.0:*
udp      0     0   0.0.0.0.0:5353    0.0.0.0:*

There then follows 8 A4 pages of Active Unix domain sockets.

Please let me know if this information is important to you in entirety or as selected lines.

Hope that this information helps and thanking you again for your patience.

Oronsay.

---

### Post by brigux on 2008-05-09
Sorry I meant netstat -nr.. I dont know why I keep asking people -na instead of -rn.... probably because I'm dealing with some port issues at the moment, but no, netstat -rn is the correct one I would like to see, that's the route table.

---

### Post by brigux on 2008-05-09
lots of error on the network card indeed..
Can you 
```
ping -c 5 127.0.0.1
```
to check your tcp/ip protocol stack..?

---

### Post by brigux on 2008-05-09
.. thinking about it.. just try another network cable as well...

---

### Post by Oronsay on 2008-05-09
Hi Brigux,
Thank you for your very quick reply.   No problem with the confusion,  only too glad not to have to type out pages and pages of data!!!
Answer to your previous post.

netstat -rn.

Kernel IP routeing table.
Destination  Gateway  Genmask     Flags  MSSWindow  irtt Igace
169.254.0.0  0.0.0.0  255.255.0.0  U      0.0        0eth1
169.254.0.0. 0.0.0.0  255.255.0.0  U      0.0        0eth0
10.0.0.0     0.0.0.0  255.0.0.0    U      0.0        0eth0
0.0.0.0      10.0.0   0.0.0.0      UG     0.0        0eth0
0.0.0.0      0.0.0.0  0.0.0.0      U      0.0        0eth1

Thanks 
Oronsay.

---

### Post by Oronsay on 2008-05-09
**Brigux,**
Thank you for your prompt reply.    No problem over the confusion of the terminal data I am only too glad not to have to type out eight pages of data!!

In answer to your questions.

     _netstat -rn_

Kernel IP routeing table
Destination  Gateway   Genmask      Flags  MSS Window  irtt Iface
169.254.0.0  0.0.0.0   255.255.0.0   U     0 0         0 eth1
169.254.0.0  0.0.0.0   255.255.0.0   U     0 0         0 eth0
10.0.0.0     0.0.0.0   255.0.0.0     U     0 0         0 eth0
0.0.0.0      10.1.1.1  0.0.0.0       UG    0 0         0 eth0
0.0.0.0      0.0.0.0   0.0.0.0       U     0 0         0 eth1

       _ping -c 5 127.0.0.1_

Ping 127.0.0.1 (127.0.0.1)  56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.020 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.016 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.015 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.016 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.015 ms

...127.0.0.1 ping statistics...
5 packets transmitted,  5 received, 0% packet loss, time 3997ms
rrt min/avg/max/mdev = 0.015/0.016/0.020/0.004 ms

I hope this will assist you.     I am completely out of my depth here and just copy (accurately, I hope) what I see in the Terminal window.

I don't think it can be the cable as I use Windows XP Home on this same computer and that internet connection functions perfectly.

Cheers,
Oronsay.

---

### Post by brigux on 2008-05-12
If you're still around, can you:

```
ping -c 10.1.1.1
```

```
cat /etc/resolv.conf 
```

and from your Windows:
```
ipconfig /all
```

---

### Post by Oronsay on 2008-05-12
Hi there Brigux.
Yep still around,  ever hopeful!!

   ping -c 10.1.1.1
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
[-p pattern] [-s packetsize] [-t ttl] [-I interface or address]  [-M mtu discovery hint] [-S sndbuf]
[-T timesatamp option ] [ -Q tos ] [hop1 ...] destination

and 

   cat /etc/resolv.conf
         nameserver 10.1.1.1

Entering ipconfig /all in RUN of Windows produced a quick flash of a black screen - too quick to read - but think it was Notepad with no entry.

Additional information that may possibly help.
Opening Network Connections from the Control Panel shows two sections.
1...Broadband.   One icon marked 'Connected Wan Miniport (PPPoE).
2...Lan or High-Speed Internet.   3 icons.
    a...Disabled 1394 Net Adaptor.
    b...Local Area Connection.  Connected.   Marvel Yukon 88E8001/8003.
    c...Local Area Connection 2.  Disabled.  Marvel Yukon 88E8001/8003. 

Cheers,
Oronsay

---

### Post by brigux on 2008-05-12
for the ping not working do:
ping -c5 10.1.1.1

for the windows:
do a start then run then cmd then ipconfig /all

---

### Post by SomethingCronic on 2008-05-12
> **Oronsay said:**
> Hi there Brigux.
Yep still around,  ever hopeful!!

   ping -c 10.1.1.1
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
[-p pattern] [-s packetsize] [-t ttl] [-I interface or address]  [-M mtu discovery hint] [-S sndbuf]
[-T timesatamp option ] [ -Q tos ] [hop1 ...] destination

and 

   cat /etc/resolv.conf
         nameserver 10.1.1.1

Entering ipconfig /all in RUN of Windows produced a quick flash of a black screen - too quick to read - but think it was Notepad with no entry.

Additional information that may possibly help.
Opening Network Connections from the Control Panel shows two sections.
1...Broadband.   One icon marked 'Connected Wan Miniport (PPPoE).
2...Lan or High-Speed Internet.   3 icons.
    a...Disabled 1394 Net Adaptor.
    b...Local Area Connection.  Connected.   Marvel Yukon 88E8001/8003.
    c...Local Area Connection 2.  Disabled.  Marvel Yukon 88E8001/8003. 

Cheers,
Oronsay

Hi, when you ran the first ping command, try it without the '-c' so that it reads

```
ping 10.1.1.1
```

also, when you run the ipconfig command in windows, do not type it in the RUN box as, like you say, it will flash too quickly. You need to type 

```
cmd
```

in RUN and then once the 'black box' appears, type the ipconfig /all command. You then need to send us the information from this.

So you know what's happening, I'm assuming the guys are trying to work out your IP address (the number assigned to your PC so that you can connect to the Internet).

I'm sure I use the same network card as you so this should not be a driver problem - these things usually work out the box but I'm sure a little more time we will get this resolved :)

Mike

---

### Post by arabadob on 2008-05-12
Sory but am also a new comer! i did the same thought it had stalled on 82% scanning for mirrors.... but gave it some time eventually it did. While not connected to the internet while installing takes shorter time cause of the config, but with internet just give more time , it might work
Thanks

---

### Post by Oronsay on 2008-05-12
Brigux,Thank you again for your quick reply.
Also welcome and thank you to Mike and arabadob for your inputs.
you will see from the fore going I am a complete numb skull when it comes to computers especially with a complete new O.S.

Some answers.

ping 10.1.1.1
Ping 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
64 bytes from 10.1.1.1: icmp_seq=1 ttl=64 time=0.394
This last line is repeated 'ad infinitum' until stopped, with the icmp_seq=number increasing on each line and a marginal difference in the ms time.

cmd....ipconf /all 

Windows IP Configuration
Host name.....:picardy
Primary Dns Suffix.....:
Node Type..............:Unknown
IP Routing Enabled.....:No
WINS Proxy Enabled.....:No

Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix:
Description.......:Marvel Yukon 88E8001/8003/8010 PCI
Gigabit Ethernet Controller
Physical Address.....:00-18-F3-D0-04-B7
Dhcp Enabled.........:Yes
Autoconfiguration Enabled....:Yes
IP Address......:10.1.1.7
Subnet Mask.....:255.0.0.0
Default Gateway.....:10.1.1.1
DHCP Server.........:10.1.1.1
DNS Servers.........:10.1.1.1
Lease Obtained......:12 May 2008  11:29;13
Lease Expires.......:12 May 2008  21:29;13

PPP adapter Speedy:

Connection-specific DNS Suffix...:
Description......................:WAN <PPP/SLIP> Interface
Physical Address.................:00-53-45-00-00-00
Dhcp Enabled.....................:No
IP Address.......................:201.95.62.7
Subnet Mask......................:255.255.255.255
Default Gateway..................:201.95.62.7
DNS Servers......................:200.204.0.10
                                  200.204.0.138
NetBIOS over Tcpip...............:Disabled

Hope this helps.
Cheers,
Oronsay.

---

### Post by SomethingCronic on 2008-05-13
> **Oronsay said:**
> Brigux,Thank you again for your quick reply.
Also welcome and thank you to Mike and arabadob for your inputs.
you will see from the fore going I am a complete numb skull when it comes to computers especially with a complete new O.S.

Some answers.

ping 10.1.1.1
Ping 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
64 bytes from 10.1.1.1: icmp_seq=1 ttl=64 time=0.394
This last line is repeated 'ad infinitum' until stopped, with the icmp_seq=number increasing on each line and a marginal difference in the ms time.

cmd....ipconf /all 

Windows IP Configuration
Host name.....:picardy
Primary Dns Suffix.....:
Node Type..............:Unknown
IP Routing Enabled.....:No
WINS Proxy Enabled.....:No

Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix:
Description.......:Marvel Yukon 88E8001/8003/8010 PCI
Gigabit Ethernet Controller
Physical Address.....:00-18-F3-D0-04-B7
Dhcp Enabled.........:Yes
Autoconfiguration Enabled....:Yes
IP Address......:10.1.1.7
Subnet Mask.....:255.0.0.0
Default Gateway.....:10.1.1.1
DHCP Server.........:10.1.1.1
DNS Servers.........:10.1.1.1
Lease Obtained......:12 May 2008  11:29;13
Lease Expires.......:12 May 2008  21:29;13

PPP adapter Speedy:

Connection-specific DNS Suffix...:
Description......................:WAN <PPP/SLIP> Interface
Physical Address.................:00-53-45-00-00-00
Dhcp Enabled.....................:No
IP Address.......................:201.95.62.7
Subnet Mask......................:255.255.255.255
Default Gateway..................:201.95.62.7
DNS Servers......................:200.204.0.10
                                  200.204.0.138
NetBIOS over Tcpip...............:Disabled

Hope this helps.
Cheers,
Oronsay.

Hi Oronsay,

From looking at this, the good news is that your network card works and you are picking up the correct address from what I can see. To make sure this isn't a name server issue could you please type the following into a web browser (firefox)

```
http://66.102.9.147
```

If all is good you will get [www.google.com](www.google.com) webpage.

EDIT
Just noticed the PPP part of your IPCONFIG. Are you receiving your Internet connection from another device and not your router? What do you have attached to the PC?

---

### Post by brigux on 2008-05-13
Yep, agree with SomethingCronic..

PPP adapter Speedy:

Connection-specific DNS Suffix...:
Description......................:WAN <PPP/SLIP> Interface
Physical Address.................:00-53-45-00-00-00
Dhcp Enabled.....................:No
IP Address.......................:201.95.62.7
Subnet Mask......................:255.255.255.255
Default Gateway..................:201.95.62.7
DNS Servers......................:200.204.0.10
200.204.0.138
NetBIOS over Tcpip...............isabled

...

Are you using a USB modem...?

In any case, It seems that you gonna need to install ppp or pppoe. Can you post as much information as you can on how is your connection to the Internet configured. Even links to your ISP help and Faq.

---

### Post by SomethingCronic on 2008-05-13
I think I know what the problem is. You have bought/received a router but continued to use your USB modem? Your router is currently sitting there doing nothing because you havn't configured it.

You will need to view the setup screen of the router (do this in XP if you wish) by entering the following in IE/Firefox:

```
http://10.1.1.1
```

Here you will need to setup the router with your Internet account details (username/password etc). when you disconnect your USB modem the router should take over.

If this works in XP, there is no reason it won't just automatically work in Ubuntu. 

Use your router, your modem will not act as a firewall and can/could be causing you security issues.

---

### Post by Oronsay on 2008-05-13
Well Gentlemen your notices sound very optimistic let's hope we are near the end of the problem.

Dealing with the requests in order.
[Http://66.102.9.147](Http://66.102.9.147)
Using the Ubuntu Firefox browser.   The server was not found.
I then attempted to connect to my normal Home Page,  [www.terra.com.br](www.terra.com.br) and again was notified that Firefox can't find the server.   Two failures.

My computer is connected to an external device.   A D-Link modem Model DSL 500-G via a RG45 connector; not a USB connector.   The telephone line plugs directly into the modem and is separated from the normal telephone dialling system by filters.As mentioned above when looking at Control Panel/Network Connections in Windows the connection appears to be made through two sections. The LAN and then the WAN Ethernet PPPoE.   Should either of these sections be 'disabled' then no connection to my ISP is made.    The Asus motherboard only has two RG45 connectors; the D-Link unit is connected to the first of these.

To be truthful I am not certain of the difference in terminology between a router and a modem.   Windows and Ubuntu are in a dual boot (Grub selection) set up on same computer.   I only have the one computer.

Using the Windows O.S. and connected to the internet via all the above items and using Firefox I entered the code  [http://10.1.1.1](http://10.1.1.1) and then gained entry using Admin in both boxes.  The result is in the attachment below. 

Should I have to install PPP or probably PPPoE where would I find a step by step tutorial?     I have no idea where to start. 

 I really must thank you for your patience and perseverance in face of my ignorance.     

Hope the foregoing helps.

Oronsay.

---

### Post by SomethingCronic on 2008-05-13
Hmm, I don't get how this has been configured. From what you've posted and the attachment I can't help but think you are receiving your Internet connection from another device.

When you access the DLINK admin page is there anywhere to configure your WAN/Internet connection?

I'm afraid I'm not familiar with D-Link routers specifically but they are normally fairly generic.

Just so you know, the modem you mention is also a router - for now this isn't too important but a modem that is also a router is a better option than just a modem.

---

### Post by SomethingCronic on 2008-05-13
Thinking about this Oronsay you *must* have another device attached that is giving you Internet - your DLINK modem (according to the attachment report you sent us) does not have an internet connection. The WAN link says it has an IP address of 0.0.0.0 - if this is the case then you have no Internet.

I would suggest you check every USB/Net Connection to your PC and confirm what they are - you don't have a mobile phone attached or a 3G card do you? - sorry I'm not must more help than that

---

### Post by brigux on 2008-05-14
Can you try this HOWTO and let us know the result?

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by Oronsay on 2008-05-14
Hello again, Gentlemen,

**SomethingCronic**
With reference to another device being connected I can assure you that the only connection is to the D-Link modem/router from the RG45 socket direct from the motherboard.   All the other connections apart from the mouse, keyboard, monitor,  loudspeakers and microphone are as follows:-
USB 1...HP Deskjet 6540 printer.
USB 2...HP Scanjet 3770 scanner.
USB 3...External Hard Drive for backups.
USB 4...Logi-Tech Quick Cam Orbit web camera.
Front panel USB socket, used occasionally for the digital camera downloads.
The D-Link admin page has numerous sub files in a tree format.   I am not at all familiar with this unit as it was installed by the telephone engineer when he installed the broadband system along with the telephone line filters.    I have had no necessity to alter anything in this unit,  to date.   The old story if it works don't fiddle with it.     This internet connection works perfectly well in conjunction with my Windows XP Home O.S.

**Brigux**

I downloaded and printed the How To instructions ADSLPPPoE. from the link you supplied,  thank you very helpful indeed.   Followed the instructions to the letter double checking each move.   At the end I opened Firefox but again it was unable to find my normal server after I entered the URL. 

I am afraid that this has not been much help to you.   I have a nagging feeling that the problem circulates round the motherboard having to connect to the LAN first and pass through the WAN PPPoE to the D-Link modem/router.   If the WAN PPPoE has been set up,  as above that leaves the LAN.   Where do I find another tutorial to set this system up?   I don't really know I am just grasping at straws in the dark so to speak.

Thanks again to both of you,
Cheers,
Oronsay.

---

### Post by brigux on 2008-05-15
I would then +1 SomethingCronic's suggestion:
Stop trying to connect the pppoe from the box but instead, contact your isp to make them help you configuring the Router instead of the PC. So the Router will take care of all the Internet setting. When that is done the PC won't use ppp anymore, will just use the router as the Internet GAteway using the LAN and we know the LAN works on both your linux and windows.. problem solved.

---

### Post by oninjao on 2008-05-15
i had a similar prob when i first started if i remember how to repair it ill tell u

---

### Post by Oronsay on 2008-05-15
Well, thank you both again, Gentlemen.
Will try your last suggestion.     I think that I will have to call in a IT Technician,  if I can find one conversant with Linux/Ubuntu, as my Portuguese is not up to a standard to sort out technical terms over a telephone.
The other alternative is to live with Windows,  what a disappointment.  I had such high hopes.     
Generally speaking it seems that Linux and Ubuntu is in 'Catch 22' situation.   To work as smoothly as Windows out of the box Linux needs refining.   But to achieve this it needs access to Drivers for everything and companies are only in business to gain money for shareholders,  so nothing is free.    Coupled to this the mass public (like me) is ignorant of or would rather not know of Terminal commands.   Basically they want a O.S. that functions first time but would willingly learn simple logical changes in presentation.
Sincerely thanking you both for your time,  patience and perseverance.
Cheers,
Oronsay.:sad:

---

### Post by SomethingCronic on 2008-05-16
Oronsay, Your DLINK router is doing nothing at the moment - if you disconnect this while in Windows you should still have an Internet connection. I suggest you test this.

I would hope you want want to make full use of this device anyway. As long as you have your ISP details you should be able to configure your router - when this is done you will not need anything installed on Windows/Linux for your connection to work.

Sorry if we are unable to help any further, but I still think if you enter your DLINK admin, enter your ISP email account and password, that this will pretty much be done.

---

### Post by Oronsay on 2008-05-17
Hello Mike,
Just casually dropped by to see if anything had been added to the thread and was surprise to see your message.   Thank you.

As the D-Link modem/router is in series with the output from the motherboard or rather forms the connecting link from the motherboard to the telephone outlet; I was unable to take it out.   That is connect the outlet of the motherboard directly to the telephone outlet - the outlet on the motherboard is an RG45 and the telephone input/output is the standard four pin connector.   I don't have an adaptor or a suitably ended cable to made a direct link.
What I did do was to switch the D-Link unit off and immediately lost my internet connection while using the Windows O.S. 
My conclusion is,  for what it is worth, that the chain or sequence of items that need to be connected and operable to enter the internet is this - First the WAN Miniport PPPoE then the LAN (Marvel/Yukon 88E8001/8003/8010PC) and finally the D-Link modem/router.   If any of these are disabled, inoperable or set up incorrectly the connection fails.   It might be quite possible to link the o/p of the motherboard to the telephone outlet and for the system to work.   Alternatively to adjust the D-Link internal settings but as it works OK as set up I am reluctant to dive into something I know nothing about,  just in case I loose the connection all together.   It would seem that the LAN section has not been detected or set up correctly with the Ubuntu installation.  
I am tempted to go back to my original idea of installing an DFE-530 TX Adapter card in the computer to see if I can by-pass the existing setup and at the same time make it easier for Ubuntu to see the D-Link modem/router and therefore the internet.    This adapter card is recognised by Ubuntu and apparently works 'straight from the box'.
What do you think?
Cheers,
Oronsay.
_________________________________________________________________

---

### Post by SomethingCronic on 2008-05-17
I didn't mean for you to connect your phone line direct to the motherboard and cut out the router, your quite right that RJ45 port will not accept the telephone wire.

I'm at a loss with this I'm afraid, You're router clearly does receive your Internet connection then but uses a method that I'm not familiar with.

A quick ```
apt-cache search ppp
``` shows the following items can be installed for ubuntu

```
ipppd - PPP daemon for syncPPP over ISDN
isdnutils-base - ISDN utilities, the basic (minimal) set
kppp - modem dialer and ppp frontend for KDE
ppp - Point-to-Point Protocol (PPP) daemon
ppp-dev - Selected headers from the ppp package
pppconfig - A text menu based utility for configuring ppp
pppdcapiplugin - plugin for pppd to communicate with CAPI-capable ISDN cards
pppoeconf - configures PPPoE/ADSL connections
wvdial - PPP dialer with built-in intelligence
br2684ctl - Utility for configuring RFC 2684 ATM/Ethernet bridging
diald - dial on demand daemon for PPP and SLIP
dxpc - a differential X protocol compressor
eql - load balancing tool for serial network connections
gkrellm-alltraxclock - analog clock plugin for GKrellM
gnome-ppp - modem internet connection tool for the GNOME Desktop

```

Hopefully you can get these installed from the livecd, and someone will be able to help you out with the configuration. I would suggest trying ```
sudo apt-get install ppp gnome-ppp
``` and seeing if this helps - but I am guessing now.

---

### Post by Oronsay on 2008-05-19
Hi there Mike,
Thank you for your reply.
I have been searching around trying to understand from what information I supplied you deduced that I had an alternative device connected to the internet.    I have confirmed the information taken from the D-Link router,  it is basically the same as supplied.   I also attach additional information taken from the same unit while connected to the net, and obviously using Windows and Firefox, to see if that helps.     I wiped out my current installation of Ubuntu and installed Kubuntu 8.04 Hardy Heron,  mainly to see if that had any luck in detecting and setting up an internet connection,  but it was in vain.   I still have Kubuntu installed but can easily change it.
I downloaded the .PDF of the User's guide for the D-Link unit.   This lead me to wondering if the unit was used in the 'Bridged' mode but checking through it doesn't seem the case.
So basically I am back to square one,  no internet connection and no idea how to remedy the situation.    Finding an IT technician here who is familiar with Linux/Ubuntu/Kubuntu is difficult as everyone uses Microsoft and eyes roll upward if I mention something else!
Thanks again Mike for suggestions and leads they have been really appreciated.
Cheers,
Oronsay.
_________________________________________________________________

---

