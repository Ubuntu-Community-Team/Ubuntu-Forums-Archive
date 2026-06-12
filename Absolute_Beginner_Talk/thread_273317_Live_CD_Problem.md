---
title: "Live CD Problem"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Sharps4570 on 2006-10-07
Hi All..Im probably too old to learn Linux but I like the challenge. Im wondering if my machine may be the problem..Compac w/3000+ amd, 256 MB onboard video and audio. I burned the dvd, verified it, and rebooted..If i use the "start or install option it loads a high res bar at top and bottom of screen and little else..If i boot in safe graphical it loads those tool bars and shows two desk top icons..install" and "examples". It also loads a nice looking wallpaper. I CAN right click the options at the top..."system, applications etc..and it will sometimes slowly show what is available under applications..but clicking them or hitting enter does nothing..I wondered if the res was too high for my system?..Any ideas?

---

### Post by CatKiller on 2006-10-07
The Live cd doesn't perform as well as having it properly installed - everything needs to be read off the disk and loaded into RAM. The amount of RAM that you have is at the lower limit for the Live cd to function, especially because your integrated graphics are likely to be using some of that.

By all means play with the environment that you're in, but you'll have a much better experience when you take the plunge and do the install. It might be best to use the text mode to install - some people have reported problems using the graphical install process in borderline cases.

No one is too old to learn. Welcome to the community.

---

### Post by Sharps4570 on 2006-10-08
catkiller..Thanks a lot for your reply..If I do a "text install" or actually install to my hard drive, will it install its own dual boot utility? I had previously installed Red Hat on another computer..I had installed a second hard drive so I didnt chance mucking up my Windows..That one had its own dual boot utility and it functioned well..Also From a "text install" will everything be command line? or will i still have some graphics?..Thanks

---

### Post by handy on 2006-10-08
I bid you welcome too... :) 

The dual boot facility - **Grub** - is part of the install if you choose to dual boot.

The graphical install is a little friendlier than the text one...

Will you be able to access the forums via another computer?

If you could, it would certainly take any strain off you, you could get answers as you go through the install, just in case you needed some.

I'm 51 & nowhere near too old to learn linux... :KS

---

### Post by xpod on 2006-10-08
The "Alternate cd" is just as easy to use as the live cd.
It has a gui of sorts to work with but its all text based choices.
It`s really easy to use and if you already got the partition
ready for ubunto then its even easier.Just leave it unallocated
and point the installer towards that space when you get to that stage.

I got an old compaq too that originally had even less memory than you and the alternative cd is what i use for it.

Good luck

---

### Post by CatKiller on 2006-10-08
You do get some graphics with the text install, comparable to a windows install - low-res fonts and menu items you can select with the keyboard, that kind of thing. Works well though.

GRUB will be installed as part of the process, by default to the MBR of the Primary Master. Are you planning on having Windows installed on this computer as well? If so, you probably want to read up on others' dual-boot experience, since there's a possibility that GRUB and the Windows bootloader will mess with each other.

Good luck, and don't forget to ask more questions **before** you get stuck. Much easier to help, that way.

---

