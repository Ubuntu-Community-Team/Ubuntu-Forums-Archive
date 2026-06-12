---
title: "Acer lcd won't resume from suspend"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by linuxhippy on 2007-05-17
I have an Acer AL1711 lcd monitor that stays black with the no signal (orange) light on the monitor when I try to resume from suspend.  The keyboard works to reboot the pc blind using CTRL-ALT-Backspace, CTRL-ALT-Delete.  The pc is resuming from suspend but the monitor is not.  I'm using Ubuntu Fiesty on an AMD Athlon64 pc.  How can I make the monitor resume (off/on doesn't wake up the monitor either)?

---

### Post by k33bz on 2007-05-17
did you check your vid card and its driver

---

### Post by linuxhippy on 2007-05-17
my video is integrated with the mobo....it uses an ATI Radeon chipset and sudo lspci gives this:

 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

I specified 32 MB of RAM for the video but it can go up to 128 MB.

---

### Post by k33bz on 2007-05-17
mmm, try a live cd, see if you get any vid response.

---

### Post by linuxhippy on 2007-05-17
I have the same suspend problem in Fedora Core.  I've lived with the problem for a couple years but would like to figure it out.  I have a lot of live cds-which one should I try?

---

### Post by k33bz on 2007-05-17
I would use any of the live cds you may have that runs diagnostics.

---

### Post by linuxhippy on 2007-05-17
Do I need to have the GNOME desktop to make it go into suspend?  That's the only place I've seen Suspend/Hibernate when you logout...except in Ubuntu there is also such a screen in XFCE.

EDIT: I have WinXP-Home on another partition that make it suspend and resume just fine.

---

### Post by linuxhippy on 2007-05-17
ok, I just downloaded the Paldo Linux Live CD that came out earlier this month and it uses the GNOME desktop.  I burned it and it booted fine.  lspci showed that it was using the same ATI Radeon chipset that Ubuntu and Fedora Core are using.  I put it in suspend and the pc came back at the press of the power button but the monitor didn't.  Maybe the ATI Radeon chipset cannot handle suspend?

---

