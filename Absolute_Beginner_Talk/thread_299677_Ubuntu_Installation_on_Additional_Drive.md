---
title: "Ubuntu Installation on Additional Drive"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Terman on 2006-11-14
I want to install Ubuntu on a new drive, without disturbing the XP installation on my existing drive. I know that this can be done, and that the operating system can be chosen from a menu at bootup, but I do not know how to achieve this. I've seen lots of references to NTLDR, but no clear explanation of what it is and how to use it. I'd be grateful for a beginner's guide, or a link to the information, which I suspect must be on here somewhere.

---

### Post by igknighted on 2006-11-14
> **Terman said:**
> I want to install Ubuntu on a new drive, without disturbing the XP installation on my existing drive. I know that this can be done, and that the operating system can be chosen from a menu at bootup, but I do not know how to achieve this. I've seen lots of references to NTLDR, but no clear explanation of what it is and how to use it. I'd be grateful for a beginner's guide, or a link to the information, which I suspect must be on here somewhere.

If you are installing from the live cd Ubuntu will ask you which hard drive you want to install to.  Install to the one windows is not on.  Near the end, Ubuntu will display a final confirmation about what it is going to do.  It will say it is installing grub to (hd0).  The (hd0) should be a link, click it and then modify it to say (hd1).  When it brings you back make sure the change was made.  Then let it install, and when you are done reboot.  Enter your BIOS setup and select the hard drive Ubuntu is on to be the default boot.  Save and exit, and then when your computer boots you should get the Ubuntu GRUB menu letting you boot into Ubuntu or Windows (if windows isn't listed, boot into Ubuntu and post back here for directions, it's really easy to add it).  This process should install Ubuntu and let you boot either OS without touching the windows install at all (ie, if you switch the boot order back to the windows drive first it would act like Ubuntu wasn't there at all).

---

### Post by confused57 on 2006-11-14
Here's how I have my system set up:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Terman on 2006-11-14
Thanks for the replies. I'll give it a try.

---

