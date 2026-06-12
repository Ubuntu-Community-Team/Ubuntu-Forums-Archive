---
title: "iwconfig changes won't register"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by blaise69 on 2007-02-12
Hi there,

I'm using a fresh install of Xubuntu 6.10 on a 30GB partition of my HDD.  I have a Broadcom wireless PCI card, that has been detected correctly by Xubuntu (lshw lists a BCMWXX driver) and I can select my wireless card and enter the connection details in Network Settings under System Settings.

However...

Although I enable my wireless card, and enter the settings 2 things are apparent.

lshw still detects the card as Disabled.
iwconfig has no settings entered, when checked in the terminal

Finally I have tried settings my ESSID and Key through the terminal with and without sudo, and again, the changes don't get registered.

A final point, although all application I've tried seem to work fine, anything that uses the net connection will crash after being opened.  Firefox didn't work at all, then when I upgraded through the package manager (with a RJ45 cable attached) firefox now opens but will close itself within a minute, the same is true for Opera.  Is this related?

Any help would be appreciated.

TIA

Blaise.

---

### Post by Trance Gemini on 2007-02-12
I suggest you edit the interfaces file at /etc/network/interfaces and make changes there

---

### Post by blaise69 on 2007-02-12
Thanks for the reply.

If I remember correctly (I'm not at my linux machine right now), the interfaces file does have the correct settings in there, which is all the more confusing as iwconfig always shows up with no values.

I think the problem is due to the card being disabled still, is there a command to activate a network interface?

---

### Post by Trance Gemini on 2007-02-13
> is there a command to activate a network interface
I think iwconfig has a key to do it, but if not, goto system->administration->network and enable it there.

---

### Post by blaise69 on 2007-02-13
I've already tried the GUI method and it just doesn't work.

Could it be a problem with it being associated with eth0?  I have an ethernet card which is eth1, I thought wireless cards were usually wlan0?

Just to recap.

My etc/network/interfaces file does have my correct settings in.
The Network settings tool does hold onto my settings.
Using iwconfig to view the settings returns blank values for ESSID and Key
Using iwconfig to manually add the settings does not work (though does not return any errors).
Enabling the card through the GUI does not work.
lshw always reports the card as DISABLED.

My machine is a 1.3GHz Athlon, 768MB RAM, Radeon 9200, PCI Broadcom chipset wifi card.

Any help or direction would be really appreciated.

---

