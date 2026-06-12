---
title: "USB problemo"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by danteman on 2007-01-29
Hi,

After having read and tried several ways of solving the problem with the USB mouse and keyboard not working after starting edgy with no luck I'm in desperate need for help. 
After some struggle I managed to install edgy with the help of an ps2 adapter to my mouse hoping that once it was installed everything would work fine. Sadly it didn't. When I get to the login mouse and keyboard are shut down. I did however manage to start ubuntu once by tapping the keyboard during startup. 
So far I've tried:

- tapping the keybord like a maniac (one successful startup!!)
- booting with acpi=off, noapic
- change BIOS setting USB legacy on (auto was default).
- screaming/staring

My Computer by the way is a HP pavilion t3150 with an AMD64. I did however install the 32-bit version after reading recommendations on the internet.

What can I do more? what would YOU do?

Now suppose that I get it started what would I have to change in the settings to force or make sure ubuntu detects the USB mouse and keyboard?

All help is appreciated
/Desperate Dan

---

### Post by dmitry on 2007-01-29
Unplug usb devices, boot your PC, open terminal and type there:

~$ tail -f /var/log/syslog

Plug your device and check terminal. There must be messages from kernel about new device found. (post it there).

Or you can just plug your device and run:

~$ lsusb

---

### Post by danteman on 2007-01-30
I tried to unplug all USB devices and wait for the login window - and it worked! What can I do next? I ran ~$ lsusb and saw my USB keyboard/mouse combo. I saved the output text but unfortunately I forgot it at home...
What next? 

/D

---

### Post by muguwmp67 on 2007-01-30
I think we're having the same problem.  If you boot with your keyboard plugged in, and wait a couple minutes, does the keyboard work?

---

### Post by danteman on 2007-01-30
> **muguwmp67 said:**
> I think we're having the same problem.  If you boot with your keyboard plugged in, and wait a couple minutes, does the keyboard work?

I don't know. I can try when I get home in about 8 hours. Hopefully someone here knows what setting etc to change to make it work :D

---

### Post by danteman on 2007-01-30
Hi,

The mouse and keyboard works fine if I wait to plug it in until the login screen appears. My USB ports are gonna get worn out if I don't find an alternate solution to this problem...
Hopefully the info below might help. Any ideas are welcome!
/D

$ tail -f /var/log/syslog
Jan 30 21:43:03 dante-desktop kernel: [17180124.388000] APIC error on CPU0: 40(40)
Jan 30 21:44:42 dante-desktop kernel: [17180223.088000] APIC error on CPU0: 40(40)
Jan 30 21:48:59 dante-desktop kernel: [17180480.448000] usb 2-1: USB disconnect, address 2
Jan 30 21:49:13 dante-desktop kernel: [17180493.988000] ohci_hcd 0000:00:13.1: wakeup
Jan 30 21:49:13 dante-desktop kernel: [17180494.376000] usb 2-1: new low speed USB device using ohci_hcd and address 3
Jan 30 21:49:14 dante-desktop kernel: [17180494.584000] usb 2-1: configuration #1 chosen from 1 choice
Jan 30 21:49:14 dante-desktop kernel: [17180494.592000] input: Logitech USB Receiver as /class/input/input5
Jan 30 21:49:14 dante-desktop kernel: [17180494.592000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.1-1
Jan 30 21:49:14 dante-desktop kernel: [17180494.604000] input: Logitech USB Receiver as /class/input/input6
Jan 30 21:49:14 dante-desktop kernel: [17180494.604000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-1

:~$ lsusb
Bus 003 Device 004: ID 0930:6508 Toshiba Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:0b0c Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by muguwmp67 on 2007-01-31
I solved it on mine.  Unfortunately, it took a reinstall of Ubuntu (which ultimately wasn't needed) to diagnose.

After reinstalling ubuntu, I had the same problem.  Since this didn't happen when I installed ubuntu the first time, I decided that it wasn't a ubuntu or linux configuration file.

[LIST=1]
[*]I removed all of the USB devices from my PC
[*]plugged a PS/2 adapter onto my keyboard and plugged it into the PC
[*]Unplugged the PC for 1 minute
[*]Plugged in my mouse and keyboard, booted
[*]They were detected, so I shut down, plugged in the rest (printer, hub, etc) booted up and the problem was fixed!
[/LIST]

My guess is that the motherboard wasn't delivering an insertion message, or some such technobabble.

Hope it helps!

---

### Post by danteman on 2007-01-31
My problem is that I don't have a ps2 keyboard...
In this day and age you would think that would work. 

Anyone else have a suggestion?

/D

---

### Post by muguwmp67 on 2007-01-31
My goal was to flush out all of the previous usb device identification prior to boot.  There might be a BIOS option to reset hardware identification.  My last PC did, but I  don't have it in my current BIOS settings.  

Maybe someone knows how to do this from a command line?

You might try the shutdown and unplug portion though.  I don't know whether USB information gets stored in CMOS or not.  (hmmm...worse comes to worst, you might shut down, unplug, pull out the CMOS battery for a minute, plug it all back together and reboot). 

I wish I could give you an easier answer, but I'm new at this too, and it really seems to me like the problem is occuring before ubuntu boots, at least mine was.

Does anyone know of a command line option that would reset usb identification?

---

### Post by dmitry on 2007-01-31
It's strange. Your computer determines your mouse and keyboard.

In your message I see "APIC error". Try noapic, when boot.

---

### Post by danteman on 2007-02-09
I solved it by installing opensuse. but thanks for your help!

/D

---

