---
title: "Can't Connect to the internet"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by afzalnaj on 2007-08-12
hello....

im a newbie to linux, my internet is not connecting so plz help me

My internet connection is of Connect.net.pk -> Connect Communications

the setup is as following:

My computer is connected to a server through LAN
a dialer is provided for windows through which i connect to the internet

the properties of the dialer after connecting in windows xp are as follows

```
Device Name : WAN Miniport (PPTP)
Device Type : vpn
Server type : PPP
Transports : TCP/IP
Authentication: MS CHAP V2
Compression : MPPC
PPP multilink framing : off
server ip address : 125.209.*.*
client ip address : 125.209.*.*
```

now the properties of my lan network are as follows:
```
my ip address : 10.104.130.95
dhcp server    : 10.104.128.3
DNS  :   10.101.10.1
DNS  :   10.101.10.2
```

plz tell me how can i set ubuntu up to log in to the internet...i have followed all the guides that i have found but to no avail...please tell me the process from after the installation of ubuntu and in detail.

my ubuntu version in 6.06 LTS (dapper drake)

when i type ipconfig in command prompt in xp i get the following

[FONT="Fixedsys"]Windows IP Configuration

Ethernet adapter Local Area Connection:
Connection-specific DNS Suffix . : connect.net.pk
IP Address. . . . . . . . . : 10.104.130.95
Subnet Mask. . . . . . . . : 255.255.252.0
Default Gateway . . . . . . :
PPP adapter Connect Communications:
Connection-specific DNS Suffix . :
IP Address. . . . . . . . . :125.209.*.*
Subnet Mask . . . . . . . . :255.255.255.255
Default Gateway . . . . . . :125.209.*.*[/FONT]


thanks

PS: i cannot use aptget because ubuntu is not connecting to the internet..any package or dependencies..i have to download from windows
__________________

---

### Post by afzalnaj on 2007-08-12
can anyone please help?

---

### Post by kleo skywalker on 2007-08-13
I'm a total newbie too, so I'm not sure this will help. Also I'm using Feisty and have no clue about Dapper. I had similar problems when I first installed Feisty and it took me many Wikipedia look-ups and ISP phone-calls to get things working.
In Feisty, you can configure your internet connection from the System-->Administration-->Network tools and Network  menu. You need to configure the device (from what you say, it seems like an Ethernet port). Ask your ISP if you're ok using DHCP settings or if you need to select Static IP, and then enter your IP address, gateway, subnet, DNS etc info accordingly.
Go to Help --> Connecting to the Internet -->ADSL Connections, and follow the instructions for PPPoE modems.
Once that's done, go to network tools and see if pinging works. If yes, you can move to the next step - find out if your ISP provides a dialer for Linux that'll work in Ubuntu.
I hope this helps a little.
Do post how it works out, and if anything I said is unclear.

---

### Post by afzalnaj on 2007-08-13
i installed network-manager, network-manager-gnome packages...and my comp now connects to the network fine...i can open lan sites...and pinging works too...the problem is the dialer...there isnt a dialer for linux...or maybe there is but its rpm...i'll see if i can use alien to install and try that...

my friend (having the same prob) called the isp headquarters and they didnt have a clue!!! (bad news) :(

---

### Post by phidia on 2007-08-13
> **afzalnaj said:**
> i installed network-manager, network-manager-gnome packages...and my comp now connects to the network fine...i can open lan sites...and pinging works too...the problem is the dialer...there isnt a dialer for linux...or maybe there is but its rpm...i'll see if i can use alien to install and try that...

my friend (having the same prob) called the isp headquarters and they didnt have a clue!!! (bad 
news) :(

There is a dialer for linux/ubuntu/and it's variants.
But I'm not sure if it will work in your situation. Try installing gnome-ppp. If you are using kde then install kppp. Hope that helps.
You don't need to use alien either. If for some reason the programs i mentioned don't work for you then try [chestnut dialer]("http://www.icewalkers.com/Linux/Software/519200/chestnut-dialer.html").

---

### Post by kleo skywalker on 2007-08-15
My ISP didn't provide a suitable dialer either, so they gave my IP address permission to log in to my internet account using a URL - now I just have to open that URL in a web browser and log in. Maybe your ISP could do that too?

---

### Post by afzalnaj on 2007-08-15
maybe...i'll try that...but i called them today...they said they can only help me if i have fedora or redhat

---

### Post by e_james on 2007-08-15
afzalnaj
I've been watching this thread to see what sort of outcome you achieved. I might be able to make some suggestions but I need more information. If I understand correctly, your PC has 2 network connections. One is the ethernet LAN connection which is working fine with ubuntu; the other is some sort of internet modem. This could be 56k dial-up, or ISDN or cable or DSL or ADSL. The dialer requirements would usually be different for each one. Can you say what the modem is, what the service type is, and how the modem connects to your PC?

---

### Post by afzalnaj on 2007-08-15
no...i only have one connection

heres a brief summary and description (i dont know what to call my net connection!)

**Version = Feisty 7.04 (installed anew today)**
I connect to a LAN...(normally)...then i launch the dialer which authenticates from crras.connect.net.pk (on the network)...when the dialer connects i am able to get on the internet...

basically i think its connection sharing...**it *is* VPN**...there is no encryption (maybe MS CHAP V2)...and mppc compression...and pptp

thats it...i only have a network card

The network part is fine with ubuntu since i have installed network-manager...the internet part's the troublesome one

---

### Post by st33med on 2007-08-15
Type this command in the terminal:
```
lspci
```
Then post the output here.

---

### Post by afzalnaj on 2007-08-16
here u go...also i would like to add that my isp doesnt use any encryption...no mppe or anything else...only mppc compression and MS CHAP V2 Authentication

```
afzal@ProStreet:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
02:01.0 Communication controller: Conexant Unknown device 2f30 (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:04.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
afzal@ProStreet:~$ 
```

---

### Post by e_james on 2007-08-16
This is definitely unfamiliar territory for me but, if I make one critical assumption, I think I can suggest a solution for your problem. If I'm wrong the rest of this post is rubbish.

'crras.connect.net.pk' is a registered internet domain so I think you are already 'connected' to the internet. The internet is not a single system but rather a collection of services built on the foundation of TCP/IP ([http://www.protocols.com/pbook/tcpip1.htm](http://www.protocols.com/pbook/tcpip1.htm)). Basically your ISP is blocking your access to services such as e-mail and web browsing until you login. The 'dialer' handles the login process but I am 95% confident that you can do the same with a few linux terminal commands if you have the correct information. You need details such as an IP address or a URL. You might find these as plain text embedded in the 'dialer' code or your ISP may be willing to tell you. This link illustrates what I mean

[http://linux.omnipotent.net/article.php?article_id=12534&page=-1](http://linux.omnipotent.net/article.php?article_id=12534&page=-1)

but, as I said at the start, it is unfamiliar territory.

---

### Post by afzalnaj on 2007-08-16
wow man...i never thought it that way...yes theres a 98% chance that might be true...!!! cool...

there is no dialer code i suppose...there is a .cms file and a .inf file...how can i use the info?...the dialer is not an exe file (as far as i know) it runs with cmmon32.exe

---

### Post by e_james on 2007-08-16
If you take the route I suggested it will not be a quick fix, but you will learn some interesting things about linux and networking. Unfortunately, although I understand some of the ideas, I do not know most of the details. If you can find a better advisor, go for it. In the meantime I can try to help you figure it out. I would start by opening the .cms file and the .inf file using Notepad. A .inf file is usually plain text. Even if the .cms file is not plain text you should be able to read any plain text it contains. You could find some useful clues. According to a google search, the cmmon.exe file is a Microsoft utility, so its only relevance lies in what it does (Connection Manager Monitor), which may not be important.

---

### Post by afzalnaj on 2007-08-17
i got these things from the files

gateway/hostname = crras.connect.net pk

that was the only thing i was able to figure out...
ok leaving that aside...i figured that the dialer is nuthin special...

i can make a normal windows vpn connect in network connections...put crras.connect.net.pk as hostname and it will connect..

vpn pptp...mppc...mschap v2...i just need something that will hold these things

i tried the built in network-manager and network-manager-gnome with network-manager-pptp....i put crras.connect.net.pk as hostname

checked authenticate peer...(some other ones)...but not mschap (is that v2 or normal?)

i checked mppc compression....unchecked require mppe coz its not used in the connection...
ran the thing...and it reported...bad username or password...but the username and password i entered is correct...

---

### Post by e_james on 2007-08-17
Please forgive me if I am telling you things you already know. I am not familiar with the procedures you are describing and I am not in a position to experiment. I propose to ramble on a bit in the hope that some comment may provide a useful clue. 

First, the message 'bad username or password' is deliberately uninformative so that someone attempting to break in to a system will gain no clues as to what part of their procedure is correct. All it tells you is that you did something wrong. Sometimes an additional security feature is to lock out a username if it is used incorrectly too many times in succession. You should probably make a normal login after every 4 or 5 failures.

If it was possible to observe the network traffic as you attempt to login you would see the messages sent and the responses. I think software such as Wireshark
([http://www.wireshark.org/docs/wsug_html_chunked/ChapterIntroduction.html#ChIntroWhatIs](http://www.wireshark.org/docs/wsug_html_chunked/ChapterIntroduction.html#ChIntroWhatIs)) would probably be suitable but it would take a while to learn how. There are Windows and Linux versions and they are free.

It is possible that Linux does something automatically that Windows doesn't or that Windows does something automatically that Linux doesn't. It is possible that there is something in the process that is Microsoft specific (mschap v2?) but I doubt that.

Especially with networking when you are using a linux gui application it is commonly just a graphical interface which sends linux commands in plain text and interprets the messages received. Try this in a dos Window. Type 'ftp<enter>' and then 'quit<enter>'. Those commands start and stop the Windows ftp client. You can send and receive files using typed commands without using a Window or a mouse. I believe similar but more powerful facilities are available with linux but I don't know how to access the ones I think you need. It's probably so obvious I can't see it because I am looking for something complicated.

You could take your latest knowledge and post a new question in the Network forum. You could try another forum. I got some useful answers in this one some time ago ([http://www.linuxformat.co.uk/](http://www.linuxformat.co.uk/)).

---

### Post by afzalnaj on 2007-08-18
ok...thanks for the info....but i knew some of it...and some was untrue (mschapv2 is supported on linux) i have downloaded pclinuxos, linuxmint and freespire...i think they might hav the answer to my problems...hope its solved then!

---

### Post by e_james on 2007-08-18
You may have noticed that I used the word 'linux' rather than 'ubuntu'. Ubuntu is the distro I like for most general purposes but it is not always my first choice for certain specialised tasks. For instance, Knoppix is particularly useful for hardware diagnosis and repair; as it should be since that is one of its main intended functions.

I didn't say mschapv2 is not supported on linux (I would expect that it would be), but there might just be some little quirk in your particular circumstances. Authentication does seem to be your problem. 

My main problem with Windows is that it keeps trying to help me in situations where I don't want help. My main problem with linux is that I keep thinking Windows.

---

### Post by afzalnaj on 2007-08-18
ok...im downloading freespire now...any idea about how to boot from an iso image...my cd writer is dead....

---

### Post by e_james on 2007-08-18
I believe you can do it with the right procedure but it looks like a lot of work, mostly working out the details.

You can read an iso image with linux. Presumably you can copy the files to another location.
You can boot linux from a floppy disc or a usb flash drive (external hdd?). Most modern PCs can also boot from a network source.

If you have a look at these links, I think you will see why it's difficult but also that it is possible.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[http://www.bootcd.us/](http://www.bootcd.us/)
[http://www.phenix.bnl.gov/~purschke/RescueCD/](http://www.phenix.bnl.gov/~purschke/RescueCD/)

---

### Post by afzalnaj on 2007-08-27
thanks...but i eventually had to write cds...i have ubuntu and pclos 2007 installed now along with xp but i cant login to internet through the linuxes...the closest ive come is pinging the server...125.209.124.1...cant ping [www.google.com](www.google.com) or open any site 

plz help 

really frustrated

---

### Post by e_james on 2007-08-27
Hello again afzalnaj. I wondered how much progress you had made.

As I understand the situation at this moment you need to know how to do three things.

1. How to manually logon to your internet gateway using Windows.
2. How to do the same logon using Linux.
3. How to automate the Linux procedure.

Normally, in this sort of situation, I would try to emulate your circumstances but in this case it would be difficult. It might be helpful if I explained why.

Mostly I use Windows (XP Pro). I would like to use Ubuntu (or other Linux) instead, but there are several important applications for which I don't yet have a satisfactory linux substitute. When I have time to spare I switch to linux in order to gain more experience. My normal internet connection is via a wireless adsl router which does its own logon to my ISP. As an alternative I have a usb adsl modem but I may have broken it while trying to use it with ubuntu. The word 'firmware' may or may not have more than one meaning in this context. I also have a small selection of dial-up modems (pcmcia, usb and serial). As a first step I would like to try logging on to one of my ISPs manually using Windows and a dial-up modem. If I can do that then I would like to try again with ubuntu. So far I have never successfully used a dial-up modem with linux so that's a challenge to start with.

In the meantime I tried a search of all ubuntu forums for the word 'hyperterminal'. Some of the results look particularly interesting, notably these so far

[http://ubuntuforums.org/showthread.php?t=510253&highlight=HYPERTERMINAL](http://ubuntuforums.org/showthread.php?t=510253&highlight=HYPERTERMINAL)
[http://ubuntuforums.org/showthread.php?t=413103&highlight=HYPERTERMINAL](http://ubuntuforums.org/showthread.php?t=413103&highlight=HYPERTERMINAL)

I now have 2 suggested 'hyperterminal' alternatives for linux - 'gtkterm' and 'minicom'.

---

### Post by afzalnaj on 2007-08-27
**HELLO WORLD!!!!**

**THIS IS FROM UBUNTU 6.06 LTS Dapper that i am writing this post!!!**

I have successfully setup my internet connection...i installed networkmanager, networkmanager gnome, pptpconfig and their dependencies
added the network monitor applet...opened the eth0 configuration...opened its properties and unchecked the "Enable this Connection" checkbox

i opened up sudo pptpconfig

heres what i setup

i opened up sudo pptpconfig

typed all the things like shown:

[IMG]http://i221.photobucket.com/albums/dd287/afzalnaj/pptpconfig-servertab.png[/IMG]

selected all to tunnel in the routing tab...DONT EVEN TOUCH THAT EDIT NETWORK ROUTES BUTTON FOR NOW

[IMG]http://i221.photobucket.com/albums/dd287/afzalnaj/pptpconfig-routingtab.png[/IMG]

[IMG]http://i221.photobucket.com/albums/dd287/afzalnaj/pptpconfig-dnstab.png[/IMG]

Connect Comm tech help told me to disable all encryption when i had called them before...i did so

[IMG]http://i221.photobucket.com/albums/dd287/afzalnaj/pptpconfig-encryptiontab.png[/IMG]

enable debug mode in the last tab for precaution...press start...

if it says Connection Terminated...and some where above it says "mppe required but refused by peer"

then do the following

open the terminal and type 

gksudo gedit /etc/ppp/options.pptp

and do this

> 
**BEFORE:**

# [http://ppp.samba.org/](http://ppp.samba.org/) the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# {{{
# Require MPPE 128-bit encryption
**require-mppe-128**
# }}}

**AFTER:**
# [http://ppp.samba.org/](http://ppp.samba.org/) the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# {{{
# Require MPPE 128-bit encryption
**#require-mppe-128**
# }}}

comment that line

now disable debug mode and start the tunnel again

if it says connected...the best way to test is fire up that firefox and type any website you remember...you'll get to it...

**This tutorial has been written for the users of Connect Communications Pakistan LTD. which is in Karachi, Pakistan, i have seen many users wanting a way to get internet on ubuntu and i, along with so many devoted fellow ubuntuers, have found a way to do this...this might work in college VPNs too!**

I will try to do this on Ubuntu 7.04 Feisty and PCLOS ASAP!

[size=3]**BUT there is a problem here...after starting the tunnel I can access the internet perfectly well but not the sites on LAN...only when i stop it i can open up LAN sites...plz help me on this...this might be a route problem...plz help me :( dying to make it work now that its as if i am touching it :D**[/size]

cant contain my happiness :D

---

### Post by afzalnaj on 2007-08-27
> **e_james said:**
> Hello again afzalnaj. I wondered how much progress you had made.

As I understand the situation at this moment you need to know how to do three things.

1. How to manually logon to your internet gateway using Windows.
2. How to do the same logon using Linux.
3. How to automate the Linux procedure.

Normally, in this sort of situation, I would try to emulate your circumstances but in this case it would be difficult. It might be helpful if I explained why.

Mostly I use Windows (XP Pro). I would like to use Ubuntu (or other Linux) instead, but there are several important applications for which I don't yet have a satisfactory linux substitute. When I have time to spare I switch to linux in order to gain more experience. My normal internet connection is via a wireless adsl router which does its own logon to my ISP. As an alternative I have a usb adsl modem but I may have broken it while trying to use it with ubuntu. The word 'firmware' may or may not have more than one meaning in this context. I also have a small selection of dial-up modems (pcmcia, usb and serial). As a first step I would like to try logging on to one of my ISPs manually using Windows and a dial-up modem. If I can do that then I would like to try again with ubuntu. So far I have never successfully used a dial-up modem with linux so that's a challenge to start with.

In the meantime I tried a search of all ubuntu forums for the word 'hyperterminal'. Some of the results look particularly interesting, notably these so far

[http://ubuntuforums.org/showthread.php?t=510253&highlight=HYPERTERMINAL](http://ubuntuforums.org/showthread.php?t=510253&highlight=HYPERTERMINAL)
[http://ubuntuforums.org/showthread.php?t=413103&highlight=HYPERTERMINAL](http://ubuntuforums.org/showthread.php?t=413103&highlight=HYPERTERMINAL)

I now have 2 suggested 'hyperterminal' alternatives for linux - 'gtkterm' and 'minicom'.

forgive me if i am wrong man...but i think you forgot the prob here :D its a NIC that i am connecting with :D

---

### Post by e_james on 2007-08-27
I am very pleased to learn that you have made such good progress. I can say nothing about the internet - LAN problem except that I am sure it can be fixed.

I do know that you are using a NIC. I was looking for clues about using command line procedures for logon. I believe that, after the hardware makes the connection, it's all fundamentally networking using a selection of suitable protocols. I found another thread in a Windows forum which commented that Hyperterminal was useful for testing the modem but no use for negotiating protocols. I was hoping to find that the linux equivalents were better. Based on your procedure above, there would have been a lot of typing involved.

My last suggestion is that you collect together all you now know about your situation and post the question in a new thread. Try to think of a subject line which will attract the attention of the right sort of expert. My posting this message should temporarily move this thread close to the top of the list but it will soon drop down again. At this moment it's on the 5th page. You could put the thread in the Ubuntu Network forum or even try other linux forums.

---

### Post by afzalnaj on 2007-08-28
ok sir...thanks for all the help u did. :D i will deem this topic as solved as i have successfully connected to the internet :D

---

### Post by afzalnaj on 2007-08-28
hey man...i installed ubuntu 7.04 feisty today just to check whether it will work on it or not...and it didnt :( how can i make it work there??? because i plan on using either PCLinuxOS or Ubuntu...i need to connect to the internet

---

### Post by e_james on 2007-08-28
I thought you had finished this thread. 

This is my understanding of the circumstances.
Feisty introduced several new network management routines as standard. I believe most of these are added applications rather than new kernel code. The consequence for me is that Feisty connects more easily to the internet via my router than Dapper or Edgy did. More of the process is automated. Since yours is an unusual network requirement, I am immediately suspicious of the new, 'helper' software. A possible strategy might be to uninstall (using Synaptic) any network applications in Feisty which you didn't have in Dapper and then follow your Dapper configuration above from there. Maybe you have tried this already. If so, the only other suggestion I can think of is in my last post...a new thread.

---

### Post by afzalnaj on 2007-08-29
ok man....i followed the procedure i did for dapper...didnt happen...it was getting stuck at some point before executing route -n for the last time...anyways...i am waiting for my cable operator to return the PCLOS cd...i really loved that thing....i'll try something on that....gonna rest for now :D

---

### Post by zaigham_tt on 2007-11-18
Hiz salam how r u....

Me also User of Connect Communications  Plz Tell me How to configure the dailer and from where you download these packages...? post the url here plz.... 

I have Setup this From the site pptpclient.sourceforge.net In Fedora core 4 in GUI Same as above as follows:

kernel_ppp_mppe-1.0.2-3dkms.noarch.rpm 
libglade-0.17-16.i386.rpm 
libxml-1.8.17-13.i386.rpm 
php-gtk-pcntl-1.0.2-1.i386.rpm 
php-pcntl-4.4.0-1.i386.rpm 
pptp-1.7.0-1.i386.rpm 
pptpconfig-20040722-6.noarch.rpm 


when i run pptpconfig and then start it gives me a Error: 

"MPPE is required, But Kernel has no support" 


when i run "uname -r" 

2.6.11-1.1369_FC4 

i want to setup dailer in Fedora Core 4 in text mode...is it possible....??? Because i want to share Internet on 4 Pc's Through this machine...Via Squid Proxy Server....Help Me plz ....:)

---

### Post by xc0rpion on 2008-01-03
I am also a connect communication user and i too seem unable to connect to the internet. Using network manager I am able to connect to the vpn but still no connection to the internet. I guess its a routing problem.
Kindly contribute

---

### Post by afzalnaj on 2008-04-19
hi...sorry to disappoint all u connect users...but i have changed my internet connection 

so im not using Connect anymore :)

and as ejames said...many things have changed in the newer versions...so u always have to start from square one if u wanna find out a solution...and i hope that you do :)

---

