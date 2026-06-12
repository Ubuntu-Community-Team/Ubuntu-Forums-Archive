---
title: "Powerbook G4 problems with USB Bluetooth Ethernet"
date: 2010-01-02
forum: Apple Hardware Users
---

### Post by serpetiello on 2010-01-02
Hi,

I installed Ubuntu 9.10 PPC on my Powerbook G4 17" 1.67 GHz ("early 2005" series), 1Gb RAM, 100Gb disk, "vertical lines" screen problem.

I have a non-powered USB hub on which I have two USB-to-serial converter and a Wacom CTE640 ("Graphire4") tablet. As of "lsusb -v", they require 50 to 90mA each, thus it is safe to use them on a non-powered hub. I have Apple bluetooth keyboard and Apple bluetooth mouse as well.

Important: all this hardware "just works" on my intel-based PC with Ubuntu 9.10, in any combination.


USB problems on Powerbook + Ubuntu 9.10 PPC, both verified with and without hub:

- Wacom Graphire4 doesn't work (it doesn't even appear in /dev/input/ when connected); the "lsusb" shows it, but no device is created

- USB to RS232 adapters have problems sending/receiving characters (noise characters in both directions); -- "dmesg" output shows they are correctly recognized (a Prolific 2303 and an "1a86 USB2 Serial port"); same problem when connecting without using the hub

- I got another USB to RS232 adapter (FTDI 232) and it is working (both on USB hub and direct USB port) provided that is connected after booting complete

- a Chesen adapter (one USB to "PS2 keyboard + PS2 mouse" connectors), known to have problems on intel machines on different operating systems, also works, provided that it is connected after booting complete


Bluetooth problems:

- Apple bluetooth mouse (early 2005) works but its connection has to be manually deleted and re-configured at every reboot (using the "Connect" command from the "Apple bluetooth mouse" under the Bluetooth icon, does not connect, even if unpowering/powering the mouse)

- Apple bluetooth keyboard cannot be paired (I type in the required pin but the bluetooth wizard waits forever); same result even after keeping the keyboard without batteries for some hours to have it "forget" previous connections


Kernel/Ethernet weird problem:

- ethernet works, but when the cable is connected, a frequent kernel bug appears. In the "dmesg" I see:

[19846.072791] BUG: scheduling while atomic: swapper/0/0x10010000
...(modules/registers/calltrace follows)...

It happens randomly every 5 to 90 seconds. It seems it does not originate other problems, but it is not something that nice to see in the system log message list...




Software problems:

- I have an external DVI display: I had to disable graphical effects because of a random flicker (appearing as if the entire screen was shifted on the left by 2-3 pixels for a fraction of second)

- I enabled "assistive" features to have the "secondary button" emulation when clicking for a certain period of time. Sometime it does not work (even "longclicking" the desktop). This is a longstanding bug in Gnome (I had it on Ubuntu 8.04 and 8.10, and it appears again on Ubuntu 9.10 both Intel and PPC)

- even when "locking" applets on the panel, I get a different order at every reboot; this is quite annoying, but it appears more a Gnome bug than a Ubuntu problem.


I did not have any crash during installation of Ubuntu 9.10 PPC.

I cannot test other machines, so I cannot guess if they are software problems or hardware problems (sometimes I miss a paranoid feature: "verify, for each installed package, presence and checksum of every file"...).

And I DON'T want to go back to Mac OS X.

Any information is appreciated.
Thank you.

---

### Post by serpetiello on 2010-01-04
Update:

Tried with a powered USB hub from a different brand: same problems.

Tried adding another USB-bluetooth key: the Bluetooth stack simply ignores it (hciconfig shows almost no traffic there). This seems a Gnome bluetooth problem, because if I disable the primary Bluetooth adapter (using hciconfig), the Bluetooth section appears entirely "disabled" (even if hciconfig reports the second unit "up iscan pscan"). Gnome seems to only use the first bluetooth adapter it can recognize.  No changes using Blueman instead of the standard bluetooth manager.

Tried another bluetooth keyboard (a Nokia SU8W): while I can "pair" it, not even a single keypress reaches the Powerbook. Thus the Bluetooth problem described in these two messages appears as a poorly implemented software...

Tried another FTDI "USB-to-serial" adapter: it works. The other adapters (non-FTDI ones) still do not work. One of these shows "transmit noise" only (receiving is good).

Tried every USB thing without hubs: no change. Tried everything on an intel-based Ubuntu 9.10 tablet PC: everything works flawless.

That hardware worked great both on Mac OS X 10.4 Tiger (PPC) and on Ubuntu 8.xx/intel and 9.xx/intel.

I guess there *may* be some hardware problem on the USB part of my Powerbook G4, but it seems there *are* software problems on PPC port (especially that kernel "scheduling while atomic"). Weird thing, a few weeks ago the intel kernel was upgraded to 2.6.31-16, while the PPC release did not move from patch level 14 (2.6.31-14).

I spent countless hours (countless reboots, countless megabytes of updates, and *three* full reinstalls) trying to figure out some combination of connections/hubs but the most I got was internet surfing while reading RS232 data on one device only.

I am going to kill Ubuntu PPC and switch to Slackintosh. :(

---

