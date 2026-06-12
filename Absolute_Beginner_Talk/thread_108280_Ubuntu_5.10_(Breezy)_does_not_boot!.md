---
title: "Ubuntu 5.10 (Breezy) does not boot!"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by Drowzee on 2005-12-25
Hello, I am really an absolute beginner to linux.. and I have chosen Ubuntu to start off with.
I have downloaded the DVD iso for Ubuntu as well as the Install CD and Live CD and all three did not boot with me. I have absolutely no idea why. I set the bios to load the DVD-ROM drives first and still no success.. it still loads windows.
I use Windows XP Professional with SP2, my motherboard is the Gigabyte P4 Titan 848P. Don't know the bios version though, and this is not the first boot problem I have experienced with this mother board~~.
What i am planning to do however is install linux on a 20GB partition from my 200GB HD, that partition has already been made via partion magic and is now unformatted and unallocated, waiting for the Ubuntu Setup to do it for me^^.
Well if anyone has any idea on how i can solve this problem please do tell me, thank you.

*~Drowzee~*

---

### Post by kaamos on 2005-12-25
Did you burn the disc as an image? (look here [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto))

---

### Post by 23meg on 2005-12-25
What exactly happens when you insert the CD and power on? How exactly did you burn the ISO image? You should choose the "burn image" (or equivalent) option on your CD writing program, not the option the burn a regular data disc. 

Can you boot with other bootable CDs?

---

### Post by timfrost on 2005-12-25
If the images werer written to CD/DVD using rawrite, they should boot.

How did you write them to the CD?  And what do you see if you load the CDs and DVD under Windows?

---

### Post by ubuntuuser on 2005-12-25
Just make sure you did NOT just copy the iso file on the dvd. In your burning program, look for an option like "burn cd from image" or "write image to cd". If you put your cd in your drive and open it with the explorer, you have to see a lot of different files. If you only see the .iso-file, you did it wrong.

---

### Post by Drowzee on 2005-12-25
well first of all the files i downloaded were not in image format.. but they were zipped and after unzipping there were several files in a folder.. with the dvd after burning it i got an autostart window.. which to me meant it was working.. with the cds i just got data cds.. with no autostart and similar..
i will check the cd burning instructions and report back here..

*~Drowzee~*

::EDIT::
What I see when I load the CD in windows are several files, that is not the problem..
What I see when i Boot my PC with the DVD/CD in the Drive is this: in the Black window while booting it says: 
BOOT CD:
BOOT CD:
and then nothing happens and starts windows normally..
The way i burned the CDs/DVD is by unzipping the file i downloaded.. never noticed it was an iso file untill now because i could unzip it.. then i compiled a cd with all the unzipped files..

---

### Post by Roland Bouman on 2005-12-25
[QUOTE=kaamos]Did you burn the disc as an image? (look here [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto))[/QUOTE]

Thank you! This worked perfectly for me (being a total NOOB Windows XP user).

---

### Post by Drowzee on 2005-12-27
after reburning the dvd it booted perfectly.. thanx for the help.

*~Drowzee~*

---

