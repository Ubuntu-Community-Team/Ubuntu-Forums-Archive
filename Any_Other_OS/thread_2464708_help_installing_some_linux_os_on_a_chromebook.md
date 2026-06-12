---
title: "help installing some linux os on a chromebook"
date: 2021-07-09
forum: Any Other OS
---

### Post by corvairbob on 2021-07-09
ok today i took the hard drive out of a chromebook and installed a formatted drive. i have the mint on a stick in the usb on the chromebook and when i started the chromebook and got a note that the chrome os is missing. so do i have to put the old drive back into this chromebook?  i was under the impression that i put the stick in the pc and booted it and that the linux would start to install automatically  if not then what is the procedure? or will this not fit on the chromebooks? if i can get it onto a chromebook that has a 16gb ssd drive then i will get a 128gb drive and reinstall it so i then have room for docs and files and maybe some photos.

but if it i can't get it onto this chromebook than i may just buy a pc off ebay with it installed already. but because i have 4 chromebooks now i figure i can play around with one. thanks bp

---

### Post by Autodave on 2021-07-09
Some more info is needed on that laptop.  There is more than likely a key that you need to press while booting it up.  Could be ESCAPE, F10, etc.  What you are looking for is the BOOT menu.  From that menu you will chose to have it boot to the USB stick and installation* should* start.

Again. if you tell us the make and model of the PC we may be able to help more.

---

### Post by mikewhatever on 2021-07-09
No, the impression you were under is completely off. There is no automatic linux installation in Ubuntu. Perhaps Linux Mint does it, but that is irrelevant. 
Also, you've posted in the New to Ubuntu section, but the question has nothing to do with Ubuntu. There was a subforum for other OSs you might want to consider.

---

### Post by Frogs Hair on 2021-07-09
Moved to Any Other OS. There is no officially supported method for installing Ubuntu based operating systems on a Chrome Book. There is an unofficial hack known as [Crouton]("https://github.com/dnschneid/crouton"), use at your own risk.

---

### Post by TheFu on 2021-07-09
Chromebooks are NOT normal laptops.
Chromebooks are locked into using ChromeOS unless you flash a new BIOS.  This breaks the warranty and usually prevents booting ChromeOS ever again.  There are many caveats around flashing a new BIOS.  On both my chromebooks, I had to physically modify the insides of the chromebooks to break an electrical connection known as the "write protect screw."  The way these are designed means scraping off a metallic sticker. That process destroys is.
 
The first step is to see whether your exact chromebook can even do it.  Google "Mr. Chromebox" to see a list of exact models and which firmware they support, if any.  Then you'll want to become an expert on THAT EXACT model, since they are all a little different.  Finally, post-install, chromebooks all have UEFI boots and GPT storage which is fine, but the EFI/ directory will not necessarily honor any standards, so you may need to manually mount the Linux installed stub to a different filename to get it booting.

For about 2 yrs, each of my chromebooks were great, light, little, travel Linux systems, but they are cheaply made and parts wear out if we use them as daily-use systems.  Every one I setup this way, the keyboards ended up breaking within 2 yrs. Replacement of the keyboard isn't an expensive part, but everything inside the case has to be removed to make that happen. Additionally, if the chromebook is disconnected from power for too long, then it will reset to factory settings and you'll end up with a bricked device that needs an EEPROM programming tool to reflash the alternative BIOS.  Chromebooks don't have a CMOS battery. They use the larger battery that powers everything else in the chromebook.  If running ChromeOS, this isn't a big deal. Loading a fresh copy of ChromeOS isn't hard, but with any other OS, it's a chicken-egg problem.  Just sayin.

When laptops were expensive, a chromebook was a great option to get a cheap laptop.  At this point, there are so many cheap laptops that the hassles of dealing with these problems with an under powered, under RAM'd, under storaged, system just aren't worth it. For $300, a really excellent laptop can be bought refurbished with a 1 yr warranty from reputable online retailers that don't have any of the hassles or challenges a chromebook requires.

---

### Post by corvairbob on 2021-07-10
ok thanks i found out my hp chromebook will not let me change the chrome os. i even took out the drive and put in a new formatted blank drive and it would not let me go to the usb port. so i gave up thanks anyway. what i may do is get a pc from ebay that has some form of linux on it and go from there. again thanks  now you can close this one if you want

---

### Post by TheFu on 2021-07-10
Only you can mark a thread as "SOLVED" - nobody else. There's a Thread Tools button.
I find it hard to believe that an HP chromebook can't be modified to run Linux. Is the exact model a state secret?

---

### Post by corvairbob on 2021-07-10
when i tried to do this and took out the drive i remember about 4 years ago i tried and on the hp they have a jumper on the mother board that somehow prevents that type of tampering. i can take that jumper of and do this but then if i decide to go back i have to take it apart again. so i will just get a pc off ebay that has some form of ununtu on it and then if i have to change that i can. thanks i will find the solved button and select that

---

