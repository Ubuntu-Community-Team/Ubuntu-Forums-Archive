---
title: "[SOLVED] USB device missing USB device not missing"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-08-13
The computer froze twice today and it's never done that before. I posted about this earlier today, but I believe I didn't explain the problem properly.

While Firefox had a page completely loaded, the mouse and keyboard froze. Ctrl-Alt-Backspace was frozen, as well as Ctrl-Alt-Del. I had to press the reset key. Once the GRUB brought up the selections, I chose "Recover mode". Ub finished booting and I did

mark@lexington#: shutdown -r now

things almost ground to a halt and I did

mark@lexington#: exit

The OS loaded again and I did a cold stop. The machine came to a cold stop and I cold booted. (Ah! how I miss the days of DOS -- ahem, not really!) 

Between this and the next series of reboots, FireFox asked to install the new TOR (The Onion Router) and I accepted the upgrade, but dismissed the "restart FireFox" . A moment after the new install of TOR, the system froze again. 

I did as above with recover, then a compete shutdown. My usb devices went partially missing. At first both the scanner and memory stick were both missing in lsusb. I pulled the plugs on both and reinserted them. Nothing. I rebooted again. This time, the memory stick showed up but not the scanner. 

When gimp is asked to File/Acquire/XSane/DeviceDialog; returned is: no devices available. BUT:

mark@Lexington:~$ lsusb
Bus 001 Device 010: ID 13fe:1a00  
Bus 001 Device 009: ID 04b8:010f Seiko Epson Corp. Perfection 1250
Bus 001 Device 003: ID 04f9:000d Brother Industries, Ltd HL-1440 Laser Printer
Bus 001 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-port Hub
Bus 001 Device 001: ID 0000:0000  

And even though the memory stick icon is on my desktop and can be opened & files moved, copies, deleted, it isn't showing up.

Is TOR's update at the bottom of this? I have been testing a Sony VIAO USB keyboard. It's backspace key and some others are kaput. I did have it plugged in while the regular kb was plugged into the regular old socket at the back of this Dell box. Did that break the USB?

---

### Post by Mark_in_Hollywood on 2007-08-13
I've become so frightened that I harmed the OS without knowing how, I ran Picassa because I know it will run the scanner, too. After a few moments of config. It returned a device not found type of error message.

I ran gimp again and Low & Behold! without anything being changed other than invoking and closing Google's Picassa, gimp started scanning again. 

So even though this isn't a solution, I'm marking this thread solved.

Thanks.

---

