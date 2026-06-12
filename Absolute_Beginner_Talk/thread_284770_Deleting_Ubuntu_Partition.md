---
title: "Deleting Ubuntu Partition"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by tellboy on 2006-10-26
I installed Ubuntu on the hard drive with XP as a seperate partition. I want to remove Ubuntu completely.
Do I just insert the XP CD and select repair or do I need to format and reinstall XP completely
Thank You

---

### Post by daou on 2006-10-26
Go check this thread:

[http://ubuntuforums.org/showthread.php?t=258776]("http://ubuntuforums.org/showthread.php?t=258776")

look at pay's reply

---

### Post by tellboy on 2006-10-26
I understand except how do you delete the linux partitions is this within UBUNTU or XP ?


Re: Uninstall Ubuntu / Restore XP 

--------------------------------------------------------------------------------

delete the linux partions boot from win xp cd go to repair console 
follow prompts then type 

fixmbr
fixboot 
exit 

reboot pc and your back into windows 

or run the fix 1st then delete and format the linux partions using windows
__________________

---

### Post by elchinovi on 2006-10-26
For what I can tell, the first set of instructions will fix the mbr so it loads directly to XP, and then, once you are running XP, you can go to Disk management, and re-format the ubuntu partition to whatever you like, let's say, NTFS.
Hope that helps.
Good Luck!

---

### Post by navneeth on 2006-10-26
Could someone please tell me what 'fixboot' does? I had problems with Kubuntu and deleted the whole thing from Windows, but after that windows wouldn't boot. So I put the CD in and only did a fixmbr and got windows running again, but I don't remember doing a fixboot.

---

### Post by elchinovi on 2006-10-26
> **navneeth said:**
> Could someone please tell me what 'fixboot' does? I had problems with Kubuntu and deleted the whole thing from Windows, but after that windows wouldn't boot. So I put the CD in and only did a fixmbr and got windows running again, but I don't remember doing a fixboot.

Fixboot writes a new partition boot sector to the system partition. The fixboot command is only available when you are using the Recovery Console.

---

### Post by navneeth on 2006-10-26
Hmm...I did go into the recovery console to do the fixmbr. Anyway, I think I might have to do that again, since I'm planning to do a fresh install of Edgy(dual boot with XP, updating from Dapper). Please tell me if this is the right thing to do...

-Delete Ubuntu (I have GParted LiveCD)
-Load Windows CD...get back XP
-Install Edgy

Thanks.

---

