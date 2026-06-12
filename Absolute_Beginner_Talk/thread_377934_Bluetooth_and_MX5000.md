---
title: "Bluetooth and MX5000"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by strikeback03 on 2007-03-06
I have a Logitech MX5000 keyboard.  When I first installed Ubuntu it worked properly most of the time.  Now it will not connect.  Typing: ```
 hcitool dev 
``` returns no devices.  The Logitech BT mini-receiver is listed (several times) in the device manager though.  I moved the dongle since installing, does it need to be told to look somewhere else?  And on a related note is it possible to get the MX5000 working in GRUB so that I don't need to leave a wired keyboard connected and pull it out every time I turn the computer on?

---

### Post by strikeback03 on 2007-03-06
anybody have any ideas on fixing bluetooth?

---

### Post by desert00rat on 2007-03-07
I have the exact same keyboard and when loading up the GRUB menu, the keyboard and mouse will act like a normal keyboard and mouse. 

As far as getting the keyboard working in Edgy, I used [[COLOR="Red"]this page[/COLOR]]("https://help.ubuntu.com/community/BluetoothSetup") to get it working again. Specifically, about half way down under the heading of "Connect Devices at Startup".

I know the BT signal is kinda weak, and the closer you can get the dongle to the keyboard/mouse the better.

Hope this helps.

---

### Post by strikeback03 on 2007-03-07
Yeah, I used that page to get Bluetooth working initially.  However since switching the receiver to a different port (in a hub in my monitor) it has not worked.  The keyboard still works fine in XP.  Normally I don't use the BT MX1000 with the desktop (have a normal MX1000 there, use the BT one with my laptop), but I just tried with the same result - no connection, hcitool dev sees no devices.  Is there a problem running in a hub, or do I have to tell it the BT receiver has moved?

The keyboard has never worked for me in GRUB.  Works in the BIOS, but not GRUB.  Do I need to add BT support when GRUB loads or something?

---

### Post by strikeback03 on 2007-03-08
OK, more info.

If I boot with the BT dongle in a USB port on the back of the computer, the BT receiver shows up in Device manager under USB UHCI controller and the keyboard works, along with hcitool finding devices, etc.  If I boot with the dongle plugged into the monitor hub, the BT receiver shows up in Device Manager under a USB EHCI controller, and the keyboard will not work unless I remove and reinsert the dongle.  This causes the keyboard to work, but hcitool does not find anything.

If I enable "USB Keyboard" in the BIOS, I can use the BT keyboard in GRUB, but then Ubuntu won't boot, it goes to "Starting up" with the blinking cursor and stays there.  How do I get USB keyboard support in GRUB and still allow the system to boot?

---

### Post by strikeback03 on 2007-03-09
Any Ideas anyone?  Should I repost in one of the Main Support Catagories for different exposure?

---

