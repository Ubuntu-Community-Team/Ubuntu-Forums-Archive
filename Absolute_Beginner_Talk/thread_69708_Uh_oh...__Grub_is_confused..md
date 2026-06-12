---
title: "Uh oh...  Grub is confused."
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Scuddie on 2005-09-27
This morning I tried to install Breezy Kubuntu.  Installation went as expected.  When time came to partition the drives, I selected manual partition.  I setup a 255MB /boot ext2 partition, a 1536MB swap partition, and dedicated the rest to a / ext3 partition.  Installed Grub on (hd1).  It seemed everything went well.  However, when time came to reboot, Grub got all confused.  I selected Ubuntu, and it came out with an error message, telling me it didnt understand the partition type 0x07.  I said screw it and decided to boot WinXP, but a different error occurred.  It told me it couldnt boot from the recognized ext2fs 0x83.  Obviously, something wasn't right.

Here are some details.  I am running XP with a 160GB drive, which is primary master.  I came across a spare 17.2GB disk, and installed it as secondary slave (bad choice, I know, but it was my only one for the moment).  I killed the contents of that drive to prepare it for Breezy Kubuntu.  Install was done, when I rebooted, I pressed F8 to force boot from HDD-1, and grub loaded.  Then the skies fell (not really :p).

So, with all that info given, could someone tell me what I did wrong?

---

### Post by mlomker on 2005-09-27
[This is a pretty good thread]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/397949.html") about reinstalling grub.  I've done this before using a Knoppix boot CD (when I got my new laptop and moved my system over).

---

### Post by Scuddie on 2005-09-27
That is a good thing to know.  However, it didnt help me because Grub wasn't working in the first place.  The boot manager loads just fine, but the references are all out of whack.  On top of that, I don't know how the /dev/hdX assignment works.  If I knew how it did, I wouldnt have to post back here.  I know reference to /dev/hda1 would boot WinXP, but I don't know what would boot to linux.

PRI MST: 160GB drive w/ WinXP
PRI SLV: None
SEC MST: DVD-RW Drive
SEC SLV: 17.2GB drive w/ Ubuntu (/boot partition is the 1st)

I would assume since using (hd1) would be valid, that /dev/hdb1 would be the appropriate pointer.  However, that doesn't explain how WinXP doesnt work from grub either.  It seems the references are all messed up, but they seemed to list properly in the .conf, so I have no idea where this is going.

---

### Post by mlomker on 2005-09-27
> /dev/hdX assignment works.  If I knew how it did, I wouldnt have to post back here.  I know reference to /dev/hda1 would boot WinXP, but I don't know what would boot to linux.


There was a passing reference to it on that page.  There is a lot of documention about grub on Google because it's used by so many linux distros.

```

Remember that for grub (hd0,1) means hda (primary controller master), second partition.

```

Here's [another one]("http://geodsoft.com/howto/dualboot/grub.htm#install").  They show the find command in the *installing grub* section that will look for the Ubuntu partition.

---

### Post by Scuddie on 2005-09-27
I don't think you understand my problem.  Grub loads just fine.  The pointers are also looking to point in the correct location according to the conf (my XP install is identified to load from (hd0,0), which is correct).  However, for some strange reason, I see an error reference /dev/hdd4, which I don't even have.  So to sum it up, (hd0,0) is pointing to /dev/hdd4 for some strange reason.  This isnt a user error from being where I wasn't supposed to, because I haven't done that... yet :D.

---

### Post by mlomker on 2005-09-28
> I see an error reference /dev/hdd4, which I don't even have.  So to sum it up, (hd0,0) is pointing to /dev/hdd4 for some strange reason.  This isnt a user error from being where I wasn't supposed to, because I haven't done that... yet :D.

An error reference when?  I'm not understanding because you aren't being clear.  You try to boot Windows from grub but it gives you an error message about hdd4?  Does Breezy boot?

Post your /boot/grub/menu.lst.  The links that I have given you would help to create a new menu.lst.  If you need to get into winXP and it isn't letting you then boot your WinXP cd into the recovery console and do a **fixmbr** to get it back.

At this point I'm really not sure what isn't working for you...

---

