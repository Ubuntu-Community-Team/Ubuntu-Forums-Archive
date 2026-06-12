---
title: "How to uninstall Ubuntu?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by madfrageris on 2006-11-05
Well, pretty easy it should be I thought... On my laptop I've decided to completely delete the old Ubuntu 6.06 LTS and install newer 6.10, so without further hesitation I put the live CD on and delete both the Linux and Swap partitions. The Windows partition (drive C:/) remains untouched.

I reboot, but... I see GRUB loading! Obviously it can't load, so I have to install Linux again in order to fix it. How GRUB is still there remains a mystery, but the fact is I can't uninstall Ubuntu now.

---

### Post by bulldog on 2006-11-05
Hmmm,you will install 6.10 so why do you want to get rid of GRUB?

Just install 6.10 and it will boot,at least I hope so :D 

Are you sure you will install 6.10?

And to solve your 'mystery' GRUB is in your MBR and by deleting your Linux partitions,you're not going to delete your MBR.
So GRUB stay there till you overwrite your MBR.

---

### Post by madfrageris on 2006-11-05
> **bulldog said:**
> Hmmm,you will install 6.10 so why do you want to get rid of GRUB?

Just install 6.10 and it will boot,at least I hope so :D 

Are you sure you will install 6.10?

Yes, I'm sure I'll install Ubuntu 6.10 after it downloads on my main computer, but the laptop has Windows XP on it, which can be used right now.

The problem is I want it to have only one operating system at this time.

---

### Post by bulldog on 2006-11-05
> **madfrageris said:**
> Yes, I'm sure I'll install Ubuntu 6.10 after it downloads on my main computer, but the laptop has Windows XP on it, which can be used right now.

The problem is I want it to have only one operating system at this time.

Yep quit right.
Im sure you know what you're talking about,but I don't get it.

---

### Post by gn2 on 2006-11-05
If your Windows is booting OK, I suggest leaving things as they are.....

If you want to remove Grub from the MBR, run fixmbr from your Windows CD recovery console, or a W98 boot floppy.

---

### Post by steve.horsley on 2006-11-05
OK. You need to replace GRUB with a windows bootloader then. You can do this with the windows installer CD, I believe.

Or you could reinstall Dapper, which will get GRUB working again, until you have the CD to install Edgy with.

---

### Post by madfrageris on 2006-11-05
> **gn2 said:**
> If your Windows is booting OK, I suggest leaving things as they are.....

If you want to remove Grub from the MBR, run fixmbr from your Windows CD recovery console, or a W98 boot floppy.

No, Windows isn't booting at all, because GRUB can't find it's files I believe, so it's stuck on GRUB starting screen, showing it has encountered an error.

> OK. You need to replace GRUB with a windows bootloader then. You can do this with the windows installer CD, I believe.

Haven't tried this yet, but it means I'll have to reinstall Windows... again?

---

### Post by bulldog on 2006-11-05
> **madfrageris said:**
> No, Windows isn't booting at all, because GRUB can't find it's files I believe, so it's stuck on GRUB starting screen, showing it has encountered an error.



Haven't tried this yet, but it means I'll have to reinstall Windows... again?

Just popin the windows cd and go to recovery console.
Then fixmbr and/or fixboot  and GRUB should be gone and your windows bootloader is installed again.

Leave the question open where you want to install 6.10 :D

---

### Post by madfrageris on 2006-11-05
> **bulldog said:**
> Just popin the windows cd and go to recovery console.
Then fixmbr and/or fixboot  and GRUB should be gone and your windows bootloader is installed again.

Leave the question open where you want to install 6.10 :D

Thank you, hope it helps. Ubuntu proved to have amazing and helpful community I never saw before :).

---

