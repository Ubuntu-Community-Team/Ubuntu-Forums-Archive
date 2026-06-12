---
title: "Need To Get Ubuntu Working Properly"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Kaiten on 2006-06-16
Keep in mind that I'm a very experienced Windows power user, but have limited (at best) experience with Linux. So be sure to explain exactly what to do, at least enough to make sense to a Windows user.
A few days back I installed Ubuntu 6.06 with the Alternate Install CD (since I only have 128MB of RAM and can't boot with the Desktop Live CD). It installed without incident, but there were some hitches. The first problem I found was exactly the same as encountered in [this thread]("http://www.ubuntuforums.org/showthread.php?t=196862&highlight=644"). I managed to bypass this by using Ctrl+Alt+F1 to boot into the desktop using the root account. But I'd like to be able to log onto the account I made and not log on as the root.
The second problem is that I can't run the screen at 1440x900. I own a 19" widescreen LCD and 1440x900 is its native resolution. I don't like running at 1280x800, which while it works, the downscaling is pretty obnoxious. The LCD is connected to a GeForce 2 Ti if that helps at all.
So I tried (unwisely) to edit the settings and messed up the file, making booting into Gnome impossible. So I uninstalled and will reinstall as soon as I can resolve these problems.
Also Ubuntu made a 361MB swap partition, I'd like to know how to reintegrate  itself back into the primary partition like it was before.

The official stats on my PC:
--Slot A Athlon Irongate 700MHZ
--MSI E6191 Slot A Motherboard (With the newest BIOS circa 2000)
--128MB PC-100 SDRAM
--30GB ATA66 & 320GB ATA100 Hard Drives
--52x32x52 Rosewill RR-521 CD-R/RW
--Sony 16x40 DVD-ROM
--VisionTek GeForce 2 Ti 64MB
--Westinghouse LCM-19w4 19" LCD Monitor (native resolution: 1440x900@60Hz)

---

### Post by dermotti on 2006-06-16
backup your /etc/X11/xorg.conf

and run

sudo dpkg-reconfigure xserver-xorg

There should be an option in there for you rresolution.

If there isnt, download the nvidia-glx package and try the above again, except use the nvidia driver.

---

### Post by Kaiten on 2006-06-17
Great, all that's left is the login problem and the swap partition.

---

