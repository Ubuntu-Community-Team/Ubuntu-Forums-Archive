---
title: "internet works for a second - then stops... help a newbie out?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by chriswible on 2007-12-17
Hi - if I had a nickel for every time I'd joined a forum for the first time just because I needed help... ;)

Anyway - I recently wiped out my old XP box and put Ubuntu on it. I want to use the old machine as a file server and backup machine for my Mac laptop. That's pretty much it - store audio files, etc.

I set up Ubuntu in a snap from a live cd - think its 6.06 (I'm at work) - and was amazed that the 4 hours I set aside to do it weren't needed. I had internet and everything... for about 2 minutes.

Rebooted router.

Internet.

Minute or two...

No Internet.

and so on.


I'm set up as follows (forgive me, I'm bad with networking lingo)...

cable modem
dell 2350 router (wireless & lan)
wireless to the laptop
ethernet directly to ubuntu box

set up on 192.168.42.xx (42 because I can remember it and the low numbers are reserved for work purposes).

I tried seting the ip of the router, doing dhcp, all kinds of stuff - nothing seems to keep the connection up.

In the router I find that if I clear intruder logs and repeat this process that it looks like my ubuntu box is being "caught" as an intruder... I have an allow access table - but there's stuff about MAC addresses and stuff... I don't know what a mac address is - but I viewed my network setup on my router, copied the mac address of the ubuntu machine - put that address in the allow access table and it didn't help...

I have read the networking help, scoured google, read my router help files from a-z - and I'm at a loss... what the huh?

Could someone throw me a line out here? I'm lost...

---

### Post by mellowd on 2007-12-17
For a start, a MAC address is the physical address. It's an address burned into the network card (and all network interfaces) This never changes. This is opposed to a logical address like an IP that can change. IP lives on level 3 while MAC addresses are layer 2 (It's how switches and NIC's know where to send data)

If you open up a terminal and type ifconfig you'll ne able to see your MAC address. It's a 48bit Hex number (something like F1:AD:34: etc...)

---

### Post by chriswible on 2007-12-17
Yea, I found the MAC address - nice to know what it is though - thanks! Weird looking address, but that's cool. Anyway - I've found that the level of technical knowledge among users goes way through the roof when you talk to linux folks. Please bear with me - I've set up a red hat or two and I can terminal to my server at work and stuff - but other than that a lot of this behind the screen stuff is a mystery to me....

---

### Post by mellowd on 2007-12-17
The nice thing about locking down security to a MAC address is that you can ensure no-one else can connect even if they manage to get your password. MAC's are unique so if you only give your equipment's MAC's access then no matter what no-one else can connect. Everyitime you got a new device though, even a new network card in your pc you would have to give access again to the new MAC address.

---

### Post by chriswible on 2007-12-17
Would it make sense that a mac address would change upon rebooting the router? That's what I think I saw but I could be mistaken... also - the mac address thing wouldn't explain the apparent time out of internet connectivity, would it?

---

### Post by OffAxis on 2007-12-17
So it's the router that's killing your connection?
The laptop's wireless still functions like it should?

There may be a firmware update for the router.

There should also be an option there to enable/ disable the 'Access Control' for the MAC addresses.

If you configure your router for 'Open' (No Security) you should have the most chance for successfully staying connected.

---

### Post by OffAxis on 2007-12-17
> Would it make sense that a mac address would change upon rebooting the router? 
MAC addresses don't arbitrarily change. They can be spoofed, but it takes a little bit of doing.

---

### Post by mellowd on 2007-12-17
> **chriswible said:**
> Would it make sense that a mac address would change upon rebooting the router? That's what I think I saw but I could be mistaken... also - the mac address thing wouldn't explain the apparent time out of internet connectivity, would it?

No, the MAC address will never change, unless you plug it into a new switch port or router port because remember every interface has it's own MAC. If you are using the same wired or wireless card then the MAC address will always be the same, only the logical IP will change.

As for the problem, I've seen this problem a few times in gutsy before. I had it too a while back when I was testing it on my desktop. In XP it worked fine, but in Gutsy it always disconnected so easily. I can't replicate it now because I only use linux on my server.

There are quite a few threads dealing with this in the networking section, unfortuantely I'm not 100% sure on what the fix is.

---

### Post by bcom on 2007-12-17
Ubuntu should work out of the box on a network.  If you don't understand what a MAC address, subnet mask, default gateway is, it would probably be better to let Ubuntu handle the network configuration.  

Go to System - Administration - Network and configure your network card for Automatic Configuration (DHCP).  

It is probably best to leave the router with the default configuration as well.  That is to say, IP address with something like 192.168.1.1 and subnet mask of 255.255.255.0.  

If you have to configure the router make sure you enable it to enable Local DHCP server.  This will enable to the router and the computers to take care of the network configuration.

If you change IP addresses, subnet masks, and default gateway without knowing what you are doing you will make it impossible for computers on the network to communicate with each other or the Internet.

Good luck

---

### Post by chriswible on 2007-12-17
Well ubuntu did work with the network out of the box - install, run for the first time, and poof there's google.  I don't have anything fancy set up on the router, other than changing to a 42 subnet. Wireless works fine and the wired worked without trouble on windows - same box, same wire, same everything - only change was ubuntu - and I've already enabled DHCP on the router and selected it under network on ubuntu...

so now I'm at a loss - might try reseting the router and reinstalling ubuntu to run everything at it's default... then, if I need to be on a different subnet for work I can deal with that then.... maybe - unless someone has a different idea?

---

### Post by mellowd on 2007-12-17
> **chriswible said:**
>  I don't have anything fancy set up on the router, other than changing to a 42 subnet.


I think you meant a /24 subnet?

Hmm, has it ever worked before? Did it work in Windows or any other version of linux?

---

### Post by philinux on 2007-12-17
> **chriswible said:**
> Well ubuntu did work with the network out of the box - install, run for the first time, and poof there's google.  I don't have anything fancy set up on the router, other than changing to a 42 subnet. Wireless works fine and the wired worked without trouble on windows - same box, same wire, same everything - only change was ubuntu - and I've already enabled DHCP on the router and selected it under network on ubuntu...

so now I'm at a loss - might try reseting the router and reinstalling ubuntu to run everything at it's default... then, if I need to be on a different subnet for work I can deal with that then.... maybe - unless someone has a different idea?

My wireless router worked out the box (it has wireless but pc is connected wired).

My setting is ticked "roaming" under network wired properties. That was the default.

---

### Post by chriswible on 2007-12-17
I think I did mean '42' - maybe not 'subnet' though - I thought 192.168.42.1 would be a .42 subnet.... apparently I'm mistaken?

Yes, two hours before I had XP running with a connection that never gave me trouble. There were no physical changes in configuration.

---

### Post by mellowd on 2007-12-17
> **chriswible said:**
> I think I did mean '42' - maybe not 'subnet' though - I thought 192.168.42.1 would be a .42 subnet.... apparently I'm mistaken?

Yes, two hours before I had XP running with a connection that never gave me trouble. There were no physical changes in configuration.

Generally when you talk number and subnets it refers to the subnet part. A /24 would be 255.255.255.0 subnet, while a /30 would be 255.255.255.252 and so on

---

### Post by chriswible on 2007-12-17
hmmm... that's one of those ones that'll have me waking up at 2am going "oh! I get it!"

Thanks for explaining that though - it's one of those things you either know or don't, I guess...

---

### Post by mellowd on 2007-12-18
> **chriswible said:**
> hmmm... that's one of those ones that'll have me waking up at 2am going "oh! I get it!"

Thanks for explaining that though - it's one of those things you either know or don't, I guess...

It's easy once you get your head around it, but you don't really need to know it unless you work with it (I have to work with this stuff everyday)

---

