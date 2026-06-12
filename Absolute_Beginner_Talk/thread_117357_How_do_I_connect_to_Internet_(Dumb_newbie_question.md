---
title: "How do I connect to Internet (Dumb newbie question)"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Ingla on 2006-01-14
Hello.

I'm pretty new to Linux. I've been running 5.10 for a while and connecting to the Internet with a USB modem. I installed Ubuntu on another hard drive and installed the modem driver. It doesn't work. Same Ubuntu installation, same driver, same configuration. No good.

Anyway, someone suggested I just use my ethernet modem to connect and forget about messing around with the USB one. OK, but now I find I have no idea how to connect and can't find anything about it in the Unofficial Guide or anywhere else. I guess the question is too basic?

I can't find any installed PPPOE client, like rp or anything else. How to I connect "out of the box"? Ubuntu doesn't have Roaring Penguin.The visual connection tools just add icons to my desktop which don't seem to do anything. 

I'm surprised there's no visual, configurable tool like Windows dial up or something. There must at least be a command to use.

Can someone tell me (in baby talk), how to connect right after installing Ubuntu?

Many thanks.

---

### Post by Arktis on 2006-01-14
System > Administration > Networking
Even better: Right-click your panel > Add to Panel > Network Monitor.  Now you can acess the above tool directly from a panel applet which also visually indicates network traffic and lets you switch which network interface to use.

---

### Post by ed_d on 2006-01-14
Is this dialup or is it broadband? If dialup, get kppp. Best thing I used is to go to the upper right corner here, click on the "Official wiki" and in the search bar, type in the word modem. I wa able to configure a dial up account for my inlaws using that. Seeing as your sig line says you use kubuntu blue, I assume you are running kubuntu. Just follow the wiki, it talks you though everything very nicely. One thing that I recommend you do is when you dial out, open a log file if available. you may have to change permissions on a couple of files.

---

### Post by Azion on 2006-01-14
It depends on what connection u have.
Best thing to do is follow the wiki as Ed said

---

### Post by Arktis on 2006-01-15
[quote=ed_d]Is this dialup or is it broadband?[/quote]
*cough*
[quote=Ingla]ethernet modem[/quote]
Doesn't really matter though; network-admin lets you configure and use ethernet, wireless, or dial-up anyways.

---

### Post by Ingla on 2006-01-15
Hi.

Thanks for the replies. I went to the Wiki as suggested. I followed the instructions that seemed to apply...ran "pppoeconf".  It took three attempts...kept saying ADSL accessor not responding. Then, it said it configured the connection (I also set it to connect on boot). However, I cannot surf. Firefox just keeps saying "loading".

Tried typing  "sudo pon adsl". No error notices, but same result. Checked in Newtworking tools. Tried to ping my ISP's DNS IP. Nothing...100% package loss.

Any ideas?

Thanks

---

### Post by bscbrit on 2006-01-15
Can you print the result of running the following command please:

ifconfig

and then the results of the following

cat /etc/resolv.conf

Thanks.

EDIT And what is the IP address of your ethernet modem?

---

### Post by Ingla on 2006-01-15
Hi.

Back again. This is a bit involved as I have to try everything on the Ubuntu disk and then go back to Windows to connect and reply here.

Results of ifconf:
-----------------------------------
ifconf
eth0        Link encap: Ethernet HWaddrs: 00:11:09:02:E538
              inet addr: 10.0.0.2 Bcast: 10.255.255.255 Mask 255.0.0.0
              inet6 addr: fe80::2119ff: fe02:538/64 Scope: Link
              VP Broadcast Running MULTICAST MTU 1500 Metric 1
              RX Packets:8 errors:0 dropped:0 overruns:0 frame:0
              TX Packets:26 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 tzqueuelen: 1000
              Interrupt: 23  Base address 0xec00
lo            Link encap 23 Local loopback
              inet address: 127.0.0.1 Mask: 255.0.0.0
              inet6 addr: ::1/128 Scope: Host
              UP loopback running MTU 16436 Metric 1
              RX Packets: 308 errors:0 dropped:0 overruns:0 frame:0
              TX Packets: 308 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 tzqueuelen:0
              RX bytes: 26325 (25.7 KiB)  TX bytes: 26325 (25.7 KiB)
---------------------------------------------------------------------
Results of cat /etc/resolv.conf:
nameserver: 10.0.0.138
---------------------------------------------------------------------

I edited the name server to show my ISP's DNS server IP's
Then, wondering why this was showing a loopback (i don't know what I'm doing, but that, together with inet address 127.0.0.1, sounded like I'm trying to connect only to myself (localhost).

The connection wasn't set for static IP, so it didn't show an IP.

So, I changed the connection to Static IP and tried these combinations.
IP Address 192.168.0.1
Subnet Mask 255.255.255.1
Gateway Address 192.168.0.2

No good, so I tried

10.0.0.2
255.255.255.1
10.0.0.3

Also no good.

In the tools, it shows:
Protocol           IP Address        Netmask          Broadcast
ipv4                 10.0.0.2           255.0.0.0        10.255.255.255
ipv6                fe80:211: 9ff: feo2: e538.64 (not sure I copied this one right)

I also tried to change loopback to eth0, but every time I checked it had returned to loopback, i.e. edit didn't take.

That's about all I know. If someone can make sense of this and tell me what to do, I'd sure appreciate it.

Thanks.

---

### Post by mips on 2006-01-15
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

and leave the loopback interface alone ;)

---

### Post by bscbrit on 2006-01-15
OK, you _were_ set up for a 10.0.0 network which is fine in theory. but I suspect that your gateway (ethernet modem) is on 192.168.0.1 or 192.168.1.1 which are both common defaults.  You haven't told me which it is - please let me know if you know what the correct IP is.

Your nameserver(s) will not be either 10.0.0.... or 192.168..... because both of the networks cannot pass over the internet - these values are designed for networks.

So first of all, we must set your NIC to the same network group as your ethernet modem.  If you don't know what its IP address is, then we will have to make an inspired guess (I would go for 192.168.1.1 being your gateway).  In which case set your NIC for 192.168.1.2 and restart your network.

Then to the command line:

ping 192.168.1.2 -c 5

In this line we are pinging the NIC so you should get a response.  This will prove that your NIC is working.

Next:

ping 192.168.1.1 -c 5

If my guess was correct, then you should get a response from your gateway.  In which case cheer loudly,  and move on to the next test below.  Otherwise we are still trying to find the IP address of your ethernet modem / gateway.  Try setting your NIC to 192.168.0.2 and then:

ping 192.168.0.2 -c 5

ping 192.168.0.1 -c 5

If you get a response this time, then begin cheering now and move on, otherwise return to the forum and tell us what happened and what messages you saw on the screen please.

Next test

ping 64.21.33.9 -c 5

If you get a response now, then you are actually getting out on to the internet because this IP address is the ubuntuforums.org!

Currently, you are having to use IP addresses because your DNS lookup is set to your own machine - 10.0.0.138.  Your ISP will have given you (or at least should have given you) one or more IP addresses to use for DNS lookup.  These will need to be entered into your resolv.conf using either the GUI (System - Administration - Networking) or by simply editing the file using whatever editor you are most comfortable with (you will have to use sudo to enable changes to be written to the file)

For example, my resolv.conf looks like this:

nameserver 127.0.0.1
nameserver 195.244.192.xxx
nameserver 195.244.192.yyy

where xxx and yyy are numbers - but I don't want everyone to start trying to use my ISP's DNS.  Yes I know it is easy to look it up but those that know how to will realise that it is not clever, far better to use a local DNS.

Once you have edited the file, you should be able to do something like:

ping [www.ubuntuforums.org](www.ubuntuforums.org) -c 5

and the DNS will convert the name into the IP address and everything will work as it should.


Good Luck

---

### Post by bscbrit on 2006-01-15
I second mips' comment about leaving the loopback alone - if you succeed in changing that then all sorts of things will stop working!  :D

---

### Post by Ingla on 2006-01-15
Hi.

Back on Windows after trying all the tests listed on the url (2 messages back).

Here's the situation:

Physical: the equipment is OK and plugged in properly because it works on Windows.
_____________________________________
Results of "sudo mii-tool eth0"
eth0 negotiated 100 base TX-FD, link OK 
_____________________________________

ifconfig eth0 looks OK according to the example, so it seems the driver is loaded.
_____________________________________

lspci | grep eth 
0000:00:12.0 Ethernet Controller: VIA Technologies, Inc. VT 6102 (RhineII) (rev74)
_____________________________________
ifconfig eth0 shows 
inet address 10.0.0.2 Bcast 10.255.255.255 Mask 255.0.0.0
_____________________________________
route -n gives 10.0.0.138 as routers IP
_____________________________________
Ping router OK
_____________________________________
I renamed ipv6 as suggested and rebooted
_____________________________________

That's as far as the good news goes. Pinging a numeric IP results in 100% package loss (as, of course, does pinging a domain).

Firefox stays on "connecting to..." for an IP and "looking up..." for a domain.

I ran pppoeconf again and told it to start the connection at boot as well as to start now. Then I ran plog, which said it's running (rp-pppoe and pppd started by root). 

Note: rp was not included with Ubuntu. I attempted to install it from a deb (v3.6) but it wouldn't configure...even from the command line. I kept getting an error notice saying there was no console that could configure it. I don't recall exactly what it said...something like no cc no cl no a-couple-of-other things. So, I wonder how the system is running that instead of some native application??

I thought I'd post this before investigating the last reply because I think some of the items might be covered here.

I seem to have a knack for getting into impossible messes. Hope someone can help.

Thanks.

---

### Post by bscbrit on 2006-01-15
Stick with the working IP addresses for both your NIC and the modem router.  Don't worry, we are making progress:p 

We have proven the hardware up to the modem/router so now we are looking at your connection to your ISP.

Can you confirm that you have all the same settings when you try to connect using Ubuntu as you do when using Windows?  If you can then we can say with a very high degree of certainty that the problem lies with the software that you have installed.  

If that it the case then what we need to do is remove your current installation and start again, step by step, until we achieve Ubunty nirvana, otherwise known as a internet connection! :D

---

### Post by bscbrit on 2006-01-15
I suggest that you download this guide before you lose your internet connection.

[https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

(I'm sure that you already have seen it, but you might want a hard copy before you find out you cannot refer to it!)

I would recommend removing any deb packages that you have not installed using synaptic or apt-get from Ubuntu repositories.

Everything you should need should be available from Ubuntu, but without you ADSL connection I realise things are not always straight-forward.  As once you leave to do the installation we lose all contact with you (sounds like Apollo going round the back of the moon or something...!) it is probably best that you ask any questions before you start.

But things to check.  Do you get a flashing connection light on your modem when it is connected to the telephone line under Windows, and before you actually try to connect?  More clearly, make sure you know what indications your equipment gives for a working system during the entire boot up / connect cycle and watch very closely for the same signs when you are doing it under Linux.  It might give someone with more intelligence than I have what exactly is going wrong :)

---

### Post by mips on 2006-01-15
Ingla,

If you are not using DHCP then use a subnet mask that matches your routers. But forget about this for now as it seems dhcp is working fine.

You are using an ethernet router so STOP trying to use PPPoE on your ubuntu pc. The router will handle the PPPoE stuff. You do not require any drivers either. You should only require DHCP on your PC.

Some questions:
1. What brand & model router are you using ?
2. Who is your ISP ?
3. Post the output from **ipconfig /all** in Windows here please.
Web links to 1&2 above would help.

Post the complete output to **route -n** here as the rest of the info is important.

---

### Post by bscbrit on 2006-01-15
Mips

Good point!

It must be getting late!

---

### Post by mips on 2006-01-15
[QUOTE=bscbrit]

...
It must be getting late![/QUOTE]

Now that you mention it I think it is time for me to go sleep.....ZZZzzzzz ;)

---

### Post by Ingla on 2006-01-15
Hi.

Results for ipconfig: Command not found.

Results for route -n:

Destination     Gateway     Genmark              Flags    Metric    RX    Use Iface
82.80.47.1      0.0.0.0       255.255.255.255   UH        0          0     0      ppp0
10.0.0.0         0.0.0.0       255.0.0.0              U         0          0     0      eth0
0.0.0.0          10.0.0.138   0.0.0.0                UG         0         0     0      eth0

Ethernet Controller  VIA Technologies VT6102 (Rhine II)
[http://www.vntek.com/en/products/velocity/vt6120/](http://www.vntek.com/en/products/velocity/vt6120/)

ISP Bezeq International 
Very hard to find info in English. Some information at:
[http://www.bezeqint.co.il/bi13_english/bin/en.jsp?enPage=BIFront](http://www.bezeqint.co.il/bi13_english/bin/en.jsp?enPage=BIFront)
[http://www.bezeq.co.il/Cultures/en-US/WOW/Support/Support/Definitions-Macintosh.htm?LinkType=posting](http://www.bezeq.co.il/Cultures/en-US/WOW/Support/Support/Definitions-Macintosh.htm?LinkType=posting) (says to use 10.200.1.1 for IP on MAC)

Note: The first line in the route -n output (apparently my IP) was not there before. Still can't connect to anything, though.

Thanks.

---

### Post by mips on 2006-01-15
You still have not told me what router you are using.

In the mean time look at this post by a fellow countryman, he uses the same ISP.
[http://ubuntuforums.org/showthread.php?t=95431](http://ubuntuforums.org/showthread.php?t=95431)

...I'm still not in bed 8-[

---

### Post by Ingla on 2006-01-15
Aztech ADSL2+ Ethernet Bridge Router DSL-600E

---

### Post by Ingla on 2006-01-15
Some router info at:
[http://66.249.93.104/custom?q=cache:ACJSIvr29lUJ:www.aztech.com/brochure/ADSL-Family-Brochure.pdf+Aztech+ADSL2%2B+Ethernet+Bridge+Router+DSL-600E&hl=en&ie=UTF-8](http://66.249.93.104/custom?q=cache:ACJSIvr29lUJ:www.aztech.com/brochure/ADSL-Family-Brochure.pdf+Aztech+ADSL2%2B+Ethernet+Bridge+Router+DSL-600E&hl=en&ie=UTF-8)
Not sure how helpful.

Thanks.

---

### Post by Ingla on 2006-01-16
Hi.

Without dropping the current discussion, can someone tell me the correct way to try to connect immediately after installing Ubuntu? People here are saying there's no need to deal with pppoe. Is pppoeconf NOT the correct starting point?

I think it's important that I understand this thoroughly. I have Ubuntu on another disk, which connects OK via my USB modem. The disk is old and beginning to make threatening noises, so I wanted to Ghost it to a new hard drive before it dies. I had installed and configured so much stuff that I didn't want to start over. Then I decided that's not the way to go. I'd better know how to do all this from scratch, as easily as I can in Windows.

So, I'd appreciate a step by step walk through. If you had just installed Ubuntu, how would you get connected? What do you run, how do you configure everything and what commands will start/stop the connection, etc.?

Meanwhile, I hope someone can make some sense of all the information I sent and help get this installation online.

Thanks very much.

---

### Post by bscbrit on 2006-01-16
Ingla
The confusion has arisen because you are not clear which method of connection you wish to use.  If I have read the advertising blurb regarding your modem correctly, it can be connected either by USB or by ethernet.  Which one are you trying to use. Usually ethernet connection is the easiest to achieve but USB is also possible although it can provide additional problems.  Which would you like to attempt?

This is why, I presume, mips wanted to know more about your modem.  Don't forget, until you tell us what you have we are all in the dark. Now that we know, we can try to find the manufacturers manual and look at what is recommended.

---

### Post by Ingla on 2006-01-17
Hi.

Using Ethernet connection. I have a USB modem (not the Aztech). But this one is in the Ethrnet card...not USB. I stated in the original post that I was trying to connect via ethernet, but sometimes these things get lost or forgotten in the thread.

I have another disk with Ubuntu, connected via the USB modem. It won't work for some reason on this installation. Anyway, it's quite another matter to use USB on Linux...lots of configuring (and hoping). Also, a bit unstable.

By the way, can you help with my last "side" question, i.e. what's the "normal" procedure to connect with a new Ubuntu installation (via ethernet)...pppoeconf, or what?

Thanks very much.

---

### Post by bscbrit on 2006-01-17
If you are using the ethernet connection you do _not_ need pppoe.

My ADSL modem uses PPPoA encapsulation, but all the settings are made _manually_ in about 1 minute.

According to the manufacturer's blurb, connect your modem to the telephone/ADSL line using the RJ11 connectors.

When you power up the modem you should have a steady green light on the modem, i.e. not blinking.

Connect your computer ethernet connection to the ethernet connection on the modem.  

Set your NIC to either DHCP, or give it a dedicated IP (e.g. 10.0.0.10, with a mask of 255.0.0.0). 

Using a _browser_, go to [http://10.0.0.1](http://10.0.0.1) which should enter your modem's set up page.  Enter your username and password in the appropriate places - I cannot tell you what you will see because I haven't got your modem in front of me.  There may be additional settings required but these will have been provided by your ISP - again I cannot tell you what they are because you have them and you haven't told us what you were given.

The connection should then be established.  That's probably the best that I can give you without having a copy of your user manuals and any information provided by your ISP.  Without your modem or knowledge of your specific model I cannot provide any more.

If you have a problem, make a note of exactly what you see (a screen shot is invaluable) and any error messages that might appear.  Also describe what each of the LEDs does/is doing, and then come here with the information and your specific questions.  

Good Luck

EDIT According to the manufacturer's page, your model of modem should have _both_ ethernet and USB.  At least thats what their web site indicates.

---

### Post by bscbrit on 2006-01-17
[http://ubuntuforums.org/showthread.php?t=106847](http://ubuntuforums.org/showthread.php?t=106847)

Also see this link on this forum for previous successful attempts at setting up your model of modem.

---

### Post by bscbrit on 2006-01-17
There might be more useful information on this site:

[http://www.dslreports.com/gs/dsl600e?cat=remark](http://www.dslreports.com/gs/dsl600e?cat=remark)

---

### Post by bscbrit on 2006-01-17
[DELETED - wrong thread!]

---

### Post by Ingla on 2006-01-17
[QUOTE=bscbrit]There may be additional settings required but these will have been provided by your ISP - again I cannot tell you what they are because you have them and you haven't told us what you were given...

The connection should then be established.  That's probably the best that I can give you without having a copy of your user manuals and any information provided by your ISP.  Without your modem or knowledge of your specific model I cannot provide any more.



EDIT According to the manufacturer's page, your model of modem should have _both_ ethernet and USB.  At least thats what their web site indicates.[/QUOTE]

Hi.

Thanks for all your time.

I'm not sure what other information you need. In previous posts, I've given the modem name and model. I know the DNS servers. Also, I've mentioned that it is plugged into the ethernet card...not USB. All this is beyond a doubt, as is the physical integrity of the system and the connection. I have two modems connected...one USB and one ethernet. So, nothing can be in the wrong place (there's only one ethernet connection on the machine). On Windows, I can connect using either one I want by simply plugging the phone adsl line into the modem of choice (there's only one line, so it can only be in one modem/router at a time), and connecting with the appropriate dialup interface.

The ISP gives this modem out free. As is their custom, they provide very little documentation of any use...mostly how to plug the phone line in and run the driver installation from their disk. I didn't need to be told any of that. The only hitch was that the USB modem dials a number (8,48) and there was no number to give the ethernet router. Their Support told me to type "adsl" instead of a number and that was it...connected.

My ISP does not support Linux. That means, go ahead and use it but don't ask us for help. I had to ask specifically for things I needed to configure the USB modem, such as protocols, DNS name servers and the like. They won't help with Linux but will answer specific questions like these, of course. Most of them don't even know anything about the OS...they're very good, but only for Windows.

Linux seems to have and identify the driver. As, we corresponded the other day, it seemed to become clear that everything is OK and that we're getting down to a problem of configuation or software. 

As far as software goes, I have some suspicions about the Ubuntu installation itself. I don't know why, but it won't run my USB modem (cannot synchronize...gives error notice about glibc double entered or corrupt). My other Ubuntu disk connects with it fine. Same Ubuntu installation CD, same modem driver, same modem configuration (double checked a number of times).

 I've also re-installed Ubuntu from scratch on the new disk (several times). Maybe some kind of incompatibilty with the hard disk (Samsung)? I tried to install Ubuntu on a HD with ATA support. The installation went fine, but I couldn't boot in. Got a message "GRUB read error". I tried the installation twice with the same results.
 
I would like to continue trying before formatting the disk again. I don't find that that helps anything anyway.

I didn't know I could configure it from the browser. I'll see what that does. Is that what you're supposed to start with after installating Ubuntu (assuming you've set the connection for DHCP and activated it and edited the DNS nameservers)?

What about a "connect" command??

Any ideas welcome.

Thanks very much.

---

### Post by bscbrit on 2006-01-17
ingla
I'm not criticising you for not giving the information but the point that I am trying to make is that we cannot see your screen or your modem.  Therefore, if there is a setting that needs to be made and there is a prompt for it, we will not know until you tell us.  All the data that you have given is OK, but no-one can tell you where to place the data in the browser set-up page because we do not know what the browser display looks like.
I suspect that, if you go to the browser page, it will be fairly easy to work out which bit of information that you have goes in which field.  If they tell you to type 'adsl' instead of number try it, but if it doesn't work then put the values that they provided for windows in an try that instead.  There is very little to be set up in the computer; simply select DHCP and off you go.  All the configuration appears to be in the modem and there is no much that anyone on this forum can suggest because what you are looking for is modem-specific and not ubuntu-specific. (Unless another Ubuntu user has the same modem and can offer additional help?).  So the best that I can suggest is that you try to set it up using the browser and, if that does not work, try to come back with enough information so that someone here can make an intelligent guess as to what it next needed to make the modem function.
I sympathise with the 'free modem but no support' problem - I had the same experience once and changed to an ethernet ADSL modem - DSL504.  It also has an http page set-up but it was really fairly intuitive to set up and works a dream.  It is unlikely that you can break anything by inputting the wrong values while trying to connect - you will either connect or you won't.  Give it your best shot and come back and let us know how you get on.

---

### Post by bscbrit on 2006-01-17
Regarding the unusual glibc error messages, check Synaptic for broken packages and repair if neccessary.  Presumably the only packages that you have installed are from the CD, and therefore you don't need the internet to repair them.

---

### Post by Ingla on 2006-01-17
Thank you.

Can you tell me how to take a screen shot in Ubuntu? Does the "Print Screen" button do it? I can probably do something with that (if I can figure out The Gimp or some other application to manipulate it a bit). Do you have a suggestion as to what Ubuntu program I should open it in. All this is a piece of cake in Windows...I've simply never tried it on Linux and should know how before I go over to Ubuntu and lose online contact for a while.

Anyway, I'll have to put it on a disk, get back to Windows, and send it along.

Thanks for everything.

---

### Post by bscbrit on 2006-01-18
System - Take Screenshot

Sorry if my replies are sometimes slow - I am having great difficulty using this forum at the moment.  The website appears to be down quite often, or at least my attempts at connecting to the site are being refused.

---

### Post by Ingla on 2006-01-18
Thanks. 

It's not you. I am having periodic trouble using the site also. Server trouble? Too many users?

As a matter of fact it's showing I'm offline when I'm right here and logged in. On the home page, it says the forum is closed to posts but it lets me post replies.

By the way (just curious) is there any explanation of the designations they give people, like how many cups of Ubuntu and that sort of stuff? X beans = 1 cup?

Thanks for your help.

---

### Post by bscbrit on 2006-01-18
The system of allocating coffee beans, cups and accolades appears to have changed since the New Year - I still haven't quite figured out the meanings or progression of the images or titles! Can't say that I've paid it too much attention though :p

---

### Post by Ingla on 2006-01-19
Wow. I've been trying to get back on this forum. It's inaccessable a lot of the time. I hope somebody can get this sorted out.

Anyway, NEWS: I got connected on the new Ubuntu disk. However, there's still a big problem.

Let me try to summarize the situation.

I have two modems connected to the machine, one USB and one Ethernet. Each is plugged into the computer in the appropriate place. I simply have to move the telephone adsl line to the modem I want to use.

I have Windows running on one hard drive. There are two standard Windows connection interfaces...one for the USB and one for Ethernet. I hit Start>Connect to> whichever one I want (at least until last night).

I have a working Ubuntu installation, which I've had for some time. It connects quite happily via the USB modem and all is well. But it's an old hard drive which has begun to rattle and shake. Being afraid it was about to pass on to Cyber Heaven, I decided to install Ubuntu on a newer hard disk. Lets call the old one Ubuntu1.

We'll call the new installation Ubuntu2. This is the one that's been giving me connection problems.

Ubuntu2 refuses to connect via the USB modem. I realize these modems can be a bit problematic under Linux, but it is exactly the same Ubuntu installation (from the same ISO), exactly the same modem driver and 100% exactly the same modem configuration. Very strange! As I mentioned, I get glibc error notices (I did check Synaptic for broken packages, but none appear. I tend to suspect that something most have gone wrong with the installation because this stuff should all be in and working "out of the box". I have a deb to install glibc, so maybe I'll try that and see what happens).

So, I tried to connect Ubuntu2 via Ethernet, which started this thread. 

I took you advice and used the browser to connect to the modem configuration (by the way, it's 10.0.0.138). I first did that on Windows and wrote down the settings. Then I went to Ubuntu2 and logged into it. There are a Quick-Start, Modem Test, Ping Test, and all kinds of helpful things in there. The modem test was fine...ping didn't work.

Checking around, I noticed that there was no user name and the number of *'s in the password field was too small. So, I entered my ISP user name and password and VOILA...connected! I immediately tried to get to this forum, but it was down for the next umpteen hours.

Going back to Windows, I found the dialup interface no longer works, but the Etherned connection goes on automatically. I just have no indication at all that I'm connected. The dialup returns an error notice that it can't connect. I don't usually like to be connected on boot, but can live with that if need be. Apparently, the ISP has this configured not to use a user name or password, but it can be used. I just don't know the connection speed because nothing shows. Anyway, I can reset the modem to default if I need to for any reason.

Back to Ubuntu2. I immediately uncommented the repositories and did apt-get update. Nothing. Can't stat any of them. So I went to Ubuntu1, did apt-get update just to check...it's fine. I copied the sources.list and put it in Ubuntu2. No good. It still can't stat anything. I have no explanation for that except that Linux has some ghosts or evil spirits!

Back on Ubuntu1, I tried the Ethernet connection. Went to modem configuration to do the quick start. It said I was already connected and showed my ISP's URL. BUT, I can't surf to anything. I double checked that it's set for DHCP, etc. Everything looks fine but no Internet.

So, there you have it. 

Ubuntu1 works with the USB modem but can't use the Ethernet (even though there must be some kind of connection as it shows my ISP's URL...before I added the username and password on Ubuntu2, I saw the screen and it had no URL...just said address unreachable).

Ubuntu2 connects fine for surfing via Ethernet (can't handle USB), but can't update anything with apt-get or Synaptic (which makes Ubuntu worthless).

The Ethernet connection on Windows has changed in unknown ways, but I still need to explore that.

Obviously, the most important problem at the moment is Ubuntu2. If it can't update, it can't be used.

I thought I'd better write all this while I'm able to connect to the forum, even though you may not be online now and I have to run anyway. Who knows if I'll be able to get in later?

Any ideas and the apt-get problem?

Thanks very much.

PS- Do you know how I can make the number eight stop making me a smiley and just show the number?

---

### Post by mips on 2006-01-19
My post came just after you posted the above update and is no longer valid.

---

### Post by mips on 2006-01-19
The dialer will no longer work as the function is being performed by the router, not a bad thing.

You can see whether you are connected in windows by keeping the ethernet adapter in the status bar. When the adsl link drops the ethernet usually drops as well.

The fact that you can surf the net is a good sign. Maybe go trough the Ethernet troubleshooting guide in this forum (sticky at the top). Post where you pick up problems. You might have DNS or IPv6 issues. Have you updated your sources file for the repositories ?

Sorry, I have to run now and will only be able to reply tonight.

---

### Post by bscbrit on 2006-01-19
Ingla,

Glad that you are now online with each installation, even if we do not know how we are achieving it!

I can only agree with Ingla yet again, find out where you have problems and come back with specific information and we will try to resolve them.

I understand your comments regarding not knowing whether you are online or not - but if you are ADSL does it really matter?  The act of actually logging on is not important, providing that you can get internet access whenever you need it. :razz:

---

### Post by Ingla on 2006-01-19
Thanks for the reply.

Essentially it's true...connected is connected. The problem remains now, what do I do about apt-get. I can't figure out what the issue could possibly be. If I can reach web sites by domain name, that should mean everything's fine. 

But, I can't update Ubuntu2. As mentioned previously, I copied in the exact same repository list I had just used 5 minutes previously on Ubuntu1. This is crazy!

Any ideas? I'm out of them.

Thanks a lot.

---

### Post by mips on 2006-01-19
Check out your DNS settings.

---

