---
title: "2 hard drives"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-04-15
I have 2 hard drives in my computer. One runs the Ubuntu and the other one doesn't show up. I just used GParted and set the second on to a primary partition? Is this not right? I'd like to use this a backup for some of my stuff.

---

### Post by Bartender on 2007-04-15
As long as the second drive isn't going to be the bootable drive, it doesn't much matter.  

If you have Windows on a drive, and you want to be able to boot into Windows, the OS has to be installed to a primary partition.  Linux can boot from an extended partition.

If the drive is blank and your goal is to use it as backup and personal data I can't think of any reason not to set it up as one primary partition.

I'm not sure you can configure a hard drive as one extended partition without having at least one primary partition first??!?

---

### Post by captgadget on 2007-04-15
Since I set it up as a primary any ideas why it doesn't show up when I click places>computer?

---

### Post by Bartender on 2007-04-15
Um, no, but the first thing I'd do is go back a few steps.  Intercept the PC's bootup by tapping on whichever key gets you into BIOS.  Is hardware detection set up as "Auto" in the BIOS?  If no, reset it to "Auto" and save it and let the PC reboot.  Go right back into BIOS and make sure you did save the change - sometimes people think they changed a BIOS setting and didn't.  
If it is in "Auto", does BIOS see the 2nd drive?

Wait a minute, you said you already wiped the drive with GParted, so of course the BIOS sees the drive.

Well, I'd still check it anyway.  Make sure BIOS sees the drive and recognizes it as something that makes sense.  For instance, unless it's an ancient BIOS it should identify a Seagate 120GB hard drive as "ST120xxx" or something similar.

If BIOS sees the drive and all seems well there, I'd toss the LiveCD back in and see if it recognizes the drive.  I'd put the GParted CD in and do the same.  What format did you use when you wiped the drive in GParted?  Is it "unallocated"?  I'd try going back and formatting it as ext3 or vfat, then see if Ubuntu recognizes it.

Are the jumpers on the back of both drives correctly positioned?

---

### Post by confused57 on 2007-04-15
It's possible that you just need to mount your second hard drive:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

