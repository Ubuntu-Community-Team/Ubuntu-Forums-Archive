---
title: "R4 DS homebrew device doesnt like Ubuntu-created file system, Windows works fine tho."
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-09-05
I have a R4 DS (allows me to run homebrew apps on my DS, can also run Linux, among other substantially more illegal things but that isn't the point).

The problem is that when I format the MicroSD card (regular FAT format) I run into many problems with the device not finding certain files.

I have a feeling that it is due to Linux being case-sensitive, because I renamed the file causing the error to exactly how the error was displaying the filename, thankfully this worked.

However only few files give errors when not found and the ones that don't just annoyingly prevent the feature its related to from working.

I instead booted up Windows and reformatted and reinstalled everything on the card, it worked fine after that.

I got everything working in the end, but I had to reboot to accomplish this, I could of just used VirtualBox since the card reader is a usb device, but I want to avoid emulation whenever possible.

So my question is: How can I copy/format files in such a way that is more similar to Windows' and doesn't cause the above mentioned problems?

---

### Post by bone2006 on 2007-09-05
what is a R4 DS device?  I'm guessing we're talking about FTA device and it really has nothing to do with your original question?  
I've never had any issue with formating and using SD cards.  If your having problems you might want to install gparted and then just unmount it and you should be able to use gparted to format the card.

---

