---
title: "can someone please explan why ubuntu wont work?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-09-09
my live CD isn't working right i cant use the ubuntu demo (put in disc and reboot) and i cant even install ubuntu?

---

### Post by hc2995 on 2006-09-09
ummm usually you have to go to the boot menu and change the boot menu from C:\ (or local disk either one) to D:\ (or IDE master (IE the CDrom Drive))

---

### Post by StarQuake on 2006-09-09
To get a better answer can you please explain, what steps you are taking and at what point it fails?

---

### Post by lordvolo on 2006-09-09
how do i IE the CD drive?

---

### Post by StarQuake on 2006-09-09
IE means in example.

---

### Post by taurus on 2006-09-09
> **hc2995 said:**
> ummm usually you have to go to the boot menu and change the boot menu from C:\ (or local disk either one) to D:\ (or IDE master (IE the CDrom Drive))
:confused:  :confused:  :confused: 

If you want to boot from your CD, just change it in the BIOS!!!

---

### Post by lordvolo on 2006-09-09
how do i boot from the CD drive!?!?

---

### Post by lordvolo on 2006-09-09
Bios?

---

### Post by taurus on 2006-09-09
You need to go into your BIOS and change the order of the boot process!  Make sure it says CD-ROM first, floppy second (if you have a floppy drive on your machine), and the harddrive...  Please look at your mobo manual on how to get into the BIOS but chances are either F2 or Del would be it!

---

### Post by jordanmthomas on 2006-09-09
When your computer first boots up, you can hit one of your F-keys (usually F2) to go into the BIOS setup.  Somewhere within there will be an option to set boot order.  Put your CD drive first.

Also, on my computer at least, I can hit F12 as it is booting and a menu asks me what device to boot from.

**got beat**

---

### Post by hc2995 on 2006-09-09
try the following:

DELL PCs F12 or F2

Others: F2 or F11 (sometimes F12)

so when you see the PC manufacturers logo hit one of those buttons to enter BIOS (bios=Basic Input Output Setup)

---

### Post by lordvolo on 2006-09-09
i pressed f2 or del and still doesnt work

---

### Post by taurus on 2006-09-09
> **lordvolo said:**
> i pressed f2 or del and still doesnt work
You need to look at the manual for your mobotherboard on how to get into the BIOS!!!  :rolleyes:

---

### Post by hc2995 on 2006-09-09
go to your manufacturers website and search for "BIOS" that will help :D

---

### Post by etomic13 on 2006-09-09
On my mother board (MSI) I have to press the DEL key. Then I go down to advanced then boot order. Call your motherboard manufacturer if you built the computer but it sounds you bought it from some manufacturer so call them if your still stumped as to how to change the boot order. we cant help unless we have some info like the manufacturer.

---

### Post by nickpaton on 2006-09-09
Switch off your PC.

Put your finger over the Del key, F2 key, F12 key but don't press them yet.

Switch on the PC.

IMMEDIATELY start pressing the Del key a few times, then the F2 key a few times and then the F12 key a few times.

If your PC starts up in Windows again, shut down Windows, and switch off the PC.

Repeat the above steps and by repeating this should take you into the BIOS screen.

When you are in the BIOS screen, look for a title which could be Advanced, or Boot up Options (or similar).

Under one of these titles look for Boot up Devices (or similar); you will see listed maybe floppy disc first device, hard disc or HDD second device, CD third device.

You can change the order which these are listed, and you need to make the CD to be above the hard disc.
Change the order by using the up & down arrows on your keyboard, and the Enter key.  This will give you a list of start up devices, and I suggest you adjust the list so that you have first floppy disk, then CD, then hard disc.

This means that when you insert a bootable CD, it will run before the hard disc does. 

If you are still having problems, so as to help you further, please tell us the make and model of your PC.

Welcome to the forums and Ubuntu - we are very happy to help you!

---

### Post by Irony on 2006-09-09
If you look at the screen as it boots up it will tell you what keys to push - you have to look close as it only lasts a few seconds.

Once you are into the BIOS use the arrow keys to navigate and look at the instructions - you need to make the computer look at your CD drive when booting up.

---

