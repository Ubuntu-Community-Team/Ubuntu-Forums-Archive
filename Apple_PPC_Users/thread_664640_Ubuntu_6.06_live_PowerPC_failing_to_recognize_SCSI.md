---
title: "Ubuntu 6.06 live PowerPC failing to recognize SCSI harddrive"
date: 2008-01-11
forum: Apple PPC Users
---

### Post by Joseph R. Watt on 2008-01-11
I am attempting to install Ubuntu on a PowerMac G4. versions 7.04 and 7.10 would successfully open an ash shell, but would not create any GUI or proceed past the barest beginning stages of booting.

6.06, however, without any boot options required, successfully shows the splash screen, and boots all the way to the GUI. I can play games, watch videos, et c.

However, the Install program recognizes no hard drive. gparted similary will only identify the CD-Rom drive. in /dev there are no sd?? devices.

The system profiler, or whatever it's called, does indicate the presence of a SCSI card, but doesn't give any options to do anything with it.

I haven't tried to install a Linux installation in years, and in the past it has only been on AMD and Cirrus based systems. What I did know about those systems, I've forgotten.

How can I get the installer or any fdisk/partition manager/whatever to recognize this drive? I've tried getting Ubuntu to install itself in thin air, but it seems to want some sort of device to write itself to.

I've posted on the Technical Answers System and gotten no answers at all. Please, please help me here!

Thank you in advance,

Joseph

---

### Post by stream303 on 2008-01-21
Assuming the hard drive itself isn't truly dead, I've had luck with hardware not showing up properly by resetting the pram, nvram, and pmu at times and then following up with the install.

Check out these apple docs for various ways to do this on different machines:

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

---

### Post by Joseph R. Watt on 2008-01-21
> **stream303 said:**
> Assuming the hard drive itself isn't truly dead, I've had luck with hardware not showing up properly by resetting the pram, nvram, and pmu at times and then following up with the install.


If the hard drive IS dead, then Mac OS 9.2 is a LOT more cleverly designed than I realized, since it still boots, and is functional. I probably knew what pram nvram and pmu were once upon a time but I have been fortunate enough to have the opportunity to forget completely.

Thank you for the link. I'll post here again after I try that.

Joseph

---

### Post by Joseph R. Watt on 2008-01-21
No change. Hard drive remains undetected. No /dev/s?? entries.

---

