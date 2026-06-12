---
title: "Cannot set up (Wired) NIC - not autodetected"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by dcoulshed on 2007-05-23
I'm absolutely new to Linux.  
I'm using a superceded computer from work - an AMD Athlon TX (whatever that is!) with 256 MBytes RAM, 32 GByte HDD and a Realtek RTL8139/810x Family PCI Ethernet NIC.
I'm using Ubuntu 6.06.1, downloaded successfully and installed successfully.

The trouble is that Ubuntu doesn't seem to recognise the Ethernet card is there.  It is hard-wired into the motherboard.  I've also tried Debian i386 install and it doesn't recognise the Realtek's existence, and neither does Ubuntu 7.04 or my (now installed) 6.06.1.

The rest of Linux appears to run OK, but my reason for wanting the whole setup is to access the internet - I've a Windows PC at home that keeps crashing, connected through a Speedtouch 510v4 Router and I want to put this one alongside and then convert entirely.  Can't get over the first hurdle of getting this one going, though.

I've tried to follow others' questions, but am stuck.  In Terminal, typing "lspci" just takes me straight back to the command line (does that mean there's no PCI devices found?).  Same for "lsusb".  Typing "ifconfig" gives:
lo   Link encap:Local loopback
      inet addr: 127.0.0.1  Mask: 255.0.0.0
      inet addr:  : : 1/128  Scope: Host
      UP LOOPBACK RUNNING   MTU: 16436   Metric:1
      RX packets: 277 errors:0  dropped:0  overruns:0  frame:0
      TX packets: 277 errors:0  dropped:0  overruns:0  carrier:0
      collisions:0 txqueuelen:0
      RX bytes: 15328  (14.9 KiB)  TX Bytes: 15328  (14.9 KiB)

Where do I go from here?

Thanks

---

### Post by chili555 on 2007-05-23
Would you please try:```
sudo modprobe 8139too
sudo ifup eth0
```Please let us know what happens. Thanks.

---

### Post by dcoulshed on 2007-05-23
Thanks
I entered:  sudo modprobe 8139too
I then entered: ifup eth0

Reply:
ifup: failed to open statefile /var/run/network/ifstate: Permission denied

---

### Post by chili555 on 2007-05-23
```
**sudo** ifup eth0
``` If in doubt, sudo. "Sudo, honey could you get me a cold beer?"

---

### Post by dcoulshed on 2007-05-23
Silly mistake by me!

after "sudo ifup eth0" I get

Internet Systems Consortium DHCP Client V3.03
Copyright .....
All rights ........
For info. ........

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

By the way, I haven't actually plugged the ethernet cable into the computer as I do this (I need to use it to get access to the internet to view these questions on another computer! Does this matter?

Thanks

---

### Post by chemtut on 2007-05-24
yes it does---connect at boot

---

### Post by dcoulshed on 2007-05-27
I've tried connecting up the ethernet cable and rebooting.  No use

I've tried reloading Ubuntu 6.06.1 from CD, with the ethernet cable connected, still no use.

I then used the instructions "sudo modprobe ..." etc, suggested before, with the same result I described before.

The ethernet cable is OK, I've used it elsewhere.  I'm reluctant to blame the ethernet card, because i) it worked on the previous use of this computer (admittedly an institution network rather than a single user one), and ii) it is an integral part of the motherboard - I don't know how I would replace it even if it were faulty!

Any other ideas?

---

### Post by dcoulshed on 2007-05-27
To try further on my own (!) I've even tried loading another version of Linux - Debian - and from the CD i386 installation disc it says "no ethernet card detected" and won't accept me manually selecting a Realtek 8139 from the list provided.

As I said before, I'me a bit reluctant to say it's faulty because it seemed to work on the previous Windows-based network, but it's beginning to look that way.  The trouble is that the ethernet connector seems to be wired/soldered direct onto the motherboard, so it would be easy to replace or bypass, would it?

Grateful for any further help ....

---

### Post by gary0 on 2007-05-27
Is the ethernet card enabled in bios? My ether card is the same built in to the mobo. I have used the equivalent pci cards aswell, and all were detected at install. Check your bios, the solution may well be there....

Gary.

---

### Post by dcoulshed on 2007-05-28
Thanks gary0, that was a good suggestion, and could perhaps have explained the difficulties that I've had.  It still might, if I can just work the BIOS settings.
The trouble is that I cannot find anywhere in the BIOS settings where the Realtek device is mentioned.
I have tried various things:
Under PnP/PCI Configurations I found that PnP OS was disabled, so I enabled it.  No difference.
I found something called PCI/VGA Palette Snoop which was disabled, so I enabled it, but no difference.
Under the "Integrated Peripherals" menu, I found something called VIA OnChip PCI device.  This looked promising.  The submenu showed VIA-3058 AC97 Audio and VIA-3068 MC97 Modem were both set to "Auto" so I disabled them, but this made no difference either.
I rebooted after each change and tried the lspci, modprobe and ifup lines in Terminal, as suggested before, but the answers were unchanged.
I don't know where else to go in the BIOS settings.

---

### Post by dcoulshed on 2007-06-07
Further input: for complex reasons I found access to an identical computer apart from the fact that it had a different network card.

Now there is no problem: I conclude that the Realtek 8139 is difficult if not impossible to get to work with Ubuntu.  Pity, but there you are ....

---

