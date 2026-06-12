---
title: "Hard time installing..."
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by sarcazmo on 2007-05-04
Sorry, I tried to do a search but with all this information its hard to find exactly what I'm looking for.

I successfully dled the iso and mounted it to a cd.  In my bios, it first scans for a floppy, then my HD, then it says CD drive or USB cd drive.  I figured since I have my USB burner hooked up, I can place that option to the top.  However, once I do that, it tells me "No boot device available" What can I do?  I'm using Win XP atm.

Thanks.

---

### Post by taurus on 2007-05-04
What do you mean by mounting an ISO to a CD?  You need to burn the .iso to your CD as an image file, not just copy it to your CD.  In other words, if you look at the content of the CD under XP, you would see a bunch of files and directories instead of one large file.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

---

### Post by sarcazmo on 2007-05-04
Sorry I was a little unclear.  I did burn the iso as an image, I used poweriso to do it.

I can't figure out why when I go into BIOS it's not booting from the CD.

I tell it to boot from the Onboard or USB Cd-drive.  My onboard drive is fried, but I figured it'd just look @ my USB drive.  It doesn't seem to be doing that as when I save the options and exit I get a  "No Boot device available" message.

---

### Post by taurus on 2007-05-04
While you are in XP, view the content to see if you see a bunch of files and directories or do you only see a one large file.

---

### Post by sarcazmo on 2007-05-04
I see many folders.  I burned it the right way :)

Just found this link [http://lists.us.dell.com/pipermail/linux-precision/2003-July/000096.html](http://lists.us.dell.com/pipermail/linux-precision/2003-July/000096.html)

Doesn't mention my system, dimension 4700, but I'll have to look into it.

---

### Post by sarcazmo on 2007-05-04
Upon further research, it appears my computer should be quite capable from booting off of a cd.  

Does my USB CD-Rom drive have to be plugged into a particular USB port for it to be recognized?  It's showing up just fine in XP.  Otherwise, I have no idea why it says "No boot Device Available"

---

### Post by sarcazmo on 2007-05-04
Updated my computers bios and the drivers of my USB cd rom drive.

Changed the settings in BIOS to boot from CD or USB CDrom device and I still get the "No Boot Device Available."

In fact, I can't even see the drive listed in BIOS, not sure if this is something I should normally be able to see or not.  It's showing up just fine in XP as a USB drive.

Any ideas?

---

### Post by jfinkels on 2007-05-05
> **sarcazmo said:**
> Updated my computers bios and the drivers of my USB cd rom drive.

Changed the settings in BIOS to boot from CD or USB CDrom device and I still get the "No Boot Device Available."

In fact, I can't even see the drive listed in BIOS, not sure if this is something I should normally be able to see or not.  It's showing up just fine in XP as a USB drive.

Any ideas?

Plug the USB drive you want to boot from into a different USB port (if you have others). See if that has any effect.

---

### Post by candtalan on 2007-05-05
> **sarcazmo said:**
> Upon further research, it appears my computer should be quite capable from booting off of a cd.  

Does my USB CD-Rom drive have to be plugged into a particular USB port for it to be recognized?  It's showing up just fine in XP.  Otherwise, I have no idea why it says "No boot Device Available"

Ithink you are using the facility of booting from a USB device (which happens to have a cd)

so your bios must be capable and set to boot from USB, not cd drive or floppy or hard drive

---

### Post by sarcazmo on 2007-05-05
The bios option reads from "Onboard or USB CDROM Drive."  

I suppose I could go out and buy a new internal cd drive, but I'd like to save the cash if possible.

---

### Post by sarcazmo on 2007-05-05
Figured out the problem.  For whatever reason, my computer just won't boot from USB, so I had to buy a new internal drive.

I'm ready to full install Ubuntu, but want to make sure I'm doing this right.  I've been using XP for a LONG time and defragged it.  Now i'm in Ubuntu off the cd and double clicked install.  I picked my time zone etc, now I choose "Guided - Use the largest continuous free space" in order to dual boot correct?

---

