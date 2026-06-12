---
title: "How do I boot from CF card in PCMCIA slot on a powerbook"
date: 2012-01-02
forum: Apple Hardware Users
---

### Post by Rgibbons on 2012-01-02
My old Powerbook G4 has a bad motherboard and will no longer power the internal drive.

I am trying to install Ubuntu on a 8 gig CF card mounted in the PCMCIA slot. The install went fine, but I cannot get the Powerbook to boot from the CF card.

Anyone know how?

---

### Post by rsavage on 2012-01-03
Not boot as you get nothing right?
 
It is likely the automatic installer cannot workout the openfirmware path to the start files.  It can be the same if you install to a USB flash drive.  See the USB section here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .  
 
You are going to have to boot into openfirmware I think to work out the openfirmware path to the files or your device.

---

### Post by Rgibbons on 2012-01-03
You are right about the openfirmware. I just can't seem to find the device it is listed under or the path and commands to boot from it.

---

### Post by rsavage on 2012-01-03
Are you sure you can boot from a PCMCIA card?  Maybe openfirmware doesn't have the necessary drivers built-in?  I don't know much about openfirmare I'm afraid....

---

### Post by Rgibbons on 2012-01-03
I am starting to suspect I can't. 

Since my powerbook only has a working PCMCIA slot and optical drive, I am trying to figure out a way to use it as a netbook. Any suggestions?

---

### Post by Rgibbons on 2012-01-03
Right now I am running Ubuntu from the Live CD, I can access my email and surf the web, but I suspect the first time I loose power all my bookmarks and settings will be lost.

---

### Post by linuxopjemac on 2012-01-03
Try the suggestions to list the devices as reported in the manual to boot from USB in the MintPPC 9.2 installation instructions. Basicaly you need to find out whether open firmware sees the bootable device. If so, you need to find the correct path and boot from it:

[http://mintppc.org/content/installation-mintppc-92#1](http://mintppc.org/content/installation-mintppc-92#1)

---

### Post by Rgibbons on 2012-01-03
There lies the problem. I have tried this and openfirmware does not list the device.

---

### Post by rsavage on 2012-01-03
> **Rgibbons said:**
> I am starting to suspect I can't. 
 
Since my powerbook only has a working PCMCIA slot and optical drive, I am trying to figure out a way to use it as a netbook. Any suggestions?
 
If you can't figure out an openfirmware path then I don't think there is a way to use yaboot, unless I am misunderstanding the yaboot instructions.  
 
If you have a USB 2 slot free and working then I think the best thing to do would be to buy a USB flash drive.  You can definitely install to them although it will be a bit of a fiddle.  My local supermarket had some very very small ones [as in dimensions not capacity] that were pretty cheap. 
 
Otherwise, you'll have to do some sort of cdrom/PCMCIA mashup.

---

### Post by Rgibbons on 2012-01-04
Yes, it looks like I have the same issue. Mine won't boot from USB or PCMCIA. Neither is recognized in openfirmware.

The only way I am going to get it to boot from the PCMCIA is to figure out a way to mount the device in open firware before I attempt to boot to it.

---

