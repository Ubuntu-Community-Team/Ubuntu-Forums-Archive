---
title: "ubuntu dapper 6.06.1 live cd hangs up"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by mixmaster87 on 2006-12-10
hey, im new to linux, but have been thinking of switching to it from windows for at least a year. i just got started with it and downloaded "ubuntu-6.06.1-desktop-i386.iso" i burned it, and booted it on my comp, but it randomly hangs up! i wanted to learn how to use the os first, but decided to just start installing, but no matter what i do, it hangs up before i get to complete anything. i burned the disk 3 times, got the same result on each and one of them. it works fine on my laptop.

I'm absolutely positive its my cd-rom that does this. i cant eject my cd-rom at any time when it hangs up. sometimes when i boot it even says "boot failure" in bios. it works better if i let it cool down for 5 minutes.

is there something i could do to prevent this from happening? or at least try to keep it going just a little longer so i could complete the installation? thx in advantage

---

### Post by Kobalt on 2006-12-10
Hi,
first of all : have you checked the integrity of the CDs you burned ? If not, you might want to do this first, just to be sure, using [this]("http://www.nullriver.com/index/products/winmd5sum"). Then, for burning ISOs, I always suggest burning them slowly, not faster than 12x actually (for CDs). 
Then, if you're sure it's your drive that is buggy (I actually had the same problem, on an old laptop) I suggest you try opening the computer case, or placing a fan close to your drive. And of course, do not use the computer before you attempt installing Ubuntu. 
Launching the LiveCD requires a lot of actions from your drive, booting a LiveCD session before you can install Ubuntu. You could use the [Alternate CD]("http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/") to install Ubuntu straight at boot. It's not a graphical installation but it's basically the same thing as the graphical installer.

Hope it helps,
Cheerio :rolleyes: !

---

### Post by mixmaster87 on 2006-12-10
i have checked the hash file yes, it matches with the one on [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes). and the last cd, i burned it at x20 at least. and i guess my cd-rom isnt bugging. its relatively new, and never had problems with it, and i already have opened the case and used a table fan right next to the cd-rom:P il have a look at that install-on-boot img and try again. thx

---

### Post by Kobalt on 2006-12-10
Yes then I guess you should try the Alternate CD... For some mysterious reasons LiveCDs sometimes cause random crashes... Good luck !

---

### Post by Sef on 2006-12-10
> i burned it at x20

You should not burn an iso at more than 4x or otherwise the burn can be bad.

---

### Post by mixmaster87 on 2006-12-10
i downloaded and burned the alternate disk, formated and installed it, but it froze many times (though ejecting the cd tray and put it back in it started working again, even though i dont think it was healthy) but the install failed at installing grub and that other boot manager something thingy (lilo or something) so i had to finish of the installation without them, and i got boot failures in bios. it said that my architecture or something didnt work with grub or lilo (or what ever that was:P) is there something i could do to fix that? or should i go for the amd64 version, or go to edgy eft?

---

### Post by mixmaster87 on 2006-12-10
bump cause i have to go soon, and then it would be to late to start downloading another version of ubuntu since i got to get up early tomorrow.

you see my computer specs in my signature, if the version i have tried to install wont fit my hardware someone could direct me to the right one.

---

### Post by mixmaster87 on 2006-12-10
i got it going in the end:D got it installed and everything. thx for the help, guess i never could do it without you:P

---

### Post by max.diems on 2006-12-10
if nothing else works, use a different ISO from a different mirror (eg, xubuntu instead of ubuntu). Also, it sounds like it boots, but if not, be sure you burn the ISO, not a file

---

