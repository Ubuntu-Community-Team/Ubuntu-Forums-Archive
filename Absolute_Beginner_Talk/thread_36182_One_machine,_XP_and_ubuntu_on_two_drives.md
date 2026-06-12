---
title: "One machine, XP and ubuntu on two drives"
date: 2005-05-22
forum: Absolute Beginner Talk
---

### Post by dweeb on 2005-05-22
I currently have ubuntu running on a completely seperate CPU from my windows machine.  Rather than creating a partitioned disk onmy  windows system machine, I am considering moving the Linux hard drive into my primary case.  Any problems doing that?

When I want to boot the ubuntu, I can change the boot order in my BIOS.  Is there a "cleaner" way to signal which OS I want my system to boot?

Thanks in advance for the assistance, these forums are great! 

dweeb

---

### Post by dekoi on 2005-05-22
Grub (the bootloader) will have to be written to the Master Boot Record (MBR), so it won't be as easy as simply adding the HD with Ubuntu on it to your existing system (with a different system architecture). 

I think your best bet is to wipe the drive with Ubuntu on it, install that drive in your Windows machine, and reinstall Ubuntu on that hard drive in your Win machine. Ubuntu should be able to then properly install itself in the new setup, and put a clean boot-up option in your MBR.

Hope that helps.

---

### Post by dweeb on 2005-05-22
It does; that makes perfect sense, and is most likely what I will do.  I am so noobesque that I have done VERY little tweaking yet.

dweeb

---

### Post by poofyhairguy on 2005-05-22
[QUOTE=dekoi]
I think your best bet is to wipe the drive with Ubuntu on it, install that drive in your Windows machine, and reinstall Ubuntu on that hard drive in your Win machine. Ubuntu should be able to then properly install itself in the new setup, and put a clean boot-up option in your MBR.
[/QUOTE]

I have done this, and I recommend it highly.

---

### Post by Spoofhound on 2005-05-22
[QUOTE=dekoi]
I think your best bet is to wipe the drive with Ubuntu on it, install that drive in your Windows machine, and reinstall Ubuntu on that hard drive in your Win machine. Ubuntu should be able to then properly install itself in the new setup, and put a clean boot-up option in your MBR.
[/QUOTE]

I agree. I've also done something similar. Added a new drive, clean installed Ubuntu on the new drive and allowed the new install to add itself to the MBR. I had an existing drive with Win 98 and my system now dual boots across both drives. Works like a charm.

The only issues I had were with the fact that my new drive is big (160G) and this caused some boot problems. The answer, as usual, was to be found in these forums

---

### Post by dweeb on 2005-05-22
That won't be a problem for me; I am using one of those old 14Gb IBM drives that refuses to die!

dweeb

---

