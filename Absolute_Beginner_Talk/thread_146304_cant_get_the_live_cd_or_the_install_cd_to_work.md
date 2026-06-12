---
title: "cant get the live cd or the install cd to work"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by onewaytrip on 2006-03-18
first a little info on my computer.  im running a dell with windows xp professional, 512mb of ram, intel pentium 4 with 2.40ghz. ok now been trying to check out ubuntu for a while but it keep freezing. when i reboot with the live cd it goes to the screen where it says this is the ubuntu live cd and the keyboard and every locks up, the same thing happens with install cd as well. please if you have any idea as to what my problem might be let me know. this is my first attempt at a linux os and i am dieing to get it up and running.
thanks in advance.

---

### Post by jpkotta on 2006-03-18
Are you sure your .iso files are uncorrupted? Did you do an md5sum check?  Your computer sounds pretty mainstream, it should work.

---

### Post by onewaytrip on 2006-03-18
the copy of ubuntu live cd and install cd i have are the ones they sent me in the mail from the ubuntu people themselves, if that doesnt sound right im very tried right now. anyways when i put the live cd in my cd drive while log on windows xp it runs ok lets me see all that preview stuff but when i restart my computer and boot from the cd it freezes at the "this is the ubuntu live cd" screen.

---

### Post by klahjn on 2006-03-18
Just a question....how many optical drives do you have? If you have more than one then i would try changing drives and restarting to see if that solves the problem.  I have had cases where my clients drives have gone flaky and start to crap out, but normally in that case, the drives prefer not to completely read bootable cd's first.  No idea why, just so happens that i've had that happen in about 3 cases.  If not available, i would try liveCD on another machine to ensure the disc is fully functional.

---

### Post by onewaytrip on 2006-03-18
i only have one drive i just try the live cd on my brother computer and it seems to work so still no clue on the problem with my computer. i was wondering is there any other way to boot the live cd or install cd other than from the cd drive? oh and a little info on my drive, its a dvd/cdrw if that helps.

---

### Post by sudomania4 on 2006-03-18
NM, i didn't read the post well enough.

---

### Post by jpkotta on 2006-03-18
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

---

### Post by catlett on 2006-03-18
I went crazy a few months ago installing another distro on my other computer. The iso checked out, I used it before etc. Long story short my dvd-rom drive was no good or not good enough for install. It worked every other way (reading cds and dvds) but not to install. I have 2 drives and switched them (changing the master/slave relationship) and the disk installed with no problem. I don't know how to install without booting from the install disk but a second dvd drive isn't that expensive and is convenient to have these days on your system. (Plus it is pretty easy to install a second drive. I'm not too bright and I did it . The only area that I messed up first but then fixed was setting the jumpers correctly so one is a master and the other is a slave). Good luck.

---

### Post by Randomskk on 2006-03-18
Maybe it's not freezing, but instead is just not reconising the keyboard - a friend of mine has a USB keyboard that for some reason cannot type anything on the boot screen (not even hit enter to go into the setup) but the PS/2 keyboard he tried seemed to work.

---

### Post by onewaytrip on 2006-03-18
i am using a usb keyboard so that may be the problem ill try the original dell keyboard that came with the computer. if that doesnt work ill just connect another cd drive and hope for the best.

---

### Post by onewaytrip on 2006-03-18
ok everyone thanks for the help finally got it to work the problem was the usb keyboard. so far loving the live cd and ready to install os now but just one more question before i do so. ok since im running a dell pc and at start up it allows me to choose where i want to boot from, is it ok for me to install ubuntu on another partition on the same harddrive with windows xp and boot using the dell boot or will i still have to download a dual boot app.

---

### Post by jpkotta on 2006-03-19
Ubuntu will install GRUB (Grand Unified Boot Loader) by default, and it should find Windows and add an option to boot it as well.  You shouldn't have to bother with any BIOS boot options.

---

### Post by onewaytrip on 2006-03-19
thanks finally got ubuntu install. its great but i cant get my internet to work on it. i use the linksys wireless network adapter for my internet, i dont have a isp of my own so i just jump on signals nearby. will i still be able to go online using this method on ubuntu like i do in windows. its sort of a pain having to switch between os just to go online and i really would like to spend more time on ubuntu.

---

