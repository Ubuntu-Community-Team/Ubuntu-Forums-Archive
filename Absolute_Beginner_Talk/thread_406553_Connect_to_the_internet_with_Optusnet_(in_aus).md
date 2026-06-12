---
title: "Connect to the internet with Optusnet (in aus)"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Jellystapler on 2007-04-11
Hey everyone, 

Originally i was having some trouble connecting to the internet using ubuntu and optusnet (in Australia).  
You cant use "dhcp" to automatically get your ip address from the dns server, because, i don't know, probably a few different reasons. which i will list now:

1. Linux isnt supported
2. Optusnet and M$ are in bed
3. Optusnet and Apple are in bed

Who knows?

Anyways, to solve this, the network settings for your Ethernet card must be set to static ip, and then set your:

Ip Address: 10.1.1.2
Subnet mask: 255.255.255.0
gateway address: 10.1.1.1

Click on the DNS tab at the top, and ensure that the dns server is set to "10.1.1.1".

It should connect automatically.

---

### Post by andrew.46 on 2007-04-14
Hi,

 What sort of Modem / Router do you use, do you have a D-Link?

I connect to AAPT in Australia with no hassles at all using DHCP.  But the best thing I ever did was to turf the D-Link 502T that came with the package and bought a Speetouch 585 = no more network configuration problems.

                     Andrew

---

### Post by antoz on 2007-04-14
I am with Optusnet, and a D-Link  Modem Ubuntu had no problem finding the connection.

---

### Post by Jellystapler on 2007-04-21
i think the problem is/was because i am using the speedstream modem. (i think thats made by siemens)

---

### Post by andrew.46 on 2007-04-21
Hi,

 I read your message with interest:

> **antoz said:**
> I am with Optusnet, and a D-Link  Modem Ubuntu had no problem finding the connection.

 but I have not been clear in my previous statement: the problem lay more with Ubuntu linux connecting to the D-Link modem / router; there was no problem from the router to my ISP.

                   Andrew

---

### Post by STREETURCHINE on 2007-04-21
> **andrew.46 said:**
> Hi,

 I read your message with interest:



 but I have not been clear in my previous statement: the problem lay more with Ubuntu linux connecting to the D-Link modem / router; there was no problem from the router to my ISP.

                   Andrew

i also connect to optus net through a skyedge modem and a dlink router,ubuntu connected straight away.
and dhcp was no drama

---

### Post by Jason Weiss on 2007-05-07
Help please don't make me a liar I really need your help
I convinced my friends to swap to Ubntu but now their optusnet will not work 

After I told them tht they will have no problems with ubuntu, and they were foolish for using windows.

when they asked me about hardware I said nothing is imposible with linux 

I am connecting via ethernet and I am using one of those crappy speedstream 4200 modems 

I followed the instuctions above, but I keep having the same problems: when modem is first connected the ip address looks fine, ie :10.1.1.2 but when the adsl tries to connect, it changes the ip to 58.something. 

If i leave the phone line disconected the ip stays at 10.1.1.2.

Some one out there must be using one of these modems succsesfully?

Please help me quickly.  I am so desperate, my friends are about to cross back to the darkside

---

### Post by ashenphoenix on 2007-09-15
Heya, don't stress.

For some reason, the Speedstream modem works better if you switch off DHCP on the connected computer or hub, and assign it the Fixed IP address of 10.1.1.3

Worked for me, prior to then I had to do a complcated boot sequence of unplugging the modem, letting it boot onto the network, and then playing a tango (seriously don't try this).

I just gave up, assigned the fixed IP address to the hub, and so there's now a kind of invisible network between the hub and the modem, and it works fine.

It's just that the speedstream modems are retarded, not that there's an anti-linux sentiment on Optus' part - hell, they even mirror the Ubuntu CDs on their own servers.

---

### Post by coolen on 2007-09-15
Have you checked your router to make sure that DHCP's turned on?
I doubt it's a problem with Optusnet...I use a derivative, with a D-Link router, and other than the fact that the router sucks, I have no issues. Router-compy works perfectly.

---

