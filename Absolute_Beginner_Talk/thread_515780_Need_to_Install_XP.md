---
title: "Need to Install XP"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by daynah on 2007-08-02
I've been a Ubuntu user for almost 2 years now, and yes, I do need to install XP on my computer. But I'm having some problems. I need Windows on my desktop because, I swear up and down, that no one has gotten a video game I really like to work in Linux. If you would like to try to get Final Fantasy XI to work in Linux and bypass all of this, please do, I'd prefer it. In the meantime...

My computer: Three harddrives, main with linux ext3 and Feisty, one storage, and one NTFS (without Windows on it, the smallest).

I'm trying to install XPSP2, using a legit cd. What a rarity. ;)

XP2 goes to the formatty section, and it formats the third harddrive to NTFS fine. Good job, Windows. Now Windows says that it needs to put some super important files on my Main Linux, Love of my Life harddrive, and that since it isn't the right file format (ext3), it recommends I reformat. Bad Windows, bad.

I, of course, do not reformat, but I sit and ponder existance. I have my Feisty Live CD ready.

How will she get these important files onto the MBR? Will she ever feel the same again, after making a conscious effort to steer away from her beloved Penguin? Why did she switch to referring to herself in the third person?

-----

To answer the questions asked probably four times by the IRC chat and my friends...

YES, I do need windows. The point is to get a game, FFXI, running that will only run in Windows. I understand this is heresy. No, WoW will not suffice.

YES, I understand that if one does want to dual boot they should install XP first and then Linux. But I haven't done that, and I have a lot of data I'd like to save, so let's not yell at me for such things, yes?

NO, I do not want to erase my entire harddrive. You make an image. No? Yeah, I'm that lazy also.

---

### Post by LaRoza on 2007-08-02
If you can use the other harddrive for Windows, thing will be much simpler. You won't even have to worry about Grub, although you can easily add Windows to grub later.

---

### Post by undertakingyou on 2007-08-02
So, you have three seperate hard drives not partitions?  I have found that windows doesn't like to be on a hard drvie that is a slave.  I would remove all harddrives but the one that you want, and then install XP.  That will change the boot loader.  Use a super grub disc to restore grub, and then edit ```
/boot/grub/menu.lst
``` to include the xp disc.  

Super Grub disc can be found here [http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

Hope that helps.

---

### Post by wolfen69 on 2007-08-02
are you asking for help? opinions?

---

### Post by jacktar on 2007-08-02
Can you not disconnect your Linux drive until XP is installed ?

---

### Post by LaRoza on 2007-08-02
> **undertakingyou said:**
> So, you have three seperate hard drives not partitions?  I have found that windows doesn't like to be on a hard drvie that is a slave.  I would remove all harddrives but the one that you want, and then install XP.  That will change the boot loader.  Use a super grub disc to restore grub, and then edit ```
/boot/grub/menu.lst
``` to include the xp disc.  

Super Grub disc can be found here [http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

Hope that helps.
If you have SATA drives, there is no slave, so you don't have to worry about that. (I have Vista on a secondary SATA drive, and it works {as well as it can}).

---

### Post by undertakingyou on 2007-08-02
> **LaRoza said:**
> If you have SATA drives, there is no slave, so you don't have to worry about that. (I have Vista on a secondary SATA drive, and it works {as well as it can}).

That is true, of course it didn't mention that they were SATA before.  
I would still disonnect all drives except the one that you want XP on.

---

### Post by LaRoza on 2007-08-02
> **undertakingyou said:**
> 
I would still disonnect all drives except the one that you want XP on.

I second that.

---

### Post by sekelly on 2007-08-02
Hey there,

I haven't tried this specific guide out myself, but I have used their guide to install Linux onto a machine that already had vista installed and it worked like a charm. Yes I realize they are completely different, it just gave the author some credibility in my eyes.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

this is to dualboot ubuntu feisty fawn 7.04 w/ windows xp, with feisty installed first.

You can take a look at it and see if this would suit your needs. Hope I helped.

---

### Post by asmoore82 on 2007-08-02
1. temporarily disconnect the Linux hard drive completely and move the Windows drive
to Primary Master position; install WinXp to your liking ...

... time and many reboots go by ...

2. add the Linux hard drive back to the configuration but not as Primary Master, let windows
keep that spot.

3. edit the "/boot/grub/menu.lst" file on your linux drive to reflect the new layout of the system.

4. use your BIOS to choose which hard drive to boot, not GRUB... you do not want to create a situation
whereby Windows will fail to boot if/when the GRUB config (linux drive) is changed, removed or damaged.

---

### Post by LaRoza on 2007-08-02
It doesn't seem to matter where the drive is with Vista, it'll boot if it is selected.

---

