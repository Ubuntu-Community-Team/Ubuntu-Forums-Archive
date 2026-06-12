---
title: "LAN Internet Trouble"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by amikhal on 2007-04-17
I am pretty much completely new to Linux, Ubuntu and computers in general so I apologize if this is a "no brainer" question. 

Yesterday I installed Ubuntu and when I tried to connect my dell desktop to the internet via ethernet cable it wouldnt work. I  made sure the connection worked with my laptop that runs windows and it used to work on the dell desktop when i ran windows. I was wondering if there were any settings that I need to change or programs I need to download. 

Any suggestions that you have would be greatly appreciated. Also if you need any information from me just let me know

Thanks!
Alex

---

### Post by Seisen on 2007-04-17
What is the name of your network card, it might not be supported.

---

### Post by amikhal on 2007-04-17
it is a ...


Linksys:  NC 100 network everywhere fast

is there a list of supported devices somewhere?

Thanks
~Alex

---

### Post by Seisen on 2007-04-17
Everything i found says the card should work. Type ifconfig in the terminal and post what is says.

---

### Post by louieb on 2007-04-17
System > Administration > Networking ><password> > Ethernet Connection

Check the properties try DHCP > OK > Activate.

I've thrown in just any old NIC found laying around, they have all worked.
Usually connects automatically.  This should work without any further configuration, unless you need a static IP.

---

### Post by amikhal on 2007-04-20
DHCP was the default setting and it obviously wasnt working, any other suggestions?

---

### Post by chemtut on 2007-04-20
Make sure that the ethernet connector is plugged in at boot!
mine never works when plugged in afterwards , but always does when plugged in at boot
good luck

---

### Post by amikhal on 2007-04-20
Nope that definitely didnt work either, I am about to lose all hope for using LINUX, Does anyone else have any suggestions?

I honestly think I have tried everything, but hopefull someone will have something I havent tried yet.


~Alex

---

### Post by altaaa on 2007-04-20
I'm gonna go with Seisen,

open up a terminal (Applications > Accessories > Terminal) and type this in:

```
ifconfig
```

Post your results here

---

### Post by amikhal on 2007-04-20
when I type ipconfig in it says...

"bash:ipconfig:command not found"

---

### Post by amikhal on 2007-04-20
Sorry I figured it out when i typed ifconfig it gave me...

eth0      Link encap:Ethernet  HWaddr 00:04:5A:6B:A4:59  
          inet6 addr: fe80::204:5aff:fe6b:a459/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1702 (1.6 KiB)  TX bytes:7092 (6.9 KiB)
          Interrupt:11 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15620 (15.2 KiB)  TX bytes:15620 (15.2 KiB)

So i pretty much have no idea what all this  means... any help?

Thank you so much for taking the time to help me out!

---

### Post by altaaa on 2007-04-20
try [SIZE="4"]**ifconfig**[/SIZE]

---

### Post by amikhal on 2007-04-20
see above

---

### Post by altaaa on 2007-04-20
Yeah, I saw it :)

type lspci, check what it says on the line that starts with "Ethernet controller"; post that here.

And this is also a nice test:

1. unplug the cable
2. type: sudo dhclient eth0
3. plugin cable
4. watch the output

Get back to me with more info :)

---

### Post by amikhal on 2007-04-20
Linksys NC100 Network Everywhere Fast Ethernet 10/100

At the end of the second test it said...

No DHCPOFFERS received.
No working leases in persistent database -  sleeping

---

### Post by steve.horsley on 2007-04-20
I see that eth0 is RUNNING, which means the cable is plugged in and working. I also see both transmitted and received packets, which is good. 
You could try this command, just in case DHCP failed first time for some odd reason:
**sudo dhclient eth0**
and post the result here if it doesn't work. This command asks for a DHCP server to allocate us an IP address.


I would add to that a request for the output of the command **ipconfig** in the windows command prompt, so we can see how windows is working and compare the two. This would be a good start to knowing what's going wrong. 

Also, how are you trying to "connect to" your dell desktop? Can you ping it, even? Actually, if you can ping the desktop then the requests for ifconfig and ipconfig are probably not needed and we can go on to looking at the application you are trying to connect with.

---

### Post by amikhal on 2007-04-20
Sorry you will have to forgive my utter lack of computing knowledge here, but hopefully this answers some of your questions...

I am only running Linux on my Dell Desktop, I am accessing the internet from my laptop that runs XP. I dont know if this means anything, but I ran IPconfig in Windows and it gave me the values for my ip address, subnet mask, gateway etc.. I tried plugging those values into the dell desktop as a static IP and that did not work either. Frankly I had this dell sitting around and figured it would be fun to put Ubuntu on it and just start a new hobby. I just wish I could figure out how to get on the internet.

As for the "Ping" I have no clue what that means or how to do it so if that may lead to a solution I would love to be walked through it. 

As for the network in my house, I am running a wireless network, but I plugged my ethernet cable from the desktop into the back of the router, I assume that works because I have done it on my laptop before.

Thanks for all your help, hope we can figure this out!

PS in my previous post i stated the output from the sudo dhclient eth0 test

---

### Post by altaaa on 2007-04-20
Do you have some kind of MAC address filtering going on in your router? That would explain why your laptop isn't getting an ip address. 

Are you sure your laptop network card is functioning? Have you been able to use it (maybe at another location?)

---

### Post by amikhal on 2007-04-20
I dont believe there is any mac address filtering. My IBM laptop's wireless internet works just fine at home and any other netwrok i try to connect to. I am just trying to get my Dell desktop runnign ubuntu to connect to the internet.

---

### Post by altaaa on 2007-04-20
Sorry, got your two computers mixed up...

if you check the backside of your computer, where the ethernet cable connects to your network card, do you see LEDs (they're mostly green or yellow) burning/blinking on the network card?

---

### Post by amikhal on 2007-04-20
sure do....
 two of them both solid
the top one is yellow says "100" next to it
 the bottom one is green says "Link/Act' nex to it

---

### Post by altaaa on 2007-04-20
Strange. Everything looks all right, but somehow you don't get an IP from your DHCP server. When you tested it with your laptop, did you use the exact same ethernet cable?

---

### Post by n3tfury on 2007-04-20
erm.... i don't think the activity light is supposed to be solid.  it should be flashing for normal network activity.  yellow indicates excessive traffic.  i'm wondering if that router is set up for dchp in the first place.

---

### Post by altaaa on 2007-04-20
It is both used for link and activity. So it is supposed to be solid and blink only when there is any activity.

---

### Post by amikhal on 2007-04-20
When I tested it with my laptop I pulled it straight out of the desktop and plugged it right in, making sure to disable my wireless netwrok adapter. Is it possible that there is not enough bandwidth to support all the computers on the network (My laptop and 2 others)?

---

### Post by altaaa on 2007-04-20
Nah, the bandwidth used for assigning IP addresses (called DHCP) is very limited...

I'm running out of options here to help you, the last thing I would do is to replace the network card to see if that works. Wouldn't be surprised...

---

### Post by amikhal on 2007-04-20
well i appreciate all the help, ill get back to you if i change the network card. If yall can thin kof anythign else get back to me I would love to figure this out, but thanks for eveyones input!

---

### Post by amikhal on 2007-04-20
By the way any suggestions on Network Cards that will work with ease?

---

### Post by altaaa on 2007-04-20
Not really, I've never seen a network card that didn't work by default... I think almost any PCI card will do.

---

### Post by blue_screen0x0 on 2007-04-21
try ifconfig, instead of ipconfig

---

### Post by medad on 2007-04-21
I was thinking through your issue and I was wondering about a couple of things.  Which version of Ubuntu are you running?  Have you tried to see if you can connect to the system via update manager or synaptic package manager and run reload to see if the system connects to update the info?   Just a couple of thoughts...

---

### Post by steve.horsley on 2007-04-21
The ifconfig shows both transmitted and received packets, so the card is recognised and the driver is almost certainly working correctly. The questions remaining are:

1) How should the PC be configured? DHCP or static IP? Look at the Windows configuration to find out, since Windows on the same PC allegedly works.

2) What application is wanted once IP is working?

---

