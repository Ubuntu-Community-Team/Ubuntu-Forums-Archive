---
title: "[SOLVED] USB permissions"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-12-08
I modified my /etc/udev/rules.d/40-permissions.rules file so that the USB line looks like this:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", 		GROUP="usbusers", MODE="0666"

I have an application that needs to read/write a USB device but I don't want to SUDO it or run as root.  First I changed the mode from "0664" to "0666" so it was wide open and that works fine.  Next I added the "GROUP" with the intent of putting users who are allowed to access USB devices in that group.  I then changed the mode back to "0664" with the result being I don't get access to the device.

Can someone help me set this up correctly (if what I'm thinking I can do with the group is even correct to begin with)?  Is there a way to set this up specific to a device, and let the rest of USB devices default?

Thanks in advance!:)

---

### Post by Arthur Archnix on 2007-12-09
What's the program?

---

### Post by anewguy on 2007-12-09
The program is a meld of pv2fetch and avidownload (see sourceforge).  It downloads from the hacked "one time use" camcorder and "one time use" digital camera from CVS/Rite-Aid.  When the cameras are mounted, the 40-permissions.rules was by default having root own the device.  This meant the program needed to be run either via "sudo" or by the root user.  The program creates subdirectories where it stores the given downloads.  The result is files in a user's directory tree that are owned by root and therefore the user can't by default delete them.  Changing the 40-permissions.rules to 0666 allows for a normal user to run the program (without the need for "sudo" or as root), which therefore creates the subdirectories with the user as the owner, so now the user can do as they please with the files/folders.

Since 0666 leaves USB fs devices wide open, not secure, I wanted to try the group route, and change the permissions back to 0664.  The result of that, even with the user in the group specified for USB fs devices, was that the device was not accessable due to the users lack of rights.

Ideally, what I would like is a seperate spec for each of the cameras, so they can be mounted wide-ope (0666), but let all other devices default back to protected (0664).

I have searched online and have not come up with anything that says what the syntax of the subsystem== statements in the xx-permissions.rules files is.  If I could find that, I could probably set up a default subsystem== for each camera and a system default subsystem== for all other devices (USB).

Any help would be greatly appreciated!:)

---

### Post by Arthur Archnix on 2007-12-09
> If you use Debian/Ubuntu, look in the /etc/udev/permissions.rules file. If you want to allow global access to all usb devices, make this change:

Change this: SUBSYSTEM=="usb_device", MODE="0664"

To this: SUBSYSTEM=="usb_device", MODE="0664", GROUP="usb"

After you reboot, all usb devices will inherit the mode and group specified.

If you want to only change permissions for certain devices, you can add this on one line and adjust the product and vendor IDs:

  SUBSYSTEM=="usb_device", GROUP="usb", \
           SYSFS{idVendor}=="1234", SYSFS{idProduct}=="1234"

from [http://search.cpan.org/~gwadej/Device-USB-0.21/lib/Device/USB/FAQ.pod](http://search.cpan.org/~gwadej/Device-USB-0.21/lib/Device/USB/FAQ.pod)

---

### Post by anewguy on 2007-12-09
> **Arthur Archnix said:**
> from [http://search.cpan.org/~gwadej/Device-USB-0.21/lib/Device/USB/FAQ.pod](http://search.cpan.org/~gwadej/Device-USB-0.21/lib/Device/USB/FAQ.pod)

Bingo!!  Exactly what I was looking for!!  Thanks so much!!:)

---

### Post by Arthur Archnix on 2007-12-09
Cheers.

---

### Post by daverave999 on 2008-04-16
I'm having similar problems writing to SD cards in a reader.

I have added the```
, GROUP="usb"
``` part but it still won't work.

Should I have created a 'usb' group?

[EDIT: I did reboot after adding it...]
[EDIT2: The write-protect tab is in the writeable position.]

[EDIT3: Many apologies-it appears to be a problem with the USB port I was putting it into. It works fine in another port!]

---

### Post by PmDematagoda on 2008-04-16
daverave999 next time please don't reply in a thread as old as this, if you really wanted to link your question with this thread then you could have made a new thread and then made a link to this one.

This thread is closed.

---

