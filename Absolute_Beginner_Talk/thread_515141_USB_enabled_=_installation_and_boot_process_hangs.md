---
title: "USB enabled = installation and boot process hangs"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by x-claus on 2007-08-01
Copenhagen, Denmark, 1.8.2007

Installing Ubuntu 5.04: When USB is enabled

a) The installation process hangs at a very early stage. 

Consequently USB was disabled, and the installation process terminated seemingly in good order.

Then USB was again enabled and

b) the boot process hangs after the message "*starting hotplug subsystem ..."

USB NEEDS to be enabled as I am using the pc with other (Windows) harddisks in removable frames.

How do I make Ubuntu 5.04 accept the USB ports?

regards
x-claus

---

### Post by Rocket2DMn on 2007-08-01
If the problem is at boot, you probably need to ensure your boor order is correct in the BIOS. USB should not fall above the HDD or the CD-ROM, unless that's how you actually want it.
Why are you installing 5.04? Hoary is rather old, you should be installing 7.04 Feisty Fawn, or at least 6.06 Dapper Drake (long term support - LTS).

---

### Post by x-claus on 2007-08-01
Version 5.04 is the one I have had lying around for some time, and I decided to try it out.

The USB problem is not a question of boot order:
1. As I wrote, it also happened during installation
2. The pc can't even boot from USP ports.

The switch " .../probe/usb=false" did not prevent the installation process from seeing the USB ports.

Is version 6.06 or 7.04 better in that respect?

regards
x-claus

---

### Post by Sayers on 2007-08-01
Ofcorse it's better, it's 2 years of development!

---

