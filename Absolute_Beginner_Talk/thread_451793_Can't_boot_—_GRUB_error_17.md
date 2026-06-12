---
title: "Can't boot — GRUB error 17"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by SlaughterDog on 2007-05-22
When I try to boot, I get GRUB error 17. No other information in specified. This happened after I formatted a partition as FAT32 in Windows last night. What's the easiest way to reinstall GRUB or fix the problem?

---

### Post by Ek0nomik on 2007-05-22
> **SlaughterDog said:**
> When I try to boot, I get GRUB error 17. No other information in specified. This happened after I formatted a partition as FAT32 in Windows last night. What's the easiest way to reinstall GRUB or fix the problem?

Here are some links relating to your problem:

[http://ubuntuforums.org/archive/index.php/t-5134.html](http://ubuntuforums.org/archive/index.php/t-5134.html)
[http://ubuntuforums.org/archive/index.php/t-1669.html](http://ubuntuforums.org/archive/index.php/t-1669.html)
[http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802)
[http://www.linuxforums.org/forum/slackware-linux-help/54246-grub-error-17-a.html](http://www.linuxforums.org/forum/slackware-linux-help/54246-grub-error-17-a.html)

---

### Post by SlaughterDog on 2007-05-22
So, GRUB doesn't like my FAT32 partition and will therefor refuse to boot anything? Shall I remove the FAT32 partition?

edit: and another question, how would I get the MS bootloader back, if I wanted to do so?
seeing as I mainly use Windows and just wanted to start trying out Ubuntu, how would I boot Windows right now if I needed to?

edit again: also, according to gparted, my ntfs partition is marked boot but not lba, while my fat32 partition is just marked lba.

---

### Post by SlaughterDog on 2007-05-22
And now, I deleted my fat32 partition and get grub error 22. So, it's time to fixboot or fixmbr and then get help once my main computer is usable again.

dammit, I did fixmbr and it warned me that it could make the partitions inaccessable, but I did so anyway. I'm booting to the livecd of Ubuntu now, I hope I didn't trash my data. Was just about do do my bi-annual backup, too.

Got Windows bootloader installed, so Windows boots. Now I need help installing GRUB and getting it set up. I would think there would be an automatic setup for it, seeing as it auto-setup when I installed Ubuntu.

---

### Post by nonewmsgs on 2007-05-22
do you only have one hard drive?

---

