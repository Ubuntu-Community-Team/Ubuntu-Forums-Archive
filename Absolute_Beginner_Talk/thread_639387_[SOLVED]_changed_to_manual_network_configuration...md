---
title: "[SOLVED] changed to manual network configuration..."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by slira on 2007-12-13
Hi there
I've just made a mistake...
in order:

installed Ubuntu 7.10 + kde
wireless was working ok, symbol automatic in tray (barchart like)
I changed to "manual network configuration" by mistake (stupid!)
now it is not working and I don't know how to "revert" the prosses............

Help! Thanks
Sérgio Lira

---

### Post by cmnorton on 2007-12-13
First, save away your /etc/network/interfaces file.

sudo cp /etc/network/interfaces /etc/network/manual_interfaces # suggested saved name

Then, edit the file, replace the contents of the file with the following:

auto lo
iface lo inet loopback

and save as /etc/network/interfaces. Of course you'll be sudo vi /etc/network/interfaces

where vi is vi or your favorite editor.

Either restart the network or reboot.

That should reset you. However, save the original file and anything else you edit. Use whatever saved name that makes sense to you. I just chose a name for my example.

---

### Post by slira on 2007-12-14
Thanks!!! solved
sergio lira:)

---

