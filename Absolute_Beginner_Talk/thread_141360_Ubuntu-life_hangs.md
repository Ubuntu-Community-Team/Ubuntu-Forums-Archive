---
title: "Ubuntu-life hangs"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by DirkF on 2006-03-08
Hi, "freeing booptstrap memory" hangs up my pc. Can't have a peek at what Ubuntu could bring. Hope it's not symbolic for what will come...
Regards,
Dirk

---

### Post by Mustard on 2006-03-08
System specs?

---

### Post by DirkF on 2006-03-08
AMD Athlon1800+, MSI K7Turbo2, 500mB RAM, VooDoo3dxf, ProAudigySoundcard, 2GB HD, CD-rom, Realtec LanCard (ISP via Router)

---

### Post by Mustard on 2006-03-08
Where did you get the live CD from?  

Is it a shipit live CD, or a CD from a magazine, or did you download the ISO and burn it yourself?

---

### Post by DirkF on 2006-03-08
The latter, it boots nicely, but halts on "freeing bootstrap memory"

---

### Post by Mustard on 2006-03-08
Did you do an md5sum check on the ISO you downloaded?

Have you verified the media when you first boot it up?

What speed did you burn the ISO at?

---

### Post by DirkF on 2006-03-08
No sum check nor media verified, burnt at halfspeed (8). Nero Burning rom command "Burn image".

---

### Post by Mustard on 2006-03-08
Ok ,well those first two negatives on the questions need to be investigated first. :)

You need to run an md5sum check on the ISO, using whatever md5 checker you can find online.  The checksums are available from the download site.  This will show whether the download was corrupted or not.  The checksums should match those found on the download site.  If not, then you have a corrupt/tainted download of some kind.

There is an option to verify the media when you first boot up.  Press the functions keys to see more options.

Ideally the CD should be burnt at the lowest possible speed (to avoid any errors), but check the first two things before worrying about this part.

---

### Post by Mustard on 2006-03-08
Your systems specs look good enough for the live CD, but perhaps the hard drive is a bit small for a full install.  I think you will fit it on the drive, but you are not going to have much space left.  Obviously your not installing yet, but its something to consider if you do decide to install.  There are ways and means of decreasing the install size, but its not something that can be explained in five minutes or two sentences. :)

---

### Post by DirkF on 2006-03-08
Ok, I'll check the iso-file and disk, might burn another one and w'll see what happens. 
tnx Dirk

---

### Post by DirkF on 2006-03-08
md5sum -c h:\ubun....iso says on all files, open or read-failure... So that's probably it?

---

### Post by DirkF on 2006-03-08
New download image fails md5sum -c ubuntu....iso "file open or read failure...",
appears previous download did a succesful check: md5sum.text on cd..., but no clue what this file states. I'm on the edge of quitting, this is even worse than five years ago with Suse and Mandrake disks, two days gone and still no simple demo. Should I try AMD64-life-version?

---

### Post by Mustard on 2006-03-08
Something is going wrong with your downloads it seems.  The details you are giving are a bit sketchy though.  It's pretty hard to fill in the blanks when your description of the process you are using is so light on detail. So many questions are going through my head.  What md5sum application did you use?  Are you using it correctly? How are you downloading the ISO?  Where are you downloading the ISO from?  If you were more forthcoming with this type of information, then it would be easier to get a picture of what is going on.

Honestly though, once someone says they are 'going to quit', my enthusiasm for helping them get through the issue drops to zero. :)

Why don't you sign up for some CD's to be sent to you via shipit?  Ubuntu does this for free.

---

### Post by DirkF on 2006-03-09
Well, did a third download and now there suddenly was a sort of in between download of an extra file in a different window, totalling 647MB, prior 627MB. Guess what, Ubuntu-live boots and starts the desktop nicely. Mustard was right, downloads were not ok. 
Now, if only the mouse would work, I could have a go. But that must be a hardware problem as the mouse in XP generates Code10. 
Tnx

---

### Post by Mustard on 2006-03-09
[QUOTE=DirkF]Well, did a third download and now there suddenly was a sort of in between download of an extra file in a different window, totalling 647MB, prior 627MB. Guess what, Ubuntu-live boots and starts the desktop nicely. Mustard was right, downloads were not ok. 
Now, if only the mouse would work, I could have a go. But that must be a hardware problem as the mouse in XP generates Code10. 
Tnx[/QUOTE]

What is the brand of mouse?  Is it USB mouse or PS2 mouse?

Do you know what this 'Code 10' means?  I have no idea.

-edit-

I did a bit of googling and found some answers anyway..

[http://www.usbman.com/Guides/Error%20Codes%20Explained.htm](http://www.usbman.com/Guides/Error%20Codes%20Explained.htm)

> Code 10

If the device has a "FailReasonString" value in its hardware key, that string is displayed as the error message. The driver or enumerator places this registry string value there. If there is no "FailReasonString" in the hardware key, the following generic error message is displayed:

    This device is either not present, not working properly, or does not have all the drivers installed. (Code 10)

    Try upgrading the device drivers for this device.

Solution button: Update Driver

To resolve this error code, make sure the device is connected to the computer correctly. For example, make sure all cables are plugged in fully and that all adapter cards are properly seated. Follow the suggested solution button and update the device driver. It may be possible to remove the device and redetect it using the Add New Hardware wizard.


I think you may be correct.  If you have installed the latest drivers for it on XP and its not working properly, its probably not a bad assumption that its not working properly. If you give me the details of brand, USB or PS2 then it might be possible to to look up some more information online.

---

### Post by DirkF on 2006-03-10
Tnx very much Mustard, ran Ubuntu-live on the other machine (roughly same hardware) with a good mouse: no problems. Spent the entire evening exploring Ubuntu and it works very well, I must say. All hardware (scanner, printer, LCD, sound, internet and grafics) were found easily. Only had to press Enter three times to install the cd. This is much better than some years ago. I will download the install-cd's and have a go.
Tnx again,
Dirk

---

