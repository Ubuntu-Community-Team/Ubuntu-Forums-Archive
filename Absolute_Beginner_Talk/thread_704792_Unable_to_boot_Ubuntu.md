---
title: "Unable to boot Ubuntu"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by DeadlyArts on 2008-02-22
I recently installed Ubuntu on my laptop, I got the drivers and everything, took like 3 days, but I managed to do it, but now, all i see is a black screen and "Press ESC to select boot option" and three errors, which appears for like 5 seconds then goes away, on the left upper corner of the screen. I really have no idea why this suddenly happened, I used it great for two days and then I went to restart it and there it was, I tried to do the recovery option from the boot menu by pressing ESC at the start up, but it only got worse after i got done doing the recovery, now all I see is a blinking white line on a black screen on the upper left corner. PLEASE HELP ME!

Laptop Specs: 
Model:            Toshiba satellite A215-S4757
Processor:      1.8GHz AMD Turion 64 X2 Mobile TL-56
Memory: 	2GB of 667MHz DDR2
Hard drive:	250GB at 4,200rpm
Graphics: 	128MB ATI Radeon X1200 (integrated)
Chipset: 	 AMD M690V
Previous OS: Vista
Thank you.

---

### Post by FreewheelinFrank on 2008-02-22
Will the computer boot from a liveCD?

If it will, then the installation may be messed up; if not, it may be a hardware issue.

---

### Post by DeadlyArts on 2008-02-22
It can, but I'm not really good with the terminal and stuff, maybe if you could help me out?

---

### Post by JoshuaRL on 2008-02-22
Can you actually get into Recovery Mode or not?

If not it sounds like a GRUB issue.  I would suggest using [SuperGrub](http://supergrub.forjamari.linex.org/) to fix it.

If you can get into Recovery Mode okay with no problems, then it might be a Xserver issue.  Xserver is the app that gives you the GUI of your choice.  If you can get into Revcovery Mode, try this:
```

login

```
It'll ask for your username and password, then do:
```

startx

```
If there are any errors,  make sure to write them down and post them.

---

### Post by DeadlyArts on 2008-02-22
I was able to get into the recovery
but it said user not authorized after I logged in even though I was on the main account.

EDIT: I've retried this and I got some more information, I'll copy it exactly the way it is on my laptop.

$startx 
X: user not authorized to run the X server, aborting.
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

---

### Post by DeadlyArts on 2008-02-22
Oh! I see, it worked now, I used the user "root" which I had no idea it existed. but yeah, I'm in and now I'm getting some error which says:

"User Switcher" has quit unexpectedly
If you reload a panel object, it will automatically be added back to the panel. 
And I clicked reload but it just keeps coming up again.

---

### Post by JoshuaRL on 2008-02-22
Can you logout, and back in to your user account?

If not, can you reboot into normal Ubuntu without using the Recovery mode?

---

### Post by xeth_delta on 2008-02-22
> **DeadlyArts said:**
> Oh! I see, it worked now, I used the user "root" which I had no idea it existed. but yeah, I'm in and now I'm getting some error which says:

"User Switcher" has quit unexpectedly
If you reload a panel object, it will automatically be added back to the panel. 
And I clicked reload but it just keeps coming up again.

Use the root account with care. Log-in as root **only** and **only** to do administrative operations. Never use it a regular account as that could be a security risk. Otherwise, you can run administrative operations with "sudo"

---

### Post by JoshuaRL on 2008-02-22
> **xeth_delta said:**
> Use the root account with care. Log-in as root **only** and **only** to do administrative operations. Never use it a regular account as that could be a security risk. Otherwise, you can run administrative operations with "sudo"

Very true.  And if you start messing with important stuff while root you can really hose your system.

Don't login as root unless its necessary or you have a specific purpose for doing so.

---

### Post by xeth_delta on 2008-02-22
Completely off-topic. JoshuaRL, nice avatar! Tux as Senna, right? My favourite F1 driver, too.

---

