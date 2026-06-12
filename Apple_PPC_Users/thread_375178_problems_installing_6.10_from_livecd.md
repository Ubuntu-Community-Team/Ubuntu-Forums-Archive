---
title: "problems installing 6.10 from livecd"
date: 2007-03-03
forum: Apple PPC Users
---

### Post by akcom on 2007-03-03
I'm trying to install Ubuntu 6.10 on a PowerBook G4 system.  The laptop is "clean" in that the partition table is wiped, no OS on it, etc.

The system boots from the livecd fine, and using the "check" boot option returns no errors.  Having said that, as soon as the "ubuntu" user is logged in, I receive the following error:
There was a problem registering the panel with the bonobo-activation server
The error code is: 3
The panel will now exit

I close this window by pressing OK and am presented with a bug-buddy panel stating that a backtrace was generated from /usr/libexec/evolution-alarm-notify.  After that, I get an error window saying "Nautilus can't be used now, due to an unexpected error."  Clicking "show more details" tells me that there was an unexpected error from Bonobo when attempting to locate the factory, killing bonobo-activation-server and restarting Nautilus may help fix the problem.

The problem is I don't have a bonobo-activation-server process running.  After all this, I am presented with only the upper panel (Applications, Places, System, and three icons) and a blank lower panel, along with the default unbuntu color background (no actual background picture).  I then goto System > Administration > Install.  The first window comes up, but is blank and shows "Step ? of 6" in the lower left corner.  Immediately after this, I get an "Installer Crashed" window.  The traceback eventually goes back to a call to datetime.datetime.today() (ValueError: microsecond must be in 0..999999).  Any ideas?

---

### Post by grazie on 2007-03-03
This looks like the well known gnome date bug. Details can be found [here]("http://ubuntuforums.org/showthread.php?t=35082") and elsewhere.

---

### Post by akcom on 2007-03-03
thank you very much.

---

