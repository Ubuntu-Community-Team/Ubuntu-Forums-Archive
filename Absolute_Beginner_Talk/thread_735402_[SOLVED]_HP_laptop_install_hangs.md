---
title: "[SOLVED] HP laptop install hangs"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by SparkyUSN on 2008-03-25
I'm attempting to install Gutsy on a new HP Pavallion dv7600t and am failing.  I've looked at the HP dv7xxx guide but none of the bootline fixes are working for me.

**hardware specs**

Intel Core 2 Duo Pprocessor T7250 (2.00 GHz, 2 MB L2 Cache, 800MHz FSB)
4GB DDR2 System Memory (2 Dimm)
NVIDIA GeForce 8400M GS
Fingerprint Reader + Webcam + Microphone
120GB 5400RPM SATA Hard Drive
SuperMulti 8X DVD+/-R/RW with Double Layer Support

The CD images I've tried all have good hashes.

I edited the boot line of the 64-bit live CDs to remove quiet and splash to avoid the known problem with the splash screen.  The live CD then hangs with "starting bluetooth services."  I can hit return to get a command prompt and start x ("startx") manually, but the installation program then hangs at 90% with "detecting hardware" and "loading usb-storage for USB storage" displayed.

The one time that I've avoided all of the above was when I booted the 32-bit image (I've tried them all) with the noacip acpi=off options.  With those flags, the live CD booted normally and the OS installed.  When I boot from the hard drive, however (editing the grub line to remove quiet so I can see what is going on) it hangs at "starting bluetooth services" and shows, "frequency scaling not supported" where I would expect to see "[OK]".

I've tried the alterate install CD (64-bit) but the "detect hardware" step fails despite my many attempts to run it.

It seems clear that I have hardware compatability issues, but I don't have the knowledge to get a wrench on the problem.

I have 7.10 running on my desktop and love it.  I'd really like to get my new laptop cooking and am willing to work to make it happen.

Can anybody help?  Thanks in advance.

---

### Post by (((X))) on 2008-03-26
Hi 
Perhaps this is a bug or something
Do you need bluetooth services?
If not, you could disable them to start up.
sudo -s
echo blacklist bluetooth >> /etc/modprobe.d/blacklist
removing all bluez, bluetooth my also work.

---

### Post by SparkyUSN on 2008-03-26
I'll give it a try . . . only how do I get to the command prompt prior to starting to boot the live CD?  Alternatively, how do I restart the script that has the bluetooth services in it once I stop it by hitting return?

I believe that the machine has no bluetooth hardware installed (it was an option that I did not purchase).

Thanks again.

---

### Post by SparkyUSN on 2008-03-26
Also, a typo:  It is a dv**6700**t, not 7600.  And that is the dv6xxx guide.

---

### Post by SparkyUSN on 2008-03-29
I've found the solution.  My computer has no bluetooth device, so I disabled the bluetooth service.  Blacklisting the service did not do the trick.  What did work, however, is to remove the bluetooth startup script.  This is located at 

/etc/rc2.d 

and is called S25bluetooth (though I think that the numbers can be different).  By changing capital S to a lowercase s, the start script can no longer be found (case sensitive).  So I used this:

sudo mv S25bluetooth s25bluetooth

---

