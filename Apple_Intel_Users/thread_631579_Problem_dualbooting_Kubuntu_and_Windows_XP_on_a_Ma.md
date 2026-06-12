---
title: "Problem dualbooting Kubuntu and Windows XP on a MacBook"
date: 2007-12-04
forum: Apple Intel Users
---

### Post by JParishy on 2007-12-04
Right. So I made a few stupid mistakes and K am not sure how to go about fixing them.

First, I have a MacBook C2D that I took Mac OS X off and it ran only Kubuntu for a while. Then I found the need to use Windows, so I resized my partition and installed Windows XP Professional on the leftover space. Now, afterwards, I completely regret this. Apparently, you should install Windows first, then linux, something I was unaware of.

Now, the problem is that I cannot get back into Kubuntu! The Windows bootloader goes automatically into Windows. Now I did try to fix this. Below is what I did.

1.) Downloaded VMWare Player and a gentoo livecd.
2.) Created a configuration file for gentoo w/ WMWare Player.
3.) Ran the gentoo livecd and ran console.
4.) Typed, 'dd if=/dev/sdb1 of=linux_boot.bin bs=512 count=1'
5.) Mounted my real HDD.
6.) Copied the linux_boot.bin from the virtual harddisk to my real HDD.
7.) Put the linux_boot.bin in 'F:\linux_boot.bin', where F:\ is my HDD.
8.) Changed the timeout in 'F:\boot.ini' to 10 seconds and added 'F:\linux_boot.bin="Linux Booter"' to it.
9.) Restarted Computer.
10.) The Windows bootloader came up and I chose "Linux Booter", but windows gives me an error about incompatible hardware when booting, which makes no sense to me...

I've exhausted my last effort, and I am hoping someone knows what to do.

Just so we are clear, the MacBook has no editable BIOS settings so I cannot boot my computer from a livecd or change which partition to boot from. I need to do something either from Windows or inside the gentoo livecd to fix this.

All help is 100% appreciated. Thank you!

-JParishy

---

### Post by Grey Box on 2007-12-04
Erm, well, I used rEFIt to get the mutliboot thing happening, and I never got rid of my OS X partition but squeezed it down to a minimal installation and kept it (just-in-case). 

However on previous installations where I have trashed my booting by installing windows *after* having instaled ubuntu, I did the following (which is NOT the best approach but it works and helps me in the future):

I got a copy of DSL (Damn Small Linux), created a tiny partition for it (say, 100mb), and did a hard-drive install of it. Insodoing DSL finds and adds all the alternative OS's in its boot menu. 

The 100mb partition should-have-been a boot partition (but who has a boot partition first off, right?), but DSL is a good compromise because it gives me a rescue OS when the **** hits the fan.

Worth a try anyhow, I guess.

---

### Post by cyberdork33 on 2007-12-05
just install grub. Don't mess with the windows bootloader. See the link in my signature.

---

