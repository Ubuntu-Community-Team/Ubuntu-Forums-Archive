---
title: "Display issues with Mac Mini (PPC)"
date: 2006-08-02
forum: Apple PPC Users
---

### Post by tdmckee on 2006-08-02
Hi there,

I had installed Ubuntu 5.10 from the ShipIt CD's without a problem on a partition I made of my Mac Mini's internal hard drive - and it ran fine, no problems.  I recently downloaded the Dapper Drake iso, burned it, and followed the instructions to install it over the older version.  I believe I tried to install without reformatting the partition, the installation freaked out, so I reformatted the partition it was on and re-installed, the second time having no problems with the install.  The problem comes when I reboot - well, two actually:  

- First, I am unable to boot back into Mac OS X.  The oS X partition seems fine (at least via a Drive Genius bootable CD), it just jumps from the boot loader to a flash of grey screen, and back to the boot loader.  

- The second problem is that I can initiate the booting into ubuntu, and the startup screen shows up fine, with the list of things loading, etc. - but when it gets to the login screen, the display appears confused - as if it doesn't know the width that the screen should be - the boot screen is scrambled such that it warps and wraps around the screen - see the attached cameraphone pic.  It appears that Ubuntu is operating fine outside of the display issue - in fact, the mouse appears as a normal cursor, which is weird - I can scroll to where the text box for logins should be, and a text input cursor appears, and I can in fact login, but I don't know my way around using key commands enough to sort out the display issue.  This happened both with a 1440x900 LCD monitor connected via DVI, and a 19" CRT using a DVI-VGA converter and VGA connector into the monitor.

I know that there used to be some methods to alter display settings at boot, I am just at a loss for how to modify those now.  Any help on how to fix either of these items would be most appreciated.

---

### Post by avtolle on 2006-08-02
Since you can log in, once you have done so, try this: get to a terrminal (alt+ctrl+F1), log in there, type dpkg-reconfigure xserver-xorg, select "vesa" as the driver and otherwise agree to the defaults if you don't know the default is incorrect for you, then when it finishes, type reboot. This may be all that you need; if not, post back. By the way, what video card do you have?

Edit: was just reminded that the above command, dpkg-reconfiugre xserver-xorg must be done as root; preface the command with sudo, please.

---

### Post by johnpernock on 2006-08-02
> **avtolle said:**
> Since you can log in, once you have done so, try this: get to a terrminal (alt+ctrl+F1), log in there, type dpkg-reconfigure xserver-xorg, select "vesa" as the driver and otherwise agree to the defaults if you don't know the default is incorrect for you, then when it finishes, type reboot. This may be all that you need; if not, post back. By the way, what video card do you have?

Edit: was just reminded that the above command, dpkg-reconfiugre xserver-xorg must be done as root; preface the command with sudo, please.

I have a problem, I have an apple 20" LCD Display and the problem is is tHAT WHEN I SELECT MY RESOLUTION, it gives me a wavy screen and i cannot see anything i cannot get it to work with the above command, is there something else i can try?

---

