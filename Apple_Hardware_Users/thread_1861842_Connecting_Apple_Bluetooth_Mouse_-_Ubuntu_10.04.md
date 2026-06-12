---
title: "Connecting Apple Bluetooth Mouse - Ubuntu 10.04"
date: 2011-10-16
forum: Apple Hardware Users
---

### Post by Epiphyte on 2011-10-16
[FONT="Arial"]I'm trying to pair an Apple Bluetooth Mouse with my Mythbuntu machine.

I've read this thread[/FONT] [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=224673]("http://ubuntuforums.org/showthread.php?t=224673")[/COLOR][FONT="Arial"] and find it a bit rambling.[/FONT]

[FONT="Arial"]I'm using Mythbuntu based on Ubuntu 10.04 and am using Gnome Bluetooth Manager.

I have:
   i. put hid_apple in my[/FONT] [FONT="Courier New"]/etc/modules[/FONT] [FONT="Arial"]file;

   ii. found my device address, and added it to my[/FONT] [FONT="Courier New"]/etc/bluetooth/rfcomm.conf[/FONT] [FONT="Arial"]file, as follows:[/FONT]
[INDENT][FONT="Courier New"]rfcomm0 {
#Automatically bind device at startup
bind yes;
# Bluetooth address of device
device 7C:6D:62:F3:81:81;
# Channel for connection
channel 1;
#Channel Description
comment "Apple Bluetooth Mouse";
}[/FONT]
[/INDENT]

[FONT="Arial"]When I enter:[/FONT] [FONT="Courier New"]$ lsusb[/FONT] [FONT="Arial"]
I get:[/FONT]
[FONT="Courier New"]Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
[/FONT]
After I reboot, the system doesn't respond to the mouse at all.

Any thoughts & assistance would be welcome :confused:

---

