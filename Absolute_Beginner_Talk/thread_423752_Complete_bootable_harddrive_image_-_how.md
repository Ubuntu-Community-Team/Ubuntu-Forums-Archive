---
title: "Complete bootable harddrive image - how?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Ciddan on 2007-04-26
Hello all.

I've got a laptop with a WinXP/Ubuntu dual-boot set up. Recently my laptop started showing me the beloved "No Operating System Found"-screen. So I'm suspecting that the internal 40GB drive is giving up. I've done some maintenance with various tools but the screen keeps coming back after a few days. I can still boot the system via a Ubuntu LiveCD and selecting Boot From First Disc which sends me to a working grub.

However I do not trust my drive at all, and I want to replace it. What I'm wondering is if there is any distro I can boot using a LiveCD and do a full, complete, bootable image file that I can later blast on to my new drive. I'd need the image to include grub, my MBR etc.

I've got plenty of external storage so saving the image file won't be an issue.

Any recommendations? Thanks alot.

---

### Post by Bachstelze on 2007-04-26
[http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage)

---

### Post by Ciddan on 2007-04-26
> **HymnToLife said:**
> [http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage)

This application seems to only back up partitions. What I really need is something to backup the entire drive. Ideally it'd be an application that is file-system agnostic and just saves an image of the entire drive - including the low level stuff.

I could use partimage to make one backup of the WinXP partition and another image of the ubuntu partition - but I really don't want to mess with a slapped on manual grub install and taking the risk of not being able to boot from the drive.

---

### Post by orb9220 on 2007-04-26
[http://ubuntuforums.org/showthread.php?t=360283](http://ubuntuforums.org/showthread.php?t=360283)

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by Ciddan on 2007-04-27
> **orb9220 said:**
> [http://ubuntuforums.org/showthread.php?t=360283](http://ubuntuforums.org/showthread.php?t=360283)

I guess I'll just do a data backup and reinstall. That guide had a nice partition setup :) Thanks!

---

