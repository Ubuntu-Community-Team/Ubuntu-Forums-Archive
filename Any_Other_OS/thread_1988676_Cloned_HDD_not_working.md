---
title: "Cloned HDD not working"
date: 2012-05-28
forum: Any Other OS
---

### Post by Shadius on 2012-05-28
Hey everybody :)

Here's the situation:
I have a Compaq Presario 5410US computer with Windows XP Home Edition SP3 installed, but the 40 GB HDD was failing due to it having some bad sectors. So to save my Windows XP Home Edition SP3, I cloned it to another HDD. The cloned HDD works perfect on my Compaq Presario, so I thought to see if it would work on my SONY VAIO PCV-RS314P. It doesn't work! Why not!? I hook up the cloned HDD and a black screen comes up with a bunch of information and at the very left bottom says:

> A disk read error occurred
Press Ctrl+Alt+Del to restart

I press that but nothing happens. What do I do? I don't understand how come it works on my Compaq, but not my SONY VAIO? :confused: Any help is greatly appreciated. I know this might be a Windows problem, but you guys seem to be very knowledgeable about any OS.

This problems stems from a previous thread of mine, [Booting/Cloning/A Big Mess]("http://ubuntuforums.org/showthread.php?t=1986349"). I used G4L (Ghost 4 Linux) from Parted Magic LiveCD to clone the HDD.

---

### Post by wilee-nilee on 2012-05-28
Actually as I read your post closer I realize that you are plugging the HD into another computer then the original cloned from, it this right?

Both computer have different hardware, and I believe the compac is a OEM install, This might be the cause, others can probably give more info.

You might want to name the way you cloned as well.

---

### Post by Shadius on 2012-05-28
> **wilee-nilee said:**
> Actually as I read your post closer I realize that you are plugging the HD into another computer then the original cloned from, it this right?

Both computer have different hardware, and I believe the compac is a OEM install, This might be the cause, others can probably give more info.

You might want to name the way you cloned as well.

Yeah, it's a different computer, a SONY VAIO. Should I still run the Boot Info script?

---

### Post by wilee-nilee on 2012-05-28
> **Shadius said:**
> Yeah, it's a different computer, a SONY VAIO. Should I still run the Boot Info script?

I had miss read the post as the XP had stopped running on the compac, I don't think that is needed, at least I don't think so. You might wait for more answers, since you have it running on the original laptop.

I have never switched HD's myself, but I have seen people suggest this for recovery, but I believe from a live cd environment, which would be different then actually booting the HD.

---

### Post by Shadius on 2012-05-28
> **wilee-nilee said:**
> I had miss read the post as the XP had stopped running on the compac, I don't think that is needed, at least I don't think so. You might wait for more answers, since you have it running on the original laptop.

I have never switched HD's myself, but I have seen people suggest this for recovery, but I believe from a live cd environment, which would be different then actually booting the HD.

They are both desktop computers. Compaq Presario 5410US and SONY VAIO PCV-RS314P. Thanks for the help again wilee-nilee. Greatly appreciated.

---

### Post by prshah on 2012-05-28
> **Shadius said:**
> The cloned HDD works perfect on my Compaq Presario, so I thought to see if it would work on my SONY VAIO PCV-RS314P. It doesn't work!

Yes, it will not work.

Windows XP is not like linux; a change in underlying hardware will cause random startup errors, and random registry corruptions.

That's how Windows is. 

It gets worse if you are moving from an IDE to a SATA based motherboard. 

Also, by moving the cloned installation to another PC (assuming the cloned installation is under an OEM license), then you are also in violation of license terms, which view change of motherboard as "creating a new personal computer".

Summary: you can't/shouldn't be doing this.

However, if you absolutely must, there are ways to do this:
a) Downgrade to standard controllers (Eg, Standard Dual HDD controllers, Standard VGA controllers, etc, reboot, shutdown, replace motherboard, boot, and install drivers).
b) Perform a "repair" install with the drive connected to the new motherboard.

 Please post back if you want details.

---

### Post by Shadius on 2012-05-28
> **prshah said:**
> Yes, it will not work.

Windows XP is not like linux; a change in underlying hardware will cause random startup errors, and random registry corruptions.

That's how Windows is. 

It gets worse if you are moving from an IDE to a SATA based motherboard. 

Also, by moving the cloned installation to another PC (assuming the cloned installation is under an OEM license), then you are also in violation of license terms, which view change of motherboard as "creating a new personal computer".

Summary: you can't/shouldn't be doing this.

However, if you absolutely must, there are ways to do this:
a) Downgrade to standard controllers (Eg, Standard Dual HDD controllers, Standard VGA controllers, etc, reboot, shutdown, replace motherboard, boot, and install drivers).
b) Perform a "repair" install with the drive connected to the new motherboard.

 Please post back if you want details.

Yes, details please.

---

### Post by prshah on 2012-05-28
> **Shadius said:**
> Yes, details please.

All advice for experts only. YMMV. At your own risk, please.

(a) [http://arstechnica.com/gadgets/2007/09/how-to-install-a-new-motherboard-without-reinstalling-windows/](http://arstechnica.com/gadgets/2007/09/how-to-install-a-new-motherboard-without-reinstalling-windows/)

Note that though the author seems to have been able to  boot back into Windows after installing standard (compatible) drivers (ie, a driver agnostic system), it is HIGHLY UNLIKELY that you will be able to do so, and may end up with a permanently broken installation; so it might be a good idea to create a clone of your clone before you try this.

(b) [http://support.microsoft.com/kb/824125](http://support.microsoft.com/kb/824125)

Note that most OEM discs do NOT offer a "repair" installation option. Instead they often have factory restore discs. If you boot off the Windows XP media and cannot find the "R" (for repair) installation, then your media either does not offer it, or does not see the Windows installed as the same as contained on the install media.

Again, I must point out that there is a very good chance that these methods are not going to work.

Besides these point, this is not a Windows forum, so expect that this thread is going to be shutdown soon.

---

### Post by Shadius on 2012-05-28
So I found a hard disk drive that had Windows XP Media Center on it and tried it on the SONY VAIO and it works! So I really don't understand why the cloned Windows XP Home Edition SP3 isn't working on the SONY VAIO. ](*,)

---

### Post by Shadius on 2012-06-17
Bump

---

### Post by howefield on 2012-06-17
Thread moved to "*Other OS/Distro Talk*" forum.

---

