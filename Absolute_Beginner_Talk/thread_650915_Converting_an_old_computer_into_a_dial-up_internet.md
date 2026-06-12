---
title: "Converting an old computer into a dial-up internet sharing machine"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by ncosens on 2007-12-26
Using an old computer I want to install Linux on it and set it up as an internet sharing machine for the rest of my home network.

HP Pavilion
Intel Pentium II
96MB RAM
Windows 98 SE packaged (converted to Windows XP Pro)

This computer still runs great and is wicked fast.  Well it was for Win 98, then I put XP on it because Microsoft stopped support for 98 when we got my mom a laptop for x-mas last year.  Worked well with SP1 and a little slower with SP2 but still better than some newer machines. Because the cable company won't be putting a line down our road anytime soon and we are too far from the service building to get DSL and because Satellite is too expensive we are stuck with dial-up, fast dial-up though with an average of 49.2 kbps. (about 5.7 Kilobytes per second pre-compression).

I have tried to install Ubuntu 7.04 on it but failed 5 times, each for a different reason.  I thought it might be the CD-ROM drive because there were a bunch of timeout messages and data read errors.  So I plugged in the CD drive from my computer and tried it. Wow it was faster, and no errors or timeouts.  Each time it boots I get this message "[0.000000] ACPI: Unable to locate RSDP" whatever that means then it continues to load.  Everything seems fine until it gets to the point where it tries to start the X server.  I outputs a blue screen with a bunch of crazy characters meant to be the border of a message box and a message that reads:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output  to diagnose the problem?

with a Yes / No choice.   I selected Yes and it output a bunch of text.  Everything seemed normal with 2 key lines reading: (EE) = error

   (EE) No devices detected.

   Fatal server error: not screens found

and an OK button.  Choose OK and it outputs a choice to view an extensive detailed output of stuff then a message "The X server is now disabled. Restart GDM when it is configured correctly.  Choose Ok to close the message and the computer stops progress on booting altogether.

Then I tried installing Ubuntu using my computer with the hard drive from the HP.  That worked but when I put the hard drive back in the HP and boot up I got the same X server issues.  I can though access text mode from there.


Now what I want is some tips on how to resolve this issue so that I can get a working copy of Linux, preferably Ubuntu because I am most familiar with that system, installed on the HP machined so I can set up a dial-up sharing server.  By the way, I'm am relatively new at Linux (September 2007) so go easy on the terminology.

Thanks

---

### Post by Kitsun on 2007-12-27
Those ACPI errors are common, my laptop gets them, but it works fine.

As with X not starting, its most likely a problem with your graphics card.

---

### Post by oldos2er on 2007-12-27
With those low specs, I'd try a distro like DSL or Puppy Linux.

---

### Post by ncosens on 2007-12-31
Thank you oldos2er.  I tried Puppy Linux and it works beautifully.  Now on to more challenging features like dial-on-demand and such.

---

