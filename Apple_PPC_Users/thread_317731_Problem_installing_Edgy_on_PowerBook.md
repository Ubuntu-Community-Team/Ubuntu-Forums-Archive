---
title: "Problem installing Edgy on PowerBook"
date: 2006-12-12
forum: Apple PPC Users
---

### Post by underdude on 2006-12-12
I'm stumped.... :confused: 

1. I downloaded the desktop PPC iso for my PowerBook G4 10.3.9...
2. Burned the iso using the instructions on the ubunto site...
3. Rebooted my mac (holding 'C' after reboot)...

Then I run into the issue...

The screen flickers for a second then goes to a black screen with a print out of this:

[I]Welcome to Ubuntu 6.10 (Edgy Eft)!

This is an Ubuntu live CDROM,
built on 20061025.

The default option is 'live'.

If the system fails to boot at all (the typical
symptom is a white screen which doesn't go away),
use 'live video=ofonly'.

Press the tab key for a list of options, or type
'help' for help.

************************************
If in doubt, just press Enter, and if that
doesn't work, type 'live video=ofonly'.
************************************[/I]


then something like this:

[I]Welcome to yaboot 1.3.13
boot:[/I]

then when I hit enter, or choose any of the available options from the help menu (or using *video=ofonly*), it spins the disk up and says:

*Please wait, loading kernel...*

then the disk spins for a few minutes and then prints out:

*read failed*

--nothing inbetween this sequence happens (that I can see on screen)...

-- and puts me back to the "*boot:*" prompt

Any clues on why this is happening and why I am not going directly to the graphical interface with the install menu?

Thanks for any help you can give..... ;) 
Chris

---

### Post by dshan on 2006-12-12
It sounds like your CD is faulty. Did you burn the iso image to a CD-R or a CD-RW disk? I'd try burning another, preferably a CD-R (and maybe at a slower speed than whatever it's defaulting to - I think I used 8X (it wouldn't work at 16X/24X if I recall correctly). If you get the same error after doing that then it might be a corrupt iso image, try downloading it again (from another mirror perhaps).

---

### Post by pauljwells on 2006-12-13
I found thst I had more success burning boot CDs using the freeware program Firestarter.

---

