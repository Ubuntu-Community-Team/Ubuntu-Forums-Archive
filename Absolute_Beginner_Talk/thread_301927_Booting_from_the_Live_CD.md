---
title: "Booting from the Live CD"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Onwlyix on 2006-11-17
Well, I downloaded the Live CD Ubuntu thing, and burned the ISO to a CD just like the wiki said. The thing is, it won't boot to the CD. I've tried setting boot priority, disabling C: Drive boot, and it doesn't recognize the CD as bootable. What do I do? 
Thanks
Onli

---

### Post by urukrama on 2006-11-17
Are you sure you burned it as an ISO file (and not as a data disk)?

---

### Post by Onwlyix on 2006-11-17
I'm pretty sure. I used the Imgburn program the help page reccommended. Plus, running the CD through Windows brings up the browser thing.

---

### Post by urukrama on 2006-11-17
I don't know Imgburn, but with some programs I have used in Windows (sorry, I forget the names), you had to select 'bootable CD' when burning them; otherwise they would burn just an ordinary CD, but one that cannot be used to boot. Could this be it?

---

### Post by Onwlyix on 2006-11-17
Maybe. I'm wanting to try again with a new CD, but I don't want to have 3 non-working Ubuntu CD's laying around (They're not RW). I guess I should just go for it. 

Oh, and also! In the help tutorial thing, it says to check the hash or something. I downloaded that program but couldn't figure how to compare it with the links it provided. I just skipped it. Could that be the problem?

---

### Post by urukrama on 2006-11-18
The hash check is to see whether the iso file is still intact before you start burning it. 

Does the CD work on another computer? Can you boot with it on another computer? You could try this to see whether the problem lies with the disk, or your computer settings. If you downloaded the Desktop ISO (i.e, not the "alternative install" ISO, you can load Ubuntu without having to install it, so you don't mess with that computer.

Since you mentioned that the CD works fine in Windows, I have a feeling it might be an issue with your BIOS setup. Are you sure it is set up correctly to boot from CD first, and only then from the hard drive?

---

### Post by localuser on 2006-11-18
> **Onwlyix said:**
> Plus, running the CD through Windows brings up the browser thing.

What do you see in the browser thing when its brought up?  Do you see any file things listed?  If so then what are they?

---

### Post by urukrama on 2006-11-18
> **localuser said:**
> What do you see in the browser thing when its brought up?

I took his statement to mean that the browser window that enables you to install some open source programs in windows (Gaim, firefox, etc.). If that comes up, the CD should be fine, no?

---

### Post by localuser on 2006-11-18
> **urukrama said:**
> I took his statement to mean that the browser window that enables you to install some open source programs in windows (Gaim, firefox, etc.). If that comes up, the CD should be fine, no?

Actually I took it to mean windows explorer and I was trying to get the OP to list the files that he sees.  I guess I should have been more clear.

---

### Post by urukrama on 2006-11-19
Onwlyix, at what speed did you burn the CD? That might affect the result. Better burn it at the lowest speed possible.

---

### Post by Bartender on 2006-11-19
As localuser is trying to get at, it's very simple to at least ascertain whether you simply copied the .iso or converted the data to a bootable CD.
In Windows Explorer, with the burned CD in the tray, click on your optical drive.  "Explore" the CD.  If you see just one file, you copied the .iso.  That won't work.  If you see 7 or 8 folders and a handful of files then you know it was converted to a bootable CD.  There may be errors on the CD, but at least you'll know that you are converting the .iso correctly.
Burn it as slowly as the utility will let you and use good quality media.  I just read a comment from Herman yesterday, where he stated that burning an .iso with cheap media resulted in failed installs but burning the same download with good quality media worked.

---

### Post by Onwlyix on 2006-11-22
I burned it at 6x I believe. I think this is a hardware problem though, because I have two similar Dells, and neither will boot from anything but the hard drive, including the Windows install CD. What should I do about that?
Thanks,
Onli

P.S. Yes, I burned the ISO, not copied the file. When I open it, the open source software thing launches.

---

