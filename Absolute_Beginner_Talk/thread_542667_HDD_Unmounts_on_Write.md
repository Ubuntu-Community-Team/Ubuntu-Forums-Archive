---
title: "HDD Unmounts on Write"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-09-04
I have a Seagate HDD formatted to ext3 and installed in an external USB enclosure.  The format was from the Live CD using Gpated.  No problems...............................

When I attempt to copy a file over to the drive the copy fails.  The drive instantly unmounts.  

Does anyone have any idea what could be the cause?

---

### Post by GMachine_24 on 2007-09-04
> **expatCM said:**
> I have a Seagate HDD formatted to ext3 and installed in an external USB enclosure.  The format was from the Live CD using Gpated.  No problems...............................

When I attempt to copy a file over to the drive the copy fails.  The drive instantly unmounts.  

Does anyone have any idea what could be the cause?

Hi - I don't know about the instant unmount. But did you set the read/write parameters for your Seagate drive?

A few basics:

What version of Ubuntu are you using?

What is the error message you get when your copy attempt fails?

What command do you use when you attempt to copy a file?

And again, did you set the access parameters for the Seagate drive (i.e. using the "chmod" command)?

--gm

---

### Post by expatCM on 2007-09-04
What version of Ubuntu are you using?
7.04

What is the error message you get when your copy attempt fails?
Relating to copy, none.  A message does appear on screen something to the effect that the drive is now unmounted and unmount it first next time.

What command do you use when you attempt to copy a file?
Gnome Commander F5

And again, did you set the access parameters for the Seagate drive (i.e. using the "chmod" command)?
Edited the properties using Nautilus in root mode.

---

