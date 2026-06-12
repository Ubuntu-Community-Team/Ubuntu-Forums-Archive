---
title: "Connecting to the internet???"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by wonneil on 2006-11-25
Hi all,

I am completely new to Linux and want to try before I install.

I can start the live cd in safe graphics mode, the screen is black in normal mode??

Anyway, i want to test the internet but cannot connect when testing Ubuntu, it is showing i have wireless and ethernet, i am using ethernet at the mo but can use either.

I have to keep restarting pc to windows to connect to the internet.

I have 6.06 ubuntu, telewest broadband, my connection is from ethernet cable to router, what settings do I need to apply as I keep getting the server not found page on anything I try?

Thanks

Neil

---

### Post by adwait on 2006-11-25
In windows, do you do anything special to connect to the net? If not, have you tried the ether configuration under Administration? Perhaps the correct settings for DHCP/statis IP and DNS servers will do the trick?

---

### Post by wonneil on 2006-11-25
I don't have to do anything special, just double click on ie.

I have looked at admin tools and can't find what I need to change as I think I'm on a DHCP server? (Telewest Broadband uses a dynamic ip address)

Thanks for the quick reply!

---

### Post by tommcd on 2006-11-25
Go to system>administration>networking. Click on the option for wired connection. Click on properties, tick 'enable this connection' and set it for DHCP. That should do it.

---

### Post by MaximB on 2006-11-25
you can try in the terminal : sudo pppoeconf

---

