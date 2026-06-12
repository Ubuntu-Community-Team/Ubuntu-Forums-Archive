---
title: "DSL network issue - Light not on"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by ed-koala on 2007-10-09
I have a duel boot machine, Win XP on one drive, Ubuntu on the other.  WinXP boots fine, and my DSL network modem light comes on and the internet works.  When I switch to Ubuntu, the network light goes out on XP shutdown and does not come back on for Ubuntu.

I have a Realtek 10/100 network card (or maybe it's in the motherboard). I check ifconfig and see that eth0 is there, and my 8139too driver is installed.

I cannot ping the modem tho, and naturally the internet is not working either.  Anyone have any ideas on what is going on, and how to get that modem network light on?

---

### Post by mridkash on 2007-10-09
Can you please tell which light is not turning on, is it the link light or the LAN light.
From what you've said, I think it is the LAN light, ie your computer couldn't connect to the modem. Then, maybe its a driver or hardware issue.

I dont know about your modem but on mine the link light turns on even when the computer is switched off ie it shows that the modem has successfully connected to the ISP.

---

### Post by ed-koala on 2007-10-09
The light is the network light, LAN.  I've found a workaround tho ... if I open my WinXP64, and then reboot without shutting down windows, the light stays on and Ubuntu works fine.

I'm assuming this is actually a Win64 issue, but it's strange that the NIC can't see the modem after Windows shuts down.  I'll check Windows forums and see if there's any help on this.

---

