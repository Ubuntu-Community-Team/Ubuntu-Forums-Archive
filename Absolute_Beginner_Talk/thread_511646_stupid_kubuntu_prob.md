---
title: "stupid kubuntu prob"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by buffylette58 on 2007-07-28
i seem to have a keyboard driver problem, which has only started since i've been playing with Kubuntu. 

ok, the keyboards fine, i've tested it on 2 other pc's, 1 with windows one with ubuntu, and it worx fine.

sometimes when booting up the pc, and it makes the system beep, then keyboard lights flash, and it will work...but most the time it won't... so it DOES work. and putting in a windows XP cd when booting up usually kickstarts the driver....

so yea, it seems to be a keyboard driver problem with kubuntu....

second problem, when the keyboard does actually work and i try to log in to kubuntu, it says: failed to start kstartupconfig. check installation....or sumthin

i've red around a bit but just can't find direct answers, sorry

any ideas ppl?

---

### Post by jamieh on 2007-07-28
Try the keyboard with an [COLOR="Red"]U[/COLOR]buntu LiveCD, if it works, I don't know what is wrong, if it doesn't, it may be the port you are plugging it into, try another one.

---

### Post by buffylette58 on 2007-07-29
thanx 4 the idea...

the same thing happend with an ubuntu liveCD...

so wot happens, we turn the computer on, and hear the system beep...sometimes the keyboard lights flash (caps, num scroll), and it will work....i test this by pressing 'esc' to enter to GRUB menu, or by pressing DEL to enter the BIOS settings....sometimes it worx, but most the time not...

sometimes the windows cd kickstarts it, gets it going again, but sometimes not...

the ubuntu liveCD didn't help.

is there something i can do with bios to help pick up the keyboard, (which will be hard to get into bios), cos its probly not a driver issue...

so yea, maybe it is the port on the back, (theres only the 1 ps/2 port, so its hard to test)

im sooo lost

---

### Post by buffylette58 on 2007-07-29
more info: i tried getting the keyboard going again, by running the winXP setup cd, and it worked....

but, it stopped working half-way through, with the error msg:
```

Setup cannot load the keyboard layout file Kbdus.dll. Setup cannot continue. Shut down or restart your computer.

```

microsoft say: [http://support.microsoft.com/kb/246187](http://support.microsoft.com/kb/246187) 
but its not even win2000 like they say, its winXP

and i have no idea how to convert their resolutions to get the keyboard going under kubuntu...

any ideas??

---

### Post by rillip on 2007-07-29
I suspect your bios has a setting that needs to be enabled, like usb keyboard support enabled, or usb support enabled.  Mine has keyboard and mouse, my wif'es only has usb devices.  You want the bios to initiate rather than the OS.  Might have teh same effect as changing the setting from "pnp os" to enabled/bios on some bios.

---

### Post by buffylette58 on 2007-07-29
i suspect the same thing, because when i first turn on the pc, i cannot press 'delete' to access my bios, even before the OS boots.

but it cuts in and out. thats the weird thing.... 

the win XP cd, with a bit of restarting, sometimes kick-starts it, and it starts working again..

so yea, now I'm thinking something with the bios...or a hardware problem? maybe the keyboard port is just dusty, or has a loose wire or something?

another keyboard doesnt work on this pc, and this keyboard worx on another pc...

HELPPP!

---

### Post by buffylette58 on 2007-07-29
ok, i went into bios settings, restored 'optimum defaults' or woteva...and the keyboard seems to be working now (3 out of 3!! lets hope it doesnt crap out again)

thanx 4 the help guys, appreciate it ;)

(now thers another kstartupconfig error, but i'll look around for an answer)

---

### Post by buffylette58 on 2007-07-29
keyboards crapped out again!

---

### Post by rillip on 2007-07-29
Step one: go to newegg.com

Step two: order a keyboard that doesn't suck

Step three: test it on another pc

Step four: test it on yours

Step five: if not working, then it's probably a motherboard issue. Try another port, if available. If not, curl up and cry in the corner.

---

