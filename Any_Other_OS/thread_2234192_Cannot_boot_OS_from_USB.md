---
title: "Cannot boot OS from USB"
date: 2014-07-13
forum: Any Other OS
---

### Post by simonfailla on 2014-07-13
I have been trying to boot SteamOS off a USB, when I press F12 to open the boot menu when my computer is starting up it asks for a boot device but when I choose "USB Storage Device" it takes me to the GNU GRUB screen where I can choose either Ubuntu or Ubuntu in recovery mode, it does not let me boot from my USB. Sorry if this seems like a nooby question but I am not very experienced with Ubuntu.
I have even tried changing it in the BIOS setup to boot from the USB but still just boots Ubuntu from the hard drive.

---

### Post by ian-weisser on 2014-07-13
Then your USB disk isn't bootable. Your machine tries the USB, the USB fails to boot, so your machine moves tries the next bootable device on it's list (the Ubuntu drive).

Your question should probably be "How do I make my SteamOS on USB bootable?"
How, exactly, did you create the SteamOS on USB?
What instructions dud you follow?
Which program did you use to write the image to USB?

---

### Post by simonfailla on 2014-07-13
> **ian-weisser said:**
> Then your USB disk isn't bootable. Your machine tries the USB, the USB fails to boot, so your machine moves tries the next bootable device on it's list (the Ubuntu drive).

Your question should probably be "How do I make my SteamOS on USB bootable?"
How, exactly, did you create the SteamOS on USB?
What instructions dud you follow?
Which program did you use to write the image to USB?

Alright, i made the USB bootable and now i am getting a new messge, it says "Remove disks or other media. Press any key to restart"
When i press any key it takes me back to the GNU GRUB screen

---

### Post by Vladlenin5000 on 2014-07-13
The same question as before:
How exactly did you created that USB? If you just copied the ISO file then it won't work...

---

### Post by simonfailla on 2014-07-13
> **Vladlenin5000 said:**
> The same question as before:
How exactly did you created that USB? If you just copied the ISO file then it won't work...

The instructions on the web page ([http://store.steampowered.com/steamos/buildyourown](http://store.steampowered.com/steamos/buildyourown)) say to download the ZIP file and extract it onto a USB, thats exactly what i did.

---

### Post by Vladlenin5000 on 2014-07-13
I see...
Those instructions imply UEFI which is either not available or not in use in your system.

PS - Steam has a forum too and you'll get better help there. SteamOS isn't Ubuntu based but Debian based like Ubuntu. As such they surely share a lot of things but they aren't the same thing...

---

### Post by howefield on 2014-07-13
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by simonfailla on 2014-07-13
> **Vladlenin5000 said:**
> I see...
Those instructions imply UEFI which is either not available or not in use in your system.

PS - Steam has a forum too and you'll get better help there. SteamOS isn't Ubuntu based but Debian based like Ubuntu. As such they surely share a lot of things but they aren't the same thing...

I was asking here because my current OS is Ubuntu and i thought it could be something to do with that. Thanks for the help though. :)

---

### Post by LastDino on 2014-07-14
I'm fairly certain that simply extracting steam OS **.zip** wont make the USB thumb drive  bootable. So, its probably not Ubuntu problem and there are some extra steps needed. Sadly, only those who have done this might be able to tell you for sure about them. Steam forum might be good place to start.

---

