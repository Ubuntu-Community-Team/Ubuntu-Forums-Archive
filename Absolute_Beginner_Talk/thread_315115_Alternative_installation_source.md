---
title: "Alternative installation source"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by drew boardman on 2006-12-08
Hi,

I have an old Compaq laptop that does not support booting from USB devices,( floppy, HDD, or CD-R only)

To install 6.10 I downloaded the iso and burnt it to CD. So far so good.

I do have a USB dvd writer and a 6.10 dvd.

Having installed using the CD it always goes back to the CD if I want to install anything, but being an old and dodgy CD player, it doesn't work well.  Can I change the installation source, now 6.10 is installed, to the DVD?

Thanks for the help.

Drew

---

### Post by drphilngood on 2006-12-08
You should follow this guide:

[Enabling Extra Repositories]("http://www.psychocats.net/ubuntu/sources")

This will allow you to install from the repos and insure that you always install current versions of apps and get security updates.

---

### Post by az on 2006-12-08
> **drew boardman said:**
> Hi,

I have an old Compaq laptop that does not support booting from USB devices,( floppy, HDD, or CD-R only)

To install 6.10 I downloaded the iso and burnt it to CD. So far so good.

I do have a USB dvd writer and a 6.10 dvd.

Having installed using the CD it always goes back to the CD if I want to install anything, but being an old and dodgy CD player, it doesn't work well.  Can I change the installation source, now 6.10 is installed, to the DVD?

Thanks for the help.

Drew
Insert the dvd into the drive when you are at the Ubuntu desktop.

If the package manager does not come up, run

sudo apt-cdrom -d /dev/sda add

That is assuming that your USB device is sda.

Then it should use the dvd as a repository.

---

### Post by drew boardman on 2006-12-09
Thanks for the help.

The repos guide was great but didn't help.  Maybe I'm missing something.

The terminal route didn't work either as my DVD writer is not recognised as SDA but it is there and working.

Screenshot attached

Note, for some reason Floppy 1 is my DVD writer under /media.

Thanks again for the advice.

Drew

---

