---
title: "Crossover Network, XP and Ubuntu..HELP!"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by shwagpo on 2007-08-14
Okay, if you've been reading my thread "A few questions before I make the plunge," you may already know what is going on.

Anyways, I cant access the net with my linux box because I have an incompatable WINmodem (Broadcom BCM 4212 v.90).  Now, I went out and got a Crossover Cable, and am attempting to link the two together through it, on machine is a Dell with XP, the other has Feisty Fawn.

Now, to start, I am initiating with the XP computer, and it wont read that I have the networking cable plugged in, am I doing something wrong already?  Can anyone advise me or give me a step by step?

---

### Post by xpod on 2007-08-14
[http://www.annoyances.org/exec/show/ics_xp](http://www.annoyances.org/exec/show/ics_xp)

I do a similar thing using an Ubuntu machine as the gateway/router but i`m not sure how that modem of yours comes into the equation doing things the opposite way i`m afraid.

I have a cable modem using the first nic but need a second nic in the same machine for the ics to other pc.s.You probably dont need the two nic`s i`m assuming but dont quote me on that ok.

EDIT:Would`nt a proper router of some sort not solve your problem??

---

### Post by toidi on 2007-08-14
Can you share with us a little info on how your xp computer accesses the web?
ie. does it have two nic cards (perhaps one wireless one wired).
Does it access the net through a usb modem or cable modem?

Also your xp machine will not detect the network connection to the linux box is due to it being a xover cable.

How I used to do it when I was using two xp machines and a cable modem a few years ago.

Nic 1: Internet connection (left that on auto detect in windows xp).

Nic 2: xover manually set the ip to 192.168.2.1 with a subnet of 255.255.255.0

Nic 3: second box set the ip to 192.168.2.2 subnet 255.255.255.0 dns server 192.168.2.1 and gateway to 192.168.2.1 
Also made sure that Internet connection sharing was enabled in winxp machine.

Hope this helps.

---

### Post by shwagpo on 2007-08-14
Okay, here goes.  I am currently running dialup on my XP machine(all I have access to in the middle of nowhere here in Iowa).  I have a crossover cable, and a network card in each computer.  And that's about it, I was told a few times I could make it work with just what I've got, but I am(once again) lost.

---

### Post by shwagpo on 2007-08-14
Okay, how do I change the settings(IP and gateway) on the machines manually?

---

### Post by xpod on 2007-08-14
System>administration>network. :)

EDIT:for XP you have to right click your network connection,then properties,then click on the internet protocol(tcp/ip) entry then it`s properties.....

It`s all explained in that link i posted i believe.

---

### Post by shwagpo on 2007-08-14
Okay, I found out how to change my IP on the Lunix Box(windows box is pretty much set...), now how do I change/input the subnet?  Do I need to input the DNS as the IP of the XP box?

---

### Post by toidi on 2007-08-14
[http://www.practicallynetworked.com/sharing/](http://www.practicallynetworked.com/sharing/)

Lots and lots of stuff on there on how to setup your network.

Edit: just seen your post.  Run the ICS (internet connection sharing) wizard on your xp box.

Choose the option something like 'This computer connects directly to the network'  'Other computers connect through this computers internet connection'

You may have to change a few settings manually later, but that will get ics up and running on your xp box (if it is not already).

---

### Post by PCFascist on 2007-08-14
Searching google I noticed there some who have a working linux driver for you modem...

[http://osdir.com/ml/linux.linmodem/2003-07/msg00256.html](http://osdir.com/ml/linux.linmodem/2003-07/msg00256.html)

Good luck!

---

### Post by shwagpo on 2007-08-14
Okay, and I am now an idiot. 

In my network settings on the Ubuntu box, I have a modem connection listed, but no networking connection...

How do I go about finding/getting my networking card onto the list?  Can I scan for it in any way?  God I am getting flustered.

---

### Post by BoardDWorld on 2007-10-22
I have been having the same problem. I'm overseas and I finally convinced my brother back in my home country to try out Ubuntu on our mothers machine. Mum's machine was already networked with my brother's so it should be good to go right:confused: Well apparently not, unfortunately all efforts to get this running have come to and end. Is there no simple guide??

Links given here are things that are already set up in the host if the client was already connected prior to installing Ubuntu (Unless set manually which it wasn't).

Anyway it looks like XP going back on tomorrow, there isn't much changing my brothers decision.

P.S. I'm using Gutsy

---

