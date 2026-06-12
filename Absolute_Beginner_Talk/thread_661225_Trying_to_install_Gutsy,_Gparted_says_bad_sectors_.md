---
title: "Trying to install Gutsy, Gparted says bad sectors but XP CHKDSK says NO"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-01-07
I just purchased a 3 year-old laptop (Dell Latitude D400) which has XP on it. I want to set up a dual boot with XP and Gutsy. I have a Parted Magic live cd so I booted up with that to downsize the XP partition and free up space for Gutsy. Once Parted Magic booted up, I opened Gparted to downsize the XP partition. But Gparted refused to allow a resizing of the partition because it said it found at least 1 bad sector on the disk. It further said I should run 'chkdsk /f /r' in Windows and reboot it twice. It said that after that, I could resize NTFS safely by additionally using the "bad-sectors option" of ntfsresize.

So I booted into XP to run chkdsk in the command line. Although I had no other programs running, the chkdsk utility told me it could not run because there were other utilities running. But it did say if I replied "y" (yes), then upon a reboot it would run chkdsk. So I replied 'y' and rebooted the computer. Chkdsk ran, and said the disk was perfectly fine. I rebooted the computer twice, then went back into Parted Magic, and Gparted still said it found at least 1 bad sector on the disk and refused to resize. I went back to XP and ran chkdsk again, and again it found no bad sectors. Again I went into Gparted, and again it said it found at least 1 bad sector. So I don't know whether there is really a bad sector or not, and furthermore Gparted will not allow me to downsize the XP partition. What should I do?

(1) Is there really a bad sector or not? If there is, then I'll return the computer.

(2) If there is no bad sector and Gparted is incorrect, then how can I get it to downsize the ntfs partition?

---

### Post by asmiller-ke6seh on 2008-01-07
I think you answered your own question. Did you try this?

> **swarup said:**
> It said that after that, I could resize NTFS safely by additionally using the "bad-sectors option" of ntfsresize.

---

### Post by swarup on 2008-01-07
> **asmiller-ke6seh said:**
> I think you answered your own question. Did you try this?

No, I haven't. One thing is that it isn't as easy to use as gparted, because it only shrinks the file system, not the partition. Then you have to use fdisk to shrink the partition and you have to match the size of the partition to the size of the file system, otherwise it won't work.

But secodly, and perhaps more importantly, I still need to know whether there really are bad sectors or not. Which should I trust-- chkdsk or gparted?  As I said, if there truly are bad sectors, then I think I really I ought to return the computer. Bad sectors means the hard drive could be unstable or go bad. So how can I be confirmed whether there really are bad sectors or not?

---

### Post by jw5801 on 2008-01-09
Hmm... A couple of potentials:

You could try defragmenting the drive in XP and seeing if it made a difference to GParted.
You could also try using a Windows partition editor and see if it has more success. I'm not sure what the software out there is like though. (EDIT: and thinking about this now, it's fairly likely that it won't be free... it's amazing how quickly one becomes accustomed to free software!)
Also if you resize the filesystem using ntfsresize then GParted might be able to shrink the partition for you.
Otherwise, I'm much more inclined to believe that GParted is simply a bit more sensitive than chkdsk and that there really are bad sectors on the disk. You could try ringing wherever you got the laptop from and see what they have to say about the issue. It's always better to be safe than sorry.

---

### Post by bumanie on 2008-01-09
I would suggest going to this site [http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287) and downloading the diagnostic tool that matches your hard drive manufacturer. It should do the best job as it is tools released by the manufacturer.

---

### Post by swarup on 2008-01-09
(edit: initial reply here is to jw5801)

Great to hear from you. :)

I've found out a bit more since I last wrote here. Parted Magic has a support forum and when I wrote there about the issue, the administrator replied:

> Windows misses bad sectors if you don't do a deep scan. The best thing to do is to use the utility for the hard drive from the manufacturer. To be 100% sure. You should be able to find it on the dell web site.

I have never seen GParted say there was a bad sector if there really wasn't.

Resizing a partition from the cli (command line interface) is easy. Read the Parted Magic Doc while doing it. 

Well, he was right. I downloaded the hardware diagnostics utility from Dell, and checked the hard drive at great length last night. The utility found two bad blocks on the drive: block # 5084681, and 5084682. The code of the error (0F00:1A44) is for uncorrectable data error. No one at Dell technical support could tell me how serious it is i.e. many people have such bad blocks on their HD and it goes for many years like that; or instead that it could be about to go bad altogether.

At this point I guess I have two options. Keep the computer as is, and try to shrink the partition using the gparted cli in Parted Magic. Or call the person who sold me the computer and tell them to give me a different one. I would unhesitatingly opt for the latter, but I don't know how easy it will be to arrange. And I'm leaving the country in four days and will be bringing the laptop to give it to someone. Anyhow, I'll call the seller today and ask them. 

But I guess I'd have two questions for you at this point:
1. Does the defect on the HD sound serious? Or instead, incidental and probably insignificant?
2. Are you familiar with using the cli? Any tips for how to access it or use it?

Thanks!

---

### Post by swarup on 2008-01-09
> **bumanie said:**
> I would suggest going to this site [http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287) and downloading the diagnostic tool that matches your hard drive manufacturer. It should do the best job as it is tools released by the manufacturer.

You are absolutely right. As indicated above, I've gotten the diagnostics utility from Dell, and it is far more detailed than CHKDSK.

---

