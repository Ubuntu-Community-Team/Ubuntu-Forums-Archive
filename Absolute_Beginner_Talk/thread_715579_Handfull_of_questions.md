---
title: "Handfull of questions"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Durden on 2008-03-05
I just recently purchased a Dell machine with Ubuntu pre-loaded. It hasn't arrived yet but I'm very anxious. For this machine I was curious what would be the best idea for a wireless networking card. Would a USB one be ideal or something else? I wasn't given an option for it when purchasing (to my dissapointment). The wireless is a must for me for many reasons I won't bore you with.

My second question is whether some issues I've had with Linux on my laptop may be resolved some time in the future. My first problem is power management. Sometimes when resuming from hibernate or suspend the machine just hangs at a black screen and never comes back. Some times when shutting down it would do the same, hanging at the black screen.

Lastly my laptop uses an alps touchpad and Ubuntu doesn't play well with it. I can get it to work as I wish by manually configure the xorg.conf but I truly don't wish to go through that every time I want to make a change. Fedora works very well with Alps, Ubuntu doesn't. Any clue if the devs are even aware of this?

---

### Post by Ianman on 2008-03-05
Hmmm to be honest I haven't really played with wireless networks in Ubuntu but I think the best option would be an internal wireless card. Perhaps from a wellknown brand like 3com?

For your other problems...I know that power management doesn't work that well. In fact there is a "brainstorm" site for Ubuntu problems that people want fixed:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Power Management is one of them.

You might even find something about your touchpad there...

Sorry I can't be of much more help.

---

### Post by TekMuzik on 2008-03-05
For wireless card I agree, any major brand should work well. I have a internal D-Link card (can't remember model right now) but it was autodetected by Ubuntu and has autoconnected to my network with no problems so far.

---

### Post by prshah on 2008-03-05
I think it's unlikely that Dell has a laptop without a wireless card. That said:

1) You can purchase a mini-pci card (specifically for laptops) but that requires some internal installation, and may require you to sacrifice the built-in modem.

2) You can use a USB WiFi dongle.

For both 1) and 2), any card with an Atheros chipset (most cheapo cards) will work out-of-the-box in (K,X)Ubuntu. I have used Compex WLP54G and NetGear WG111v2 for PCI cards and NetGear USB without problems.

Hibernation issues were a problem with 7.04 (Fiesty Fawn) , but I have faced no problems on my Toshiba P5110 with XUbuntu 7.10 (Gutsy Gibbon). Maybe you need to look into that? (version)?

HTH.
Cheers,
PRShah

---

### Post by hyper_ch on 2008-03-05
I was given a USB wifi card with my VDSL installation. It's from netopia and works in Hardy out of the box. Haven't tried it in Gutsy yet. When I'm back home I'll check which one it is exactely.

---

### Post by niteshifter on 2008-03-05
> I just recently purchased a Dell machine with Ubuntu pre-loaded. It hasn't arrived yet but I'm very anxious. For this machine I was curious what would be the best idea for a wireless networking card

I've had excellent results with the Intel 220BG and 3945ABG cards with the Intel driver. This machine (a 1420n) came Ubuntu (Gutsy) pre-loaded from Dell, I spec'd the Intel 3945 card - no wireless problems at all.

---

### Post by Durden on 2008-03-05
Thanks for all the great replies. It looks like my computer will be delivered in a few days so I'll try a 3com or Intel card and see how it goes.

Thanks for the link on power management. I guess I'll just wait and see where that goes.

---

### Post by Crafty Kisses on 2008-03-05
Mostly everything works out of the box with a pre-built Ubuntu machine. I hope you have fun and good luck. :)

---

### Post by stchman on 2008-03-05
> **Durden said:**
> I just recently purchased a Dell machine with Ubuntu pre-loaded. It hasn't arrived yet but I'm very anxious. For this machine I was curious what would be the best idea for a wireless networking card. Would a USB one be ideal or something else? I wasn't given an option for it when purchasing (to my dissapointment). The wireless is a must for me for many reasons I won't bore you with.

My second question is whether some issues I've had with Linux on my laptop may be resolved some time in the future. My first problem is power management. Sometimes when resuming from hibernate or suspend the machine just hangs at a black screen and never comes back. Some times when shutting down it would do the same, hanging at the black screen.

Lastly my laptop uses an alps touchpad and Ubuntu doesn't play well with it. I can get it to work as I wish by manually configure the xorg.conf but I truly don't wish to go through that every time I want to make a change. Fedora works very well with Alps, Ubuntu doesn't. Any clue if the devs are even aware of this?

All the Ubuntu equipped Dell LAPTOPS come with an Intel 3945 wireless card by default.  If you mean a desktop then a card based on Atheros or Intel will work fine.

---

### Post by Papa-san on 2008-03-05
Yes, I was going to pass this along... You would have had to make a big fuss over the built-in wireless card for them to have NOT put one in. Did you SPECIFICALLY request that they NOT install one? Because if you didn't, you have one in there...

The ones I just received (Inspiron 1525's) have the broadcom wireless card built right in. They came with Vista, so I have to fuss to get the dual boot Ubuntu wireless working. On the ones that have Ubuntu pre-installed, they already work out of the box. (Almost always, but that's usually a router security setting issue...)

Take another look at your order status, and in your breakdown of the system, you should see: 
1	430-2334	Intel 3945 WLAN (802.11a/g) Mini Card

EDIT:

OOPS! Yes, that is for the laptops...

---

### Post by hyper_ch on 2008-03-05
the one I got is a Netopia TER/GUSB-E - as said, it works out of the box in hardy herron... however a quick search on the net revealed that older releases (Dapper) have problems with it...

---

