---
title: "Installing hardware in Xubuntu"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by drahmad on 2007-01-23
Sorry but I'm new to this. I have an old laptop that I successfully managed to install Xubuntu onto (yah!!).

As a Windows/OS X user, I'm completely unfamiliar with Linux and can't work out how to install new hardware properly.

I have a "no brand" PCMCIA 10/100 network card which I can download Linux drivers for if required. But where to start?

In Windows I would go to Control Panel - Add/Remove Hardware. But what to do in Linux?

I tried "plugging and playing" (not sure if that was wise), by plugging it in and powering on. The card seems to be recognised - I got no error messages - and in Applications/System/Networking, I have a "Wired Connection" option, which I set to DHCP. I have no idea if this is properly installed, but the activity lights DO work, but Firefox can't find a connection (it is set, as by default, to Direct Connection to the Internet).

Finally on another note, I was expecting Xubuntu to install Open Office, but instead I have Gnumeric (which it won't let me uninstall in "Add/Remove"), and Abidword. Does Xubuntu install different software to Ubuntu?

Thanks!

---

### Post by sardion on 2007-01-23
You should be able to plug and play that card with no problem.  Can you open a terminal and type "ifconfig" and post the output, that should help to figure out what's wrong.

As to the gnumeric thing, yes xubuntu installs less than ubuntu because it is lightweight.  But, you can always install openoffice.org from the repos (once the network is working).  I run OO on xubuntu, there's no problem there.

---

### Post by drahmad on 2007-01-24
Thank you for your reply.

Here is the output:

lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0b) TX bytes:0 (0.0b)

I also tried ping to my router (ping x.x.x.x - not sure if that's the correct command), and it says connect: Network is unreachable

I also tried pointing firefox to my router IP but again no luck.


For future reference, how do I install hardware in Linux? Do I just plug it in and reboot? If drivers are required, will I be prompted, and if so what is the process? Will I just be guided through?

Is there any way of bringing up a "Device Manager" type of list of installed hardware on the machine? And can I "uninstall" hardware for the purpose of removing it? Or do I just "hot-remove" the PCMCIA card?

---

### Post by 3rdalbum on 2007-01-24
In the "Networking" panel, you may need to put your DNS server addresses in. You can usually find out what they are from your ISP's website.

Your router's address could be 192.168.1.1, so if you could find out for sure what it is that would be very helpful.

---

### Post by drahmad on 2007-01-24
I should be able to browse to my router even without the DNS setting right?

I did put the DNS in just now to check, but still no luck :/

Edit: I had no idea that I had to "TICK" the ethernet card in order for it to work - I double clicked and then "enabled this device" but didn't realise it had to enabled "again"!

Thanks, all sorted now.

Still would like questions about "device manager" and future installs of hardware answered if possible please - questions are still listed above.

---

