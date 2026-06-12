---
title: "Vista, Ubuntu, and XP?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by PixArtist on 2006-11-23
I currently **have xp & vista installed**. (installed xp then vista) When I turn on my computer it brings up the Windows Vista boot screen and asks me if I want to start vista or "earlier version of windows" aka xp. I **want to install** Ubuntu. My question is how would I make it so I can boot all 3 OS's? Can I Just add Ubuntu to Vista's boot manager?

---

### Post by jon419 on 2006-11-23
I am sure it is possible, but I have not looked into it yet.

I have the same setup as you.  When I turn on my computer grub is loaded.  I can either load Ubuntu or Windows.  If i choose Windows, I get the windows bootloader.


Wait, this might help you:
[Triple Boot (XP, Vista, Ubuntu) With a Single Boot Screen]("http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/").  I haven't tried it at all, but it looks like what you would need.

---

### Post by m0e on 2006-11-23
When you install Ubuntu to the hard disk it will install the Grub boot manager, which will give you the choice of which OS you want to boot from. Be sure during the install you do not format the entire disk. There is a pretty good explanation [here]("http://ubuntuforums.org/showthread.php?t=305243&highlight=dual+boot+install") of how to back up your MBR if you have access to a USB drive. As far as the actual install there are a couple of guides, one [here]("https://help.ubuntu.com/community/WindowsDualBoot") and a more thorough one [here]("http://www.psychocats.net/ubuntu/index"). An assortment of guides can be found [here]("https://help.ubuntu.com/community/Installation").
I have no experience with the link posted above but it looks pretty good also, just giving you some more choices on doing the install.
On a closing note I would recommend using Ubuntu Dapper instead of Edgy at this point in time, Dapper is much more stable in my experience. I have installed Edgy in two different computer's in the last couple of weeks and have had to work through a number of issues. My main machines are still running Dapper at now, one of them is a dual boot with Windows XP.

---

### Post by rlozano on 2006-11-24
> **PixArtist said:**
> I currently **have xp & vista installed**. (installed xp then vista) When I turn on my computer it brings up the Windows Vista boot screen and asks me if I want to start vista or "earlier version of windows" aka xp. I **want to install** Ubuntu. My question is how would I make it so I can boot all 3 OS's? Can I Just add Ubuntu to Vista's boot manager?

there is no harm in trying to make a triple boot. but make sure that you have to backup your files (important files). there seems to be different structure in vista already as to how they organize the MBR. but for most of the times, GRUB cannot load vista with its normal script in loading windows OS.

have fun and goodluck!

---

### Post by PixArtist on 2006-11-24
Everything worked fine. When I start my computer Grub comes up and gives me options for Ubuntu and Windows Vista Boot Something which then lets me boot vista & xp.

---

### Post by cantormath on 2006-11-24
> **PixArtist said:**
> I currently **have xp & vista installed**. (installed xp then vista) When I turn on my computer it brings up the Windows Vista boot screen and asks me if I want to start vista or "earlier version of windows" aka xp. I **want to install** Ubuntu. My question is how would I make it so I can boot all 3 OS's? Can I Just add Ubuntu to Vista's boot manager?

put the disk in and choose dual boot settings.  Ubuntu (particularly grub) will manage what you choose to boot and startup.

---

### Post by m0e on 2006-11-24
> **PixArtist said:**
> Everything worked fine. When I start my computer Grub comes up and gives me options for Ubuntu and Windows Vista Boot Something which then lets me boot vista & xp.

That has been my experience ***almost*** every time with Linux since I swithched from LILO to GRUB. The key word there being almost, which is why I provided a link to the post about backing up your MBR to USB.

---

