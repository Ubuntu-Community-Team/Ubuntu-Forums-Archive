---
title: "Ubuntu 9.04 / rEFIt / can't boot into Mac OS X"
date: 2009-06-15
forum: Apple Hardware Users
---

### Post by discosucker on 2009-06-15
Hi,

I'm running Mac OS X and Ubuntu 9.04 in dual-boot setup with rEFIt on Macbook (5.1).

Here's the problem:
After updating Mac OS X to 10.5.7 (combo update) ...

1) the rEFit menu is gone
2) I get Macintosh HD and Windows (sic!) when hitting "alt" on start up
3) can boot into ubuntu and even browse the Macintosh HD from there
4) can't boot into Mac OS (blinking folder)

So the files are there, but there seems no way to get Mac OS X to boot.

Any ideas how I could get this fixed?

Thanks
Disco

---

### Post by jjrecort on 2009-06-17
I have a similar problem.

I have a brand new Macpro.
2 HDD one for MACOS X and another for UBUNTU
I have installed Ubuntu 9.04 on the second HD without any problem.

but upon restart... the mac wasn't restarting. (white screen with blinking folder)
pressing the ALT key to select the booting device is not working anymore.
the Computer only boots from CD.

I have installed again Ubuntu from the CD this time, assigning the boot thing to the second hard disc.

Now I can boot form the Ubuntu HD and see the MacIntosh HD (as the previous post)
But I cannot boot from the Mac OX Disc.
I have tried to install (formating the disc) the MAC OS X again..
now the ALT key on reboot is working but I only see the Ubuntu devices (HD and CD)

How Can I boot from the MAC OS X HD?
it's the Mac Boot manager lost/damaged forever?
It's a new mac! and is not mine!

thanks!

Note: I'm absolutely newbie in the linux/Ubuntu world...Advanced mac user for 20 years!
but I want to learn new things!

thanks again!

---

### Post by cyberdork33 on 2009-06-17
the multiple disk capability is a bit unique on the mac pro and can require some special handling. boot from the OS X dvd and see if you can select your OSX partition as the startup volume. I think that may be your issue.

---

### Post by jjrecort on 2009-06-17
Thanks!

I already tried, and yes I see the MacOX HD.. and I can select it in the startup disk app.

but when I restart it boots again from the DVD..

if I reboot and hold option key.. then I see only the DVD and the Ubuntu HD...

Should I install the reFit?

thanks again!

---

### Post by cyberdork33 on 2009-06-17
> **jjrecort said:**
> Thanks!

I already tried, and yes I see the MacOX HD.. and I can select it in the startup disk app.

but when I restart it boots again from the DVD..

if I reboot and hold option key.. then I see only the DVD and the Ubuntu HD...

Should I install the reFit?

thanks again!
you would need to boot into OS X to "install" rEFIt. There is a CD image though so you can make a bootable CD.

Have you tried taking all other disks out of the machine?

---

### Post by jjrecort on 2009-06-17
This was my next try... to take out the second disk with ubuntu.

I just readed your guides, and I finally undestand what is Refit...

all of this is so new to me! and I didn't knew what was refit.


thanks for your guides!

and your help!

---

### Post by jjrecort on 2009-06-19
I already tried...

it's not booting... blinking folder

if I press the ALT key upon booting, then stays on the gray screen without listing any device.


How can I revert this and go back to the original MAC OX EFI boot?

this computer is not mine!

thanks!

---

### Post by jjrecort on 2009-06-20
SOLVED!

first,

just a note to clear that when I said ALT key it's option in the US keyboards

if it can help to others,
this is what I did to lead to the problem.

1. open a new macpro and complete the preinstallation
2. install a second brand new disk in bay 2 (no formated)
3. boot with LiveCD
4. Install Ubuntu 9.0.4 with the default settings in disk 2 (didn't touch anything on disk 1)
5. reboot.

what happened?

the Mac was not booting (blinking folder)
then,

rebooted with option key pressed > ligth grey screen > nothing
rebooted with liveCD > LiveCD booted with no problem

what I did then?

1 reinstall again ubuntu this time modifing the booting info at the computer (can't remeber exacly the letters)
2.again I didn't touch the disk 1 (macosx)

result > the same behavior

third try

1. reinstall again Ubuntu from LiveCD on disc2
2. this time in the advanced booting I set the booting to the disk 2
3. again I didn't touch the disk one

results

voila!

1. Macpro booted from Ubuntu, great!
2. From Ubuntu I can mount and browse the disk 1 (macos x)

I tougth I was done!

then I restart pressing the option key to reboot from the Mac OS disk
and on the Boot manager I only got the Ubuntu HD marked as "WINDOWS"
no trace of the Disk 1 with MAC OS X

what I did:

1. booted with MACOSX DVD
2. the MACOSX DVD recongized the 2 discks! Ununtu and Macos
3. I tried to set the "startup disk" to the Mac OS X disk, but was not working
4. I Installed again the MACOX on disk 1 erasing the disk

and nothing!

5. I tried to physically take out the 2nd disk with ubuntu > same behavior

at this point Is when yesterday I wrote you in the forum.

and this morning some fresh idea come to my mind, and Voila! worked!

so HOW I SOLVED THIS.

1. booted with MACOSX DVD
2. Launch DISK UTILITY > the MAC OSX Volume is recognized and mounted
3. REPARTITION THE DISK
4. I Installed again the MACOX on disk 1


SOLVED!, now boots with the MACOS X!

now I'm finishing to update the MACOS X.. as soon is finished I will plug again the disk with Ubuntu and check if is still working and I have a neat dual boot.



Thanks for all,
And Sorry for my English if have lead to some confusion
I'm Catalan, so English is not my mother tonge.

---

