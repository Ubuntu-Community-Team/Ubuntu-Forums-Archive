---
title: "How to mount external DVD drive permantly?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by soldave on 2007-09-04
I'm trying to get used to using Ubuntu and am having a few teething issues.  My current one is with my external firewire DVD/RW drive and getting it to mount permanently.  By this I mean that when a DVD is inserted into it, it mounts and is shown in the /media folder.  But the name of the DVD drive sets itself to the actual title of the dvd (e.g. /media/HPOTTER or /media/LORDRINGS).  When I eject the DVD, the link to the DVD drive in the media folder disappears completely, even though the drive is still switched on.

Is there any way to keep the drive mounted permanently, preferably with something like a /media/DVD as a constant folder?  Sorry if this is a dumb question again but I am just getting used to this.  Thanks for any advice you can offer me in advance:)

---

### Post by GMachine_24 on 2007-09-04
> **soldave said:**
> I'm trying to get used to using Ubuntu and am having a few teething issues.  My current one is with my external firewire DVD/RW drive and getting it to mount permanently.  By this I mean that when a DVD is inserted into it, it mounts and is shown in the /media folder.  But the name of the DVD drive sets itself to the actual title of the dvd (e.g. /media/HPOTTER or /media/LORDRINGS).  When I eject the DVD, the link to the DVD drive in the media folder disappears completely, even though the drive is still switched on.

Is there any way to keep the drive mounted permanently, preferably with something like a /media/DVD as a constant folder?  Sorry if this is a dumb question again but I am just getting used to this.  Thanks for any advice you can offer me in advance:)

Hi - I think this is odd. Whenever I attach a Firewire drive it shows up on the desktop (as well as in the /media folder) with an icon describing what it is, DVD/RW Drive, WD160GB hard drive, etc.

Sorry if this sounds like a simpleton question, but I'm assuming you do not get a similar icon on your desktop when you plug in or turn on your Firewire DVD drive?

Also, what version of Linux are you using? In versions either before 6 or 6 and before it took some fancy footwork sometimes (i.e. lots of playing around with commands) to get a drive to mount - at least for me. Not so in the latest version.

-gm

---

### Post by soldave on 2007-09-04
No - I don't get a desktop icon when I plug in my DVD drive - I only get it when I put a CD or DVD into the drive.

And I'm using Ubuntu version 7.0.4

---

### Post by GMachine_24 on 2007-09-04
> **soldave said:**
> No - I don't get a desktop icon when I plug in my DVD drive - I only get it when I put a CD or DVD into the drive.

And I'm using Ubuntu version 7.0.4

What about when you click on places>computer? Is it listed there?

I just remembered I don't have a desktop icon but one shows up when I insert a disc in  my  IDE connected DVD drives. Sorry for my error.

If you go to /media is there a drive listed there that looks something like cdrom0 or other optical drive?

--gm

---

### Post by schorsch on 2007-09-04
That is pretty normal: You do not mount the DVD drive but the disc in the drive. There is no need to mount an empty DVD drive. That's what the automounter is designed for.
What you want is something like a USB disc permanently mounted even if it is not attached.

---

