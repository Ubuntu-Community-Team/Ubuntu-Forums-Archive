---
title: "Blank screen on install"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by NeilCC on 2007-01-06
I'm new to Linux and am having trouble installing. I've downloaded 6.06 and 6.10, (both AMD64 and x386 versions). When I try to boot from the cd everything seems fine and I get no error messages, but I always end up with a blank screen with a solid cursor in the top left corner and what sounds like African music playing. The outcome is the same no matter what version I try and using a text install makes no difference.

I'm running KN1 SLi Lite, AMD Athlon 4600 (x2), 3 x SATA (Not RAID), 2Gig RAM, 2 x NVidia 6800 XT 256MB and onboard sound.

Any tips or ideas, please?

---

### Post by fo3 on 2007-01-06
have you checked the media, it's an option on the boot up screen.
I know exactly what you're talking about though because it's happening to me too.  It's just before it initalizes the gnome GUI.
I just stuffed my system up and on re install I've had that blank screen, plus a lock up, but so far third time lucky.
fwiw in my case I think it's because the cd is old and scratched, or my old dvd rom is stuffed.

edit:  yep, froze again on reinstall.  Burnt a new cd, used a cleaner on the drive and now no problems, quicker too.  Before it took longer to load and seemed to scan the cd over and over on certain parts.
Are you using decent media and did a slower write when burning?

---

### Post by xyz on 2007-01-06
Hi folks,
You could try and start your box in "Recovery Mode" and run this to reconfigure X. See if it works and let us know:
```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by NeilCC on 2007-01-06
Thanks for the prompt response. I've checked all four copies for media errors and they are all fine. I've also tried the "repair" option and on restart I get "Restart GNOME Fail"
I've also tried "ACPI=Off" and "noapic nolapic" all with the same result.

---

### Post by NeilCC on 2007-01-07
I've also tried SUSE and Mandriva and have the same problem. If I try running "Live" the system hangs. I've installed the drivers for the graphic cards from NVidia and modded xorg as per their instructions. Still the same. Back to Windows.

---

