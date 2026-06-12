---
title: "Crashes in Linux....."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by MerreM on 2008-04-19
OK,
I'm guessing this has been posted before, but I can't find it anywhere.
So here goes.
I've been using Ubuntu a little while now and it keeps locking up. 
I mean properly locking up, not mouse movement windows mid change. etc.
I assumed it was a sata drive unplugged that, no help. (after a reinstall)
So i switched to Fedora, assuming it was a Ubuntu issue.
Apparently not.
Back on ubuntu now, had the same problem. Most common when updating; but anything will set it off, even leaving the computer on the login screen, everything shuts down and stops responding...
So....
Any idea what it could be?
Running on a Quad Core Q6600
2gb Ram,
Nvidia 8800(GT!?)
Couple of HDDs, one SATA (data) one IDE with Xp and Ubuntu on.
Anyway, at first I assumed it was xOrg or something but I honestly don't know what to look for.
Couple of logs for you.
Apr 19 15:46:25 Wodan kernel: [   73.998766] Adding 979956k swap on /dev/hda3.  Priority:-1 extents:1 across:979956k
Apr 19 15:46:25 Wodan kernel: [   74.373940] EXT3 FS on hda2, internal journal
Apr 19 15:46:25 Wodan kernel: [   75.600148] input: Power Button (FF) as /class/input/input4
Apr 19 15:46:25 Wodan kernel: [   75.600164] ACPI: Power Button (FF) [PWRF]
Apr 19 15:46:25 Wodan kernel: [   75.600195] input: Power Button (CM) as /class/input/input5
Apr 19 15:46:25 Wodan kernel: [   75.600205] ACPI: Power Button (CM) [PWRB]
Apr 19 15:46:25 Wodan kernel: [   75.600231] input: Sleep Button (CM) as /class/input/input6
Apr 19 15:46:25 Wodan kernel: [   75.600243] ACPI: Sleep Button (CM) [SLPB]
Apr 19 15:46:25 Wodan kernel: [   75.621894] No dock devices found.
Apr 19 15:46:25 Wodan kernel: [   76.439048] ppdev: user-space parallel port driver
Apr 19 15:46:25 Wodan kernel: [   76.569210] audit(1208616385.684:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5336 profile="/usr/sbin/cupsd"
Apr 19 15:46:25 Wodan kernel: [   76.673417] Failure registering capabilities with primary security module.
Apr 19 15:46:25 Wodan dhcdbd: Started up.
Apr 19 15:46:25 Wodan kernel: [   76.795763] eth1: link up, 10Mbps, half-duplex, lpa 0x0000
Apr 19 15:46:25 Wodan kernel: [   76.824162] Bluetooth: Core ver 2.11
Apr 19 15:46:25 Wodan kernel: [   76.824243] NET: Registered protocol family 31
Apr 19 15:46:25 Wodan kernel: [   76.824245] Bluetooth: HCI device and connection manager initialized
Apr 19 15:46:25 Wodan kernel: [   76.824248] Bluetooth: HCI socket layer initialized
Apr 19 15:46:25 Wodan kernel: [   76.830788] Bluetooth: L2CAP ver 2.8
Apr 19 15:46:25 Wodan kernel: [   76.830791] Bluetooth: L2CAP socket layer initialized
Apr 19 15:46:25 Wodan kernel: [   76.880690] Bluetooth: RFCOMM socket layer initialized
Apr 19 15:46:25 Wodan kernel: [   76.880821] Bluetooth: RFCOMM TTY layer initialized
Apr 19 15:46:25 Wodan kernel: [   76.880824] Bluetooth: RFCOMM ver 1.8
Apr 19 15:46:27 Wodan dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 19 15:46:30 Wodan kernel: [   81.008155] NET: Registered protocol family 17
Apr 19 15:46:30 Wodan dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Apr 19 15:46:30 Wodan dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Apr 19 15:46:30 Wodan dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Apr 19 15:46:31 Wodan kernel: [   82.397405] NET: Registered protocol family 10
Apr 19 15:46:31 Wodan kernel: [   82.397516] lo: Disabled Privacy Extensions
Apr 19 15:46:31 Wodan kernel: [   82.397648] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 15:46:29 Wodan kernel: [   83.914584] hda-intel: Invalid position buffer, using LPIB read method instead.

Hope you can help!
Mike.

---

### Post by gn2 on 2008-04-19
Have you overclocked it at all or is it running standard settings in the BIOS?

---

### Post by mikeyphi on 2008-04-19
Random lockups - not OS related.....could be a RAM problem.
Some years ago, under windows I kept getting the blue screen of death - on examination it seemed to be related to some memory addresses, so I replaced the RAM module (after trial and error to find the faulty module) and all worked fine.
Think on it!

---

### Post by Moop on 2008-04-19
Have you run memtest from the live cd or from the boot menu? Do you have a decent power supply in your pc?

---

### Post by RumorsOfWar on 2008-04-19
I had an identical lockup problem. It ended up being a video problem. I installed a PCI-E card, but the bios was still set to PCI.  I changed the bios setting and haven't had a lockup since.
I hope that helps.

---

### Post by MerreM on 2008-04-19
Thanksfor the responses!
Ok...First off;
Not overclocked.
And there not too random; happens mainly if I update or if i leave it too long.
Will run memtest though.
Decent power supply?
I'd hope so.
XP runs fine.
I'll get back to you in a sec on Memtest.
And for the sweet irony, in Ubuntu whilst attempting to respond; it crashed.

---

### Post by MerreM on 2008-04-19
Mem test was either;
Unresponsive,
Or on a loop,
I'll get back  to you. 
But it appeared to have no errors whilst i oculd be arsed to watch it..
Any other ideas?

---

### Post by will1911a1 on 2008-04-19
Could be a heat issue... are all your fans working?

---

### Post by thewump on 2008-04-19
Do you have another machine on the network?  If so,  then o the problem machine, 

sudo apt-get install ssh

and set up a static IP for that machine, or make a note of it next time you connect.

When the "crash" occurs go to the other machine and type:

ssh ip.ip.ip.ip -l username

where ip is the ip address of the crashed machine and username is your username on it.  You'll proably have to say YES it's ok about certificate stuff.

If that lets you login, then it's the X window that has crashed, not the machine itself.  I have found that happens.  in the terminal type:

top

That shows you what processes are currently eating up CPU. What's at the top?  Is anything at 100%?  Do you see compiz on that list?

Recently I've seen compiz locking me up, in which case the problem could be various things.. hardware acceleration has many elements.

If you type:

ps -ef |grep compiz

you should end up with a line of in.. the PID is on the left.. a number, eg 12345

try typing 

kill 12345

Your machine might magically come back to life without compiz..

Anyway. Hope this helps you go in the right direction.

Keith

---

