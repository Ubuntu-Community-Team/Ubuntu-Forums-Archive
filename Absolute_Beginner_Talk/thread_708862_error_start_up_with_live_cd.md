---
title: "error start up with live cd"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by slickh20 on 2008-02-26
yup i am new read below it will be obvious, thanks for any help!!


right after the first screen of ubuntu where it asks if i want to start or install, it starts checking for stuff but the first two lines that come up are

[199.656000] Buffer Error I/O error on device fdo, logical block 0
[237.868000] Buffer Error I/O error on device fdo, logical block 0

and then it starts checking a bunch of other stuff and most things are ok but there is a few items that fail,  sometimes it allows ubuntu to star other times it restarts itself and then other times the screen just goes into suspend mode i think and i have to hol in the power button and turn it back on.  

any suggestions?

thanks

---

### Post by glennric on 2008-02-26
Check to make sure that your copy of the live cd isn't corrupt.

---

### Post by slickh20 on 2008-02-26
have done this as well as download and burn a new cd.  i just got it to open under the second choice on the first screen the safe mode graphics or what ever it is i don't remember off hand.  but i have been here before and it freezes on me during install. i will try again here fingers crossed.

---

### Post by slickh20 on 2008-02-27
got it installed still have all kinds of problems so i am reinstalling and this same message came up again any one got any ideas?   thanks 
ps this is a new disk with a formatted hardrive

older system tho athalon 1.2ghz

ran windows xp ok before

---

### Post by glennric on 2008-02-27
I am not sure what device "fdo" is?  Should that be "fd0"?  If so that is referring to the floppy drive.  Do you have a floppy disk in the drive?

---

### Post by jcanini on 2008-02-27
Your pc should be quick enough.

When Ubuntu boots the first time it is running the OS of the CD so tends to run slowly.

Once it is installed on to your hard drive it should become more stable/responsive.

Partitions should be something like:
/swap                    1/2 to 1 g 
/                             the rest of you hard drive

---

