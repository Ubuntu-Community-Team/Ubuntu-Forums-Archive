---
title: "How do I uninstall ubuntu?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by edawson on 2007-01-02
i curently have unbuntu version 6.06 lts on my computer. If anyone could help me out by giving me a set of instructions on how to uninstall ubuntu. I would greatly appreciate the help.

p.s.(I want to install windows 98)

---

### Post by taurus on 2007-01-02
Boot from the LiveCD.  Then use gparted (System -> Administration) to delete all the partitions on your harddrive.  Then, format it as ntfs.  Shutdown and switch the CD to XP and boot from it...

---

### Post by meng on 2007-01-02
Windows 98? Okay, whatever makes you happy, even though it's no longer patched/supported. Sorry Ubuntu didn't work out for you. Taurus' advice should work for you, although I'm not sure if you need to format to NTFS. Doesn't Win98 default to FAT?

---

### Post by Solver on 2007-01-02
Yes, format as FAT if you want Win98. Win98 will, in fact, if I remember correctly, freak out at the sight of a NTFS hard drive and not detect the partitions automatically.

---

### Post by edawson on 2007-01-02
i will reply again in a bit if i can not figure it out.

---

### Post by oilchangeguy on 2007-01-02
instead of doing all that if the user has the 98 boot floppy (which they've gotta have to install 98) all they have to do is insert the floppy (make sure the floppy is set as the first boot device in the bios) start the computer select boot w/out cd-rom drive (don't need it til the actual install step) at the a:> promt type fdisk,enter follow the prompts till you get to the screen that shows 4 options, select delete non dos partition, follow the prompts to delete the partition. then select option 1 to create the correct windows partition. re-start the computer again select w/out cd again at the a:> type format c: answer y to all your data will be lost. when format has finished re-start the computer, and now you'll select the cd option when prompted.insert your 98 cd.  at the a:> prompt type e: \setup. e is the drive letter temp assigned to the cd drive.

---

### Post by deadw8 on 2008-07-22
my friend (moved away) installed Ubuntu for me, praising its worth and ive always been fascinated by Linux. 
Anyhow, there are some errors in my feisty fawn and paradoxically im not able to go online because of these errors to download an automatic update which would fix them. 
So i want to uninstall and use XP to write my scripts. I have an XP cd rom but thats all. No floppy and dont want to burn any CDs. is there a while, all i know how to do is press ESC before the GRUB (???) counts down. I dont even know if anyone can help someone as hopeless as me...

---

### Post by CirtexHosting on 2008-07-22
I think that following te all included instructions is the best way to get what you are looking for ;)

---

### Post by hoax.it on 2008-07-22
> **edawson said:**
> i curently have unbuntu version 6.06 lts on my computer. If anyone could help me out by giving me a set of instructions on how to uninstall ubuntu. I would greatly appreciate the help.

p.s.(I want to install windows 98)

but ubuntu... is ubuntu win98.. noooo
if you whant run windows application you can use wine..
You Know Wine Project ?
ubuntu is very secure distro and win 98 is too old.

---

### Post by possumator on 2008-07-22
Seems like this topic should be a sticky as I am sure there are lots of folks who try various linux flavors only to either try something else or go back to windows. 

Personally I have found VMWARE to be a rather nice place to experiment with linux distros, however, there is no guarantee what works in VMWARE will work on the bare metal you plan to install it on later.

---

### Post by overdrank on 2008-07-23
Hi and as deadw8 has resurrected this old thread and has another thread in the new forums then I think this thread it run its course.
Thread closed. :)

---

