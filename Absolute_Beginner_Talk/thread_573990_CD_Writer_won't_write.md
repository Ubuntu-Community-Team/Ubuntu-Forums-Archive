---
title: "CD Writer won't write"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by RobbieG on 2007-10-12
I've had v7.04 installed for a couple of months now after reformatting and making a fresh install and am gradually getting to grips with using it but have come across a new problem for me.
I've searched the forums and the documentation but can't find relevant help (though of course that doesn't mean it's not there ;).

Today I have tried for the first time to write data files (268.4MB) to a CD writer and failed.

If I put a RW disc in the drive then it is recognised and I get a CDROM icon on the desktop and if I open this I get a 'CD/DVD Creator file browser' opening up with burn:/// in the address bar.
If I drag files to the browser then I get the option to 'Write to Disc' but then the drive opens and I get a message saying 'Insert a rewritable or blank disc'.

I have all the latest updates installed and the drive comes up as a CR-4804TE in the 'Write to Disc' dialogue box.

I've also tried using Brasero with the same result.

Thanks in advance.
RobbieG

---

### Post by wpshooter on 2007-10-12
Have you tried the **k3b** program ?  You can install it from either add/remove applications or from Synaptic.  I would suggest installing it from Synaptic.

---

### Post by RobbieG on 2007-10-12
Thank you. I've tried this and still no good.   :(

---

### Post by b20963a2 on 2007-10-15
Is the disc already formatted?

---

### Post by FuturePilot on 2007-10-15
How about Gnomebaker? I was having this same problem on my laptop. Gnomebaker worked.

---

### Post by anaconda on 2007-10-15
OK. this is probably a stupid question, but do you belong to the cdrom group? eg. do you have the rights to use cdrom? (I had this problem with groups)

to check type (in terminal)
```
groups
```
if one of the results is "cdrom" then you are ok.

---

### Post by Dave M G on 2007-10-21
I am having what I think is the exact same problem.

It actually first appeared while writing data to some disks, under Feisty. I was backing up files using K3B. And then on the fourth or fifth disk, suddenly K3B would say "Please load a blank disk" in the burn dialog, even though it the main interface would correctly identify a blank disk being present in the drive.

I had hoped that maybe upgrading to Gutsy would help, but it hasn't.

As another poster described, when I put in a blank DVD, an icon for it appears on the desktop. The system recognizes that there is a blank disk there. However, any attempt to write to the disk results in a dialog asking to insert a blank DVD.

This is true with K3B, Gnomebaker, straight off the desktop, or any other DVD writer.

However, it is only true for DVDs. I was able to download the Gutsy CD ISO file and burn it without any difficulty whatsoever.

I am part of the cdrom group, so that is not the problem.

I hope a solution, workaround, or bug fix can be made available, because I am starting to get a backlog of files I need to back up.

Thank you for any advice you may be able to offer.

---

