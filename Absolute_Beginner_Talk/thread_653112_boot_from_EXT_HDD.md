---
title: "boot from EXT HDD"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-12-29
i want help on how to know if my BIOS is compatible for booting from usb.. and how to.. i think it is capable.. cause i had a usb debice connected and it told me something but i am not sure.

PD: i already installed ubuntu into it

plz help...

---

### Post by eternicode on 2007-12-29
Do you know how to get into the BIOS setup?  It's usually to tap the Delete, F12, F2, or F10 keys when you start the comp up.  Once you get in there, look for something like "Boot Order" or "Boot Sequence".  If it's a fairly old computer, it may not have USB bootable capabilities.  If it's fairly new, it should have a USB boot option.

---

### Post by patchido on 2007-12-29
phoenix notebios 4.0 release 6.1 thats my bios... but i cant make it work

---

### Post by eternicode on 2007-12-29
> **patchido said:**
> phoenix notebios 4.0 release 6.1 thats my bios... but i cant make it work

Were you able to find the boot order section?

You also need to make the external drive bootable, and you also need to install an OS on it (the OS install should automatically make it bootable)

---

### Post by patchido on 2007-12-29
this is really wierd.... i already installed ubuntu gutsy on my EXT HDD but the BIOS wont recognize it as bootable.. but if i insert a usb of 1 GB i got i does recognize it... what can i do.?

---

### Post by mytwobears on 2007-12-29
You can check to see if your BIOS supports the capacity hard drive you are trying to boot from.  Some BIOS, especially older ones may support hard drive capacity up to a certain amount of gigabytes.

If this is the case, you can probably update the BIOS, your motherboard manufacturer would probably have the update on their site :).

---

### Post by eternicode on 2007-12-29
Are you saying that your computer will boot from the 1GB flash stick?

Also, are you sure you're not in Windows trying to read the drives as storage devices?  If you used the entire external disk to install Gutsy, it will have been formatted in ext3, which Windows can't understand.  Most flash drives come already formatted with FAT32 or FAT16, which is visible to most operating systems.

If you can physically access your internal hard drive(s) and are comfortable with messing with computer guts, try unplugging the data cables from the hard drives ([color="red"]AFTER shutting the computer down![/color]).  You might also want to unplug the power cables from the drives.  Then, after making sure "USB Device" or "USB-HDD" or something similar is selected in your BIOS boot order, plug in the external drive (and unplug other USB storage devices) and reboot.  If you're sure everything's setup properly, and it still doesn't boot, I'm not sure what else to do, other than boot into a livecd, fire up gparted, and make sure that the computer can see the drive and that the gutsy partition is bootable.

@mytwobears: hadn't thought about BIOS/HDD-size compatibility issues...I wouldn't know how to do that, other than by checking the manufacturer's site.

---

### Post by patchido on 2007-12-29
> **eternicode said:**
> Are you saying that your computer will boot from the 1GB flash stick?

Also, are you sure you're not in Windows trying to read the drives as storage devices?  If you used the entire external disk to install Gutsy, it will have been formatted in ext3, which Windows can't understand.  Most flash drives come already formatted with FAT32 or FAT16, which is visible to most operating systems.

If you can physically access your internal hard drive(s) and are comfortable with messing with computer guts, try unplugging the data cables from the hard drives ([color="red"]AFTER shutting the computer down![/color]).  You might also want to unplug the power cables from the drives.  Then, after making sure "USB Device" or "USB-HDD" or something similar is selected in your BIOS boot order, plug in the external drive (and unplug other USB storage devices) and reboot.  If you're sure everything's setup properly, and it still doesn't boot, I'm not sure what else to do, other than boot into a livecd, fire up gparted, and make sure that the computer can see the drive and that the gutsy partition is bootable.

@mytwobears: hadn't thought about BIOS/HDD-size compatibility issues...I wouldn't know how to do that, other than by checking the manufacturer's site.

dude... i am not a noob.... yes.. i am in the biuos setup screen.. it does detect my 1 gb flash drive but not my 60 gb EXT HDD

---

### Post by patchido on 2007-12-29
> **mytwobears said:**
> You can check to see if your BIOS supports the capacity hard drive you are trying to boot from.  Some BIOS, especially older ones may support hard drive capacity up to a certain amount of gigabytes.

If this is the case, you can probably update the BIOS, your motherboard manufacturer would probably have the update on their site :).

so i check in pheonix site?

---

### Post by patchido on 2007-12-29
> **patchido said:**
> so i check in pheonix site?

there is no download section for bios updates :S

---

### Post by eternicode on 2007-12-29
> **patchido said:**
> dude... i am not a noob.... yes.. i am in the biuos setup screen.. it does detect my 1 gb flash drive but not my 60 gb EXT HDD

Alright, just wanted to make sure we were on the the same page.

Reading [Computer Stupidities]("http://rinkworks.com/stupid/") has made me slightly paranoid on that type of thing :)

......and, no, a computer cannot save to a floppy that is sitting in front of it on the table :lolflag:

---

### Post by mytwobears on 2008-01-05
Check your motherboard manufacturer site for a Bios update.

---

