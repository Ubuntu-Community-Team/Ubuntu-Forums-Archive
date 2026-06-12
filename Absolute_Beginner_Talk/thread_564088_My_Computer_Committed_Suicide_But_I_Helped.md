---
title: "My Computer Committed Suicide But I Helped"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by nakedparrot on 2007-09-30
It's the sort of thing that happens when you have an extra bit of time on your hands - you play with things you shouldn't be playing with.
For no good reason I decided this afternoon to give uBuntu a try.  I downloaded the program and burned it to a disk.  I then ran the disk and everything seemed fine until it told me it could not give me the all the graphical advantages without updating my nVidia driver.

The driver was okay for Vista but apparently not for uBuntu.  And so I let the system download and install the nVidia driver that it said would make everything work.

But such was not the case.  In fact, I lost my video entirely.  And nothing I do will bring it back.  I can't boot to uBuntu; I can't boot to Vista, I can't even get the Vista install disk to show up.  My screen is, for all intents and purposes, DEAD, making my laptop computer, likewise.

Does anyone have any ideas on how I can recoup my video?  I tried an external monitor but, as I figured, it didn't work either.  Any suggestions would be much appreciated.

Thanks.

---

### Post by santiagoward2000 on 2007-09-30
Most likely your Video Card is fried. I'm not sure if it was caused by Ubuntu's drivers, but still, I'm quite sure you'll need to buy a new card. Sorry!

---

### Post by Ripfox on 2007-09-30
Do you see anything at all? Is there any text at all up there. It is jumping to conclusions to think your card is dead at this stage. Also, it is VERY unlikely Ubuntu fried your hardware, sorry...

---

### Post by nakedparrot on 2007-09-30
Appreciate your response.  However, it seems unlikely to me that installing an incorrect, or non-compatible, driver would "fry" the video.

---

### Post by Roaster on 2007-09-30
Try to reinstall Vista. I know any and all of your data will be lost but, it may not be the card is gone just that the improper drivers are installed. I sure hope this is the case! Best of luck,

---

### Post by nakedparrot on 2007-09-30
I'm afraid there was absolutely nothing visible on the screen at any stage.  It's just as though the computer is turned off.  Strange the driver would install if it wasn't compatible.  And why would it over-ride the Vista nVidia driver - I wasn't running Vista at the time.  I thought removing the uBuntu CD from the computer would allow the system to revert to Vista.

---

### Post by nakedparrot on 2007-09-30
> **Roaster said:**
> Try to reinstall Vista. I know any and all of your data will be lost but, it may not be the card is gone just that the improper drivers are installed. I sure hope this is the case! Best of luck,
That was the first thing I tried, after rebooting unsuccessfully.  But the screen showed nothing with either the uBuntu disk or the Vista installation disk.  Can't see; can't reinstall.

---

### Post by Lord Illidan on 2007-09-30
Sounds improbable to me too. Either a really really wierd co-incidence, or else...a bad card?

Eitherway, if nothing appears on the screen then it's time to go to a techie!

---

### Post by santiagoward2000 on 2007-09-30
> **nakedparrot said:**
> Appreciate your response.  However, it seems unlikely to me that installing an incorrect, or non-compatible, driver would "fry" the video.

But can you see anything while it is starting up? Windows or Linux drivers could be a problem once the system is loaded, but not before...

---

### Post by darkness5723 on 2007-09-30
This actually just happened to me as well. I upgraded to Gutsy and installed new ATI drivers for my card hoping to get compiz to work, but it didnt. ANYWAY... I was just browsing the web and my computer crashed. Now everytime I try to boot off my HDD into ubuntu it won't work and the monitor just sits there refreshing.

---

### Post by mlentink on 2007-09-30
> **ripfox said:**
> Also, it is VERY unlikely Ubuntu fried your hardware, sorry...Probability approaching zero...
I would say. I seriously advise trying to boot off a rescue cd ilke the the [Ultimate Boot cd]("http://www.ultimatebootcd.com/download.html") or the [super Grub disk]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html"). 
As sson as your system starts up, you should be able to press a key (depends on your system) that will allow you to specify your boot order. Choose Cd to boot from cd.
 report back, and we&#314;l try and help you further

---

### Post by jrusso2 on 2007-09-30
It seems like the OP was running Ubuntu as a live cd.  I don't think you can install an nvidia driver on a live cd.

But I also don't see how he could have trashed his video card.

Maybe a bios reset would help.

---

### Post by nakedparrot on 2007-09-30
Thanks for all your suggestions.  I have, however, resolved the problem.  I disconnected the power from the laptop and removed the battery and waited a few minutes.  When I hooked everything back up I was good to go.

Thanks again for your input.

---

### Post by eph1973 on 2007-09-30
Did you have a BIOS splash screen before, and do you still?  If you do, at what point during the boot process does the screen go "dead".  If you never had a BIOS splash screen, other than the screen, does everything seem to boot normally? (i.e. you hear the CPU fan running, the normal indication lights, etc).  Have you tried anything else, besides installing Ubuntu recently?  Sounds like maybe you are talking about a laptop.  Do you have any model information on it?  Did you move it recently?  I think since you couldn't see it with an external monitor, you can probably eliminate the actual screen becoming unplugged or damaged such that it doesn't display anymore.

---

### Post by armandh on 2007-09-30
is everything pluged in tight?
you should get the video card ID or beep codes
do you get the usual bios startup?
try the monitor on another computer
If it boots off the live CD it is not the video card

Never mind I see you fixed it with a hard restart

---

