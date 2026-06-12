---
title: "Verizon DSL Connection"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Mojave1 on 2007-07-14
Hi, I have Verizon DSL and I'm unable to get on the Internet with Ubuntu 7.04. I'm new to Ubuntu... I've searched the internet and this forum and haven't found a thread that helps me with this.

Verizon DSL is up and running fine - I'm on it now.
I'm using an ActionTec GT704WG modem using the RJ-45 LAN Port.

My IP address is: 192.168.1.65
Subnet Mask is: 255.255.255.0

Also, Ubuntu doesn't like my video, which causes the computer to lock up. It's an onboard Nvidia chipset 7025 (Mothboard Biostar TF7025-M2 with an AMD 5600+). It runs fine in safemode so really not a burning issue at the moment.

I'm an old DOS guy, but I have no idea what I'm doing with regard to the command lines in Ubuntu. I'm willing to learn... I'm put off by Vista, thinking it should do something besides hogging resources and playing Cop, I hate reregistering my windows (reinstalls) just because the stupid OS degrades over time. Figured I'd try migrating to Ubuntu over time; moving away from XP when microsoft quits supporting it. So now, the learning curve...

Sorry, I'm sure these dumb questions come up 15 times a day. Thanks in advance.

---

### Post by starcraft.man on 2007-07-14
> **Mojave1 said:**
> Hi, I have Verizon DSL and I'm unable to get on the Internet with Ubuntu 7.04. I'm new to Ubuntu... I've searched the internet and this forum and haven't found a thread that helps me with this.

Verizon DSL is up and running fine - I'm on it now.
I'm using an ActionTec GT704WG modem using the RJ-45 LAN Port.

My IP address is: 192.168.1.65
Subnet Mask is: 255.255.255.0


I'm confused... you still having problem's with the Verizon DSL? Since you mentioned it's a standard RJ 45 you shouldn't have any trouble connecting it to the box when in Ubuntu and getting DHCP to hand out an IP and automatically configure.

> Also, Ubuntu doesn't like my video, which causes the computer to lock up. It's an onboard Nvidia chipset 7025 (Mothboard Biostar TF7025-M2 with an AMD 5600+). It runs fine in safemode so really not a burning issue at the moment.

Sorry, I'm not much good with motherboard video...

> I'm an old DOS guy, but I have no idea what I'm doing with regard to the command lines in Ubuntu. I'm willing to learn... I'm put off by Vista, thinking it should do something besides hogging resources and playing Cop, I hate reregistering my windows (reinstalls) just because the stupid OS degrades over time. Figured I'd try migrating to Ubuntu over time; moving away from XP when microsoft quits supporting it. So now, the learning curve...


Hey well I'm equally an old DOS Guy :D. Perfect timing. For understanding how to install anything in Ubuntu, see my blue link in my sig (just posted my guide yesterday). The orange one will take you to a command line tutorial for Ubuntu, learning the shell is the important section (go to the blue one first and read along till you get to the bits I hand off to linux command, read those and come back to the guide and continue. I structured the blue guide with no pre-existing experience required to understand.). The two combined should teach ya everything ya need for daily working with Ubuntu. The two links on the right will answer common questions and help you find programs respectively.

> Sorry, I'm sure these dumb questions come up 15 times a day. Thanks in advance.

There are no dumb questions. Just set some time aside and read the few guides I pointed ya to, you'll pick up fast I think :).

---

### Post by Mojave1 on 2007-07-14
Sorry, I meant the DSL is working fine w/ XP. Meaning my account is setup.

Yes, I read your sticky post instructions last night. Very useful, I'll be relying on them once I figure out the internet connection problem. Thanks again!

---

### Post by starcraft.man on 2007-07-14
> **Mojave1 said:**
> Sorry, I meant the DSL is working fine w/ XP. Meaning my account is setup.

Yes, I read your sticky post instructions last night. Very useful, I'll be relying on them once I figure out the internet connection problem. Thanks again!

Hmmm, so you plug in the DSL Ethernet line and it doesn't automatically connect on Ubuntu? I can only think it's an unsupported feature of the motherboard... ethernet works perfectly and automatically from all of my experiences. I did a quick google and found a few folks saying this on a few review sites:

> Ubuntu 7.04 has no drivers for the network port. I had to disable it and install an old NIC card in order to get it working.

Your best bet might be to find a cheap networking PCI card and use that. I'm afraid apart from that I can't offer any other advice, mobos aren't something I know huge amounts on.

---

### Post by Warren Watts on 2007-07-14
> **Mojave1 said:**
> Verizon DSL is up and running fine - I'm on it now.
I'm using an ActionTec GT704WG modem using the RJ-45 LAN Port.

My IP address is: 192.168.1.65
Subnet Mask is: 255.255.255.0



I used to be a Verizon DSL Online CSR, but it's been a while and I am a little rusty...

From your IP, I can see you have a good connection to your modem because it gave you a local IP.

What you need to do is configure your PPPoE connection on the modem itself.  To do this, enter the modem's IP into the address bar of your browser.  If I remember right, it is 192.168.0.1 or 192.168.1.1 If one doesn't work, try the other.

This will bring up the modem setup screen.  

If you get a screen asking you to enter the modem administration username/password, try leaving both fields blank, or entering admin as the username and leaving the password blank.

You should be able to set up or reconfigure your PPPoE from the menus that follow.

Enter your Verizon email address WITHOUT the @blah.foo for the username
Enter your Verizon password as the password

Like I said, I'm a bit rusty but I hope this helps!

---

### Post by Mojave1 on 2007-07-14
The 192.168.1.1 did not work from within Ubuntu (firefox) but it does work from within XP (internet explorer). From within XP I did not follow the rest of the directions i.e. entering password etc?

Now I'm begining to wonder if:

1) Ubuntu is finding my modem?
2) If Firefox is adding the http\\ bit before the address, thus stopping the hardware from recoginizing the address?

Thanks, that was useful information.

---

### Post by covertLuv on 2007-09-13
I think this is an issue with your wireless card.  It is probably a broadcom based card.  This is a known issue. Try searching "Broadcom 43xx based wireless cards the EASY way" for one possible solution.  

If it is a broadcom card then this is a known issue.  So do some searches for a solution in the forums.  You may find something that works for you.  Your mileage will vary...

---

