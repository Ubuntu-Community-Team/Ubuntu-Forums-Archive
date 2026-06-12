---
title: "Duel Booting"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-11
I have one 80 Gig Hard Drive that is running Windows 2000.
I'd like to Duel Boot but have never set up a Duel boot in my life.

On this 80 Gig drive is 2 partitions C: and D:

C: has 24 Gigs of Free Space
D: has 38 Gigs of Free Space

I plan to set up Ubuntu and have it look like this
/
Swap
Home

My issue and why I am so scared is if something should happen to windows
and windows needed to be reinstalled.

If I should need to install Windows in 6 months or so, how could
I save Linux...... Wouldn't the Boot loader be an issue with a Windows
reinstall....

I have a Current Ghost Image of The C: and D: partitions and I would
just blast that back onto the Windows Partitions.

Could someone tell me if this would be a problem.... Thank you :KS

---

### Post by por100pre1 on 2007-10-11
You can use the Guided -use largest free space option, **but first backup your windows files first to removable media or external hdd**. **[COLOR="Red"]To backup your files first is paramount.[/COLOR]** :)

---

### Post by celticbhoy on 2007-10-11
Backup
Cleanup system
Defrag
Install Ubuntu as suggested above
Make a new ghost image of the drives, otherwise if you use the old one to re-install windows you will wipe out Ubuntu.

---

### Post by Orbital75 on 2007-10-11
> **celticbhoy said:**
> Backup
Cleanup system
Defrag
Install Ubuntu as suggested above
Make a new ghost image of the drives, otherwise if you use the old one to re-install windows you will wipe out Ubuntu.

Humm.... Well I was just planning on backing up the C: and D: windows partitions.
Will Ghost back up a ext3 file system?

If so, I'll just Ghost the whole thing........ I Ghost to DVD RW

---

