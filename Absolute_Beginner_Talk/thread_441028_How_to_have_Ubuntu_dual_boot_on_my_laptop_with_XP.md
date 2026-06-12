---
title: "How to have Ubuntu dual boot on my laptop with XP"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-12
I want to install Feisty on my ThinkPad T43, but I had a quick question.  I know that [my] thinkpad has a little partition tucked away that lets me reinstall windows - would installing Ubuntu delete that partition?  And before I make the big jump I wanted to have both XP and Feisty running on the T43, what would be the proper sequence of events?  I'm thinking of this:

1. Format drive
2. Reinstall XP from partition
3. Install Feisty

Or should 2 and 3 be switched?  I'm thinking that GRUB can probably handle dual boots better than the XP bootloader so I thought I should do the Feisty install last.  Any thoughts before I go through this?

---

### Post by benanzo on 2007-05-12
Definitely do the Feisty install last.  GRUB is smart enough to know not to just blow away the whole MBR without at least the option of booting into windows...NTLDR is not so smart.  So do exactly what you said, reinstall windows on the whole disk, then boot the feisty livecd, create some space at the end of the drive and install feisty.  It will set up to dual boot automatically.

---

