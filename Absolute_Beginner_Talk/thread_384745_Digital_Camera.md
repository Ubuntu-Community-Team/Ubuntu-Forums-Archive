---
title: "Digital Camera"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by gaby PR on 2007-03-14
My camera was working since I installed Ubuntu 6.10.  Today I tried to import photos and the following error message show.

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I tried with digikam but also I cannot connect to the camera.  

The camera is recognize by the system.

Any help will be appreciate.

---

### Post by yabbadabbadont on 2007-03-14
Downgrade libgphoto2 to the previous version, the update has been causing this error for a lot of people.  (and should have shown up in a forums search...  ;))

---

### Post by yabbadabbadont on 2007-03-14
Known bug:  [https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

---

### Post by gaby PR on 2007-03-14
How I do the downgrade?

---

### Post by yabbadabbadont on 2007-03-14
Just make the change listed in the bug report and the problem should be fixed.
> Binary package hint: libgphoto2-2

The file /etc/udev/rules.d/45-libgphoto2.rules says in line 3:

BUS!="usb*", GOTO="libgphoto2_rules_end"

while recenly updated udev doesn't produce BUS properties in corresponding event. Thus this line makes the whole file useless, because BUS!="usb*" is never true.

Something like

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

instead would work.

So you would open a terminal window and run "sudo gedit  /etc/udev/rules.d/45-libgphoto2.rules".  Change the line that looks like:
BUS!="usb*", GOTO="libgphoto2_rules_end"
So that it looks like:
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
Save your change, logout, reboot.

---

### Post by teddmeister2 on 2007-03-19
I tried this fix and I got an error when I tried to import it was something like the following:
Protocol error, PTP: data expected.

...or something like that.

---

### Post by yabbadabbadont on 2007-03-19
Verify that your camera is in PTP mode and not USB mass storage mode.

---

### Post by rosswmcgee on 2007-03-31
> **yabbadabbadont said:**
> Just make the change listed in the bug report and the problem should be fixed.

So you would open a terminal window and run "sudo gedit  /etc/udev/rules.d/45-libgphoto2.rules".  Change the line that looks like:
BUS!="usb*", GOTO="libgphoto2_rules_end"
So that it looks like:
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
Save your change, logout, reboot.
I had the same error on my Kodak Easy Share 6630. This fix worked perfectly. What I do not understand is why Digikam worked the first time I used it in ubuntu 6.10, but the next  time I got the above error. Well it is fixed now and I thank Ubuntu for these great forums. I could never have installed evey thing I have with out them. I am an old time Linspire user, but have installed Edgy and really like it. The next move will be to go to Feisty I guess but wonder why when everything works so well now.

---

### Post by rare HERO on 2007-08-05
> **yabbadabbadont said:**
> Just make the change listed in the bug report and the problem should be fixed.

So you would open a terminal window and run "sudo gedit  /etc/udev/rules.d/45-libgphoto2.rules".  Change the line that looks like:
BUS!="usb*", GOTO="libgphoto2_rules_end"
So that it looks like:
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
Save your change, logout, reboot.
This solution worked for me thanks!

---

### Post by MST3Kakalina on 2007-08-14
This didn't work for me.  I'm on Dapper, with a Kodak EasyShare Z740.  Would an upgrade to Edgy/Feisty fix this?

---

### Post by yabbadabbadont on 2007-08-14
> **MST3Kakalina said:**
> This didn't work for me.  I'm on Dapper, with a Kodak EasyShare Z740.  Would an upgrade to Edgy/Feisty fix this?

What is the exact error message, if any, that you see?

---

### Post by z987k on 2007-08-25
This is wierd, my camera worked fine in dapper, I upgraded to fiesty and now I get a PTP I/O error.  Camera is a Cannon Powershot A710 IS.  It uses ptp instead of making it easy and using usb mass storage.

I've tried the fix with this file: /etc/udev/rules.d/45-libgphoto2.rules
amd I've downgraded gphoto and it's libraries as suggested in this thread, but I still get the I/O error.

I've also tried running as root, but that doesn't do anything either.

We need to get a fix for this, seems like it's been around for a long time.

---

### Post by rare HERO on 2007-09-13
> **rare HERO said:**
> This solution worked for me thanks!
It does not work anymore.

---

