---
title: "can't boot from live cd"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by tentel on 2007-11-30
i know there are similar problems to this, but from what i've researched, i can't seem to find anything else like my problem.




i have an HP laptop running on vista, and when i try to boot 7.04 from the live cd (which i have checked the integrity of), everything starts working fine, and then during the bootup text, i get this error:

firmware-helper [5916]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver 
'(unknown)' [   313.187350]bcm43xx: error: microcode: "bcm43xx_microcode5.fw" not available or load failed



i know this is a problem with my wireless card.  i guess i'm supposed to extract the firmware from the driver, but every article i've read seems to assume that i can boot up ubuntu, and that the problem is just that it doesn't have the firmware, in which case i just open up a terminal and run the program, and then install the firmware.

but i can't do that.
because it's not booting up.
after that error message repeats three times, some more stuff loads up normally, then everything stops.
i waited about an hour on more than one occasion, but the computer just sits there.

should i give it more time?






thanks,
-tim

---

### Post by shanepardue on 2007-11-30
I've ran the live cd with a wireless card that required that firmware, but I was still able to 
run the cd without wireless capabilities. Have you tried installing ubuntu from the 
alternate cd or are you just wanting to run the live cd? You can try running it from safe 
graphics mode, but I'm not sure if that option is on the 7.04 live cd. I know it is with the 
7.10 version.

---

### Post by ptn107 on 2007-11-30
My laptop uses the BCM4318 integrated wireless card and also displays similar error messages during boot.  However, those should only prevent the wireless from working, not the computer from booting the CD at all.  Feisty Fawn should continue to boot given enough time.

If your just installing use the alternate CD or if you need the Live CD try the Gutsy Gibbon one.

---

### Post by tentel on 2007-11-30
i managed to get it to boot by hitting f6 and typing noapic nolapic


but then it took me to the login screen and asked for my username and password, which i don't have because i never made them yet.

it's got me baffled.






i am planning on doing a clean install, but for now i just want to run the live cd to make sure i like everything.

---

### Post by tentel on 2007-11-30
*note.

i did try 7.10, but i had problems, and i read that HPs have a lot of issues with gutsy and that i should stick with feisty until all the kinks are worked out.

---

### Post by shanepardue on 2007-11-30
I run Gutsy on many different HP laptops at my job and haven't had any issues to report 
other than one of them takes a bit longer than usual to login, but I saw there was an 
easy fix for it. I just haven't had the time to look into it.

---

### Post by tentel on 2007-11-30
i'm going to give gutsy another whorl.



i'll let you know how it goes, but i'm going to give it a while to boot up.


thanks for all the feedback guys.



-tim

---

### Post by tentel on 2007-11-30
so i got gutsy installed.


but now i have a few problems.


when i try to put a data cd into the drive, it won't open.

instead it gives me a message "cannot mount volume UDF volume"


also, my usb drives seem to be dead.

i plugged in an ipod and a mouse and neither worked.



and lastly, i can't get online.

no wireless, and when i plug in a hardwire, it does something (that little icon on the upper right tells me it is looking for an internet connection), but then nothing happens.

---

