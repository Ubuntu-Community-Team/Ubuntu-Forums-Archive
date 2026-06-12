---
title: "Help!Windows XP hang after install Ubuntu"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Nightin on 2007-05-31
I used to have disk C, D, E, F in Windows, I use F to install Ubuntu, But after the installation, I can't enter Windows any more: The microsoft logo appears for a short while and then blue screen appears, saying that I should run DSKCHK /F to see if something's wrong with the disk. I know it was formatted to ext3. The problem is that I can't even enter DOS mode to run ghost or re-install windows with CDs. Is it because of GRUB? I'm a little confused, at least my boot disk should lead me to DOS mode, but that always fails.

Another problem is that every time Ubuntu starts, it checks all the file systems using fdsk(?). This process always takes up a long time and finally died with exit code 1, does it have something to do with the windows xp failure?

Please, I love Ubuntu, but I also need windows badly...

---

### Post by Cypher on 2007-05-31
If you simply re-formatted an existing NTFS XP partition to EXT3, the only time this would cause issues in XP is if it was looking for something on a drive it knew as F: If that isn't the case, there should be no reason why it would hang.

As long as GRUB is allowing you to boot into Ubuntu and XP, then it's job is done and it isn't interfering anymore.

After you choose to boot into XP, hit the F8 key and then try going into Safe Mode and if that doesn't do anything, Last Known Good Configuration to see if either will allow you to get somewhere.

Additionally, the XP CD should get you to a "Recovery Console" from where you should be able to run the "chkdsk /f" command Windows is suggesting..

---

### Post by Nightin on 2007-06-01
> **Cypher said:**
> If you simply re-formatted an existing NTFS XP partition to EXT3, the only time this would cause issues in XP is if it was looking for something on a drive it knew as F: If that isn't the case, there should be no reason why it would hang.

As long as GRUB is allowing you to boot into Ubuntu and XP, then it's job is done and it isn't interfering anymore.

After you choose to boot into XP, hit the F8 key and then try going into Safe Mode and if that doesn't do anything, Last Known Good Configuration to see if either will allow you to get somewhere.

Additionally, the XP CD should get you to a "Recovery Console" from where you should be able to run the "chkdsk /f" command Windows is suggesting..
Thanks, but this seems isn't help. Both safe mode and last known good configuration won't work. the XP CD leads me to "Setup is inspecting your computer's configuration" screen and then it stops there.

By the way, my ubuntu always run the "fsck" command and check my whole hard disk during start up, even if the system is shut down normally.

---

