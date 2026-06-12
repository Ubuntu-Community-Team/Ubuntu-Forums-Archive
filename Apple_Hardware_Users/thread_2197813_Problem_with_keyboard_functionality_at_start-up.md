---
title: "Problem with keyboard functionality at start-up"
date: 2014-01-05
forum: Apple Hardware Users
---

### Post by Michael_Kolonay on 2014-01-05
I recently converted my girlfriend's old iMac to a Linux machine in hopes of using it as a sort of makeshift server for my home network. Everything seemed to be going fine until the power went out unexpectedly and I found myself at the grub selection screen;suddenly an issue I had faced earlier in the conversion reappeared.

The problem stems from the computer's inability to recognize the USB keyboard before the operating system loads.  This would almost certainly be a bios issue in a pc, but being a mac complicates the situation.  A bit of research reveals that this is a documented,if uncommon, problem.  People who replaced their original bluetooth keyboards with usb equivalents were unable to utilize startup keys (or anything else that required a keyboard) before the operating system loaded.  Interestingly enough, most of the cases I found dealt with people who had purchased Apple manufactured replacements -- my girlfriend included.  Admittedly, I have not yet tried using a usb keyboard from a different manufacturer (since i do not have one on hand), but I have read about others who have to no avail, so I have little hope for such an easy fix.

I first encountered the issue when I was trying to force the live CD to load while the system was still running OS-X.  I was unable to use the startup keys to access what apple calls the startup manager. Even once I made it to the manager by holding the menu button on a Apple media remote I could not select any option due to the lack of keyboard functionality.  I was able to work around that problem by pairing my brother's Apple bluetooth keyboard within OS-X and then restarting (although I suspect I could have used the Logitec I use for my tablet).

I am still able to access the live CD simply by placing it in the drive at startup, so I am fairly confident I can pair a bluetooth keyboard to the computer and then restart without the disk (or in a worst case scenario simply reinstall entirely).  As of now a full reinstall would not be so bad (I have not done much to the system beyond setting up a simple ssh server), but in the future it would be a much greater inconvenience.

**My question therefore is this**: does it make sense that the computer cannot receive input from USB devices, and is there a way I can change some settings from within Ubuntu which will allow the Mac to accept USB keyboards at startup?

I apologize if this seems long winded, but I believe my story compiles a good deal of searching about what I found to be an relitively poorly documented problem.

---

### Post by bapoumba on 2014-01-06
Moved to Apple Users.

---

### Post by Michael_Kolonay on 2014-01-09
I would debate that the move was unreasonable based on the nature of my question, but no matter.  

Update: My logitec keyboard did not work with the Mac in the grub loading screen.  I was able to pair the keyboard easily within the live CD, but (not surprisingly now that I think about it) the computer failed to recognize the keyboard upon reboot.  Perhaps the computer will recognize a Mac bluetooth keyboard, but I fear I may have taken that capability away as well since OS-X is a thing of the past.  Regardless, while I can do a fresh install from the boot CD, my problem will be sure to return again the first time the power goes out because I do not feel like paying 50-60 dollars to buy my own Mac keyboard.

Further thinking has made me realize I was limiting the scope of my search too much by limiting it to Macs, so I broadened it a bit and found a new angle.  Why is it that grub is not timing out and loading the first option?  From what I can tell, that is a default setting...

---

