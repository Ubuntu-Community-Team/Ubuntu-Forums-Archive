---
title: "Wake on LAN from Windows"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2007-12-25
I have seen a number of threads about wake on lan but I cannot seem to get my system to work.

I have an Ubuntu machine and I have set the bios settings to allow it to be woken. I have then used ethtool to enable wake on lan but when I suspend the machine it will not wake up.

I am trying to wake it from an XP machine on the same network by just opening a shared drive. My thinking was that XP would kick the Ubuntu box into life by asking for the contents of the drive. (I know they can talk to each other as I have set that all up and tested it)

Should I be using something else on the XP machine or is there a problem else where?

---

### Post by popch on 2007-12-25
Have you tried waking your machine while it was powered off (as opposed to power saving or hibernating mode)?

---

### Post by Twizzle on 2007-12-28
I have tried both but I do remember reading something about my motherboard needed a min voltage from the PSU to allow this from off.

I would prefer, however, to enable it to wake from Standby and then drop back after a certain ammount of inactivity time. My reason for this is as I want it to be quickly accessable but not on all the time. I would be happy if it just came to life when I try to open a shared drive from a network machine - something I am sure I managed with Windows but can't remember how!

(On a side note - I managed to get it to wake by sending a magic packet but then Tight VNC did not work so I could not remote access it! I don't really want to use magic packets to do this)

---

### Post by popch on 2007-12-28
This is how Wake On Lan (WOL) works:
[LIST]
[*]The following conditions must be true:[LIST]
[*]Your PC's network card is equipped to wake your PC
[*]The network card as a lead connected to the WOL pin on the motherboard (if applicable)
[*]Your PC's BIOS is set to enable WOL
[*]Your PC is 'switched off' but connected to the mains (in fact, at least the network card draws a smallish amount of current because it needs to supervise the LAN)
[*]Your PC is connected to the LAN[/LIST]
[*]Then this will wake your PC[LIST]
[*]Another PC on the same LAN sends a 'magic package'[/LIST]
[*]Waking up your PC will cause[LIST]
[*]the PC to boot.[/LIST][/LIST]It is in theory not impossible that the PC also will wake from stand by mode, but I have never seen a PC which can do that. Waking the PC from hibernation mode might work as hibernating is mostly the same as powering off.

Therefore, trying to access a shared folder over the network is not going to wake your PC. The PC which wants to access the folder does not send the magic package, and only sending the magic package will wake the PC.

---

### Post by WhyWontThisWork on 2007-12-30
I'm trying to get my linux box to wake on lan, it just doesn't respond at all and I can't find the settings to check in the bios... don't most PCs come with this built in, I remember years ago having to connect a wire but I thought that was no longer needed?

---

### Post by popch on 2007-12-30
> **WhyWontThisWork said:**
> ... don't most PCs come with this built in, I remember years ago having to connect a wire but I thought that was no longer needed?

Some do and some do not come with this built in. If yours does, it has to have an entry in the BIOS. Look for 'wake up' and 'WOL'. Also try and look up the specifications of your PC at the manufacturer's site or in the documentation that came with your PC.

---

