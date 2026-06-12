---
title: "Live CD damaged intel raid partition?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-03-31
Hi,

I have an intel Raid 1 (mirror) array for my data.  My main server (running XP), has 15 hard drives.   2 of them are a 500gb raid array.  When I booted into the live CD, I saw my raid drives were both being seen as two separate drives.  I decided to copy a 700 mb zip file on one of the drives (assuming i t would mirror on both).  It didnt, I didnt think much of it, I rebooted, then found XP wouldnt boot.  

The end result was my raid array had to be rebuilt & for some reason one of my other drives lost all formatting (a windows based data recovery software suite is in the process of fixing it). 

Any idea what happened?

My server has 2gb ram & a Q6600 (quad) processor & I thought it would be fun to mess with it in Ubuntu to see some quad core action.

Thanks,
Rich

---

### Post by dstew on 2008-04-01
The Live CD operating system did not recognize your RAID. When you copied the zip file, it was using the disk as if it was a single disk.

To get the Live CD system to recognize the RAID, you might have to install RAID software on it. (Yes, you can install onto the Live CD system, but the installed programs are only in system memory, so they disappear when you shut down.) The RAID packages are dmraid and mdadm, I believe.

This [HowTo]("https://help.ubuntu.com/community/FakeRaidHowto") talks about setting up the Live CD to recognize and install to a RAID.

---

### Post by RichTJ99 on 2008-04-01
Is that why the array was damaged?  

I thought I had a hardware raid, I didnt realize it was OS dependant.

---

### Post by dstew on 2008-04-01
It is almost certainly not hardware RAID, since Ubuntu saw two disks. Hardware RAID is uncommon. Most RAID is software RAID using a multi-disk or enhanced controller. But, the controller is still dependent on operating system software to run the RAID.

---

### Post by RichTJ99 on 2008-04-02
I was under the impression that even if I didnt have an OS (say my non raid windows C drive died), & one of my raid array drives died, if I couldnt boot into windows (or Ubuntu) that while in the bios, the raid array would rebuild itself.

I am glad to know that isnt the case.  Ubuntu can handle my ICH9-R raid setup?

---

### Post by dstew on 2008-04-02
> I was under the impression that even if I didnt have an OS (say my non raid windows C drive died), & one of my raid array drives died, if I couldnt boot into windows (or Ubuntu) that while in the bios, the raid array would rebuild itself.I think the BIOS has extra functions that help the RAID controller, but it seems that this type of RAID needs some software to help it run.> Ubuntu can handle my ICH9-R raid setup?I believe so, but googling around I see plenty of advice but no confirmed succsess stories. One approach would be to send an email or PM to those who have posted requesting help with this and see if they were successful. The general drift of the advice is to use dmraid and/or mdadm to set up the RAID or to get Ubuntu to see and use a RAID that you set up before. Mdadm is more user-friendly than dmraid, but I don't know if they both do the same things. You can install these on your Ubuntu system using Synaptic.

---

### Post by philinux on 2008-04-02
On-board raid found on most motherboards is classed as soft-raid. Meaning all the calculations go on in the sofware driver.

"Real raid" needs a dedicated RAID controller card.

Big subject !!

---

