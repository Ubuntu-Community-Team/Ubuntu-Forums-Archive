---
title: "Triple/Quad boot rEFIt/Gparted GPT problem"
date: 2009-04-23
forum: Apple Hardware Users
---

### Post by amidnightrambler on 2009-04-23
Ok, this is my situation. I installed rEFIt on my Macbook Pro in order to manage the other OSs I was going to load. I then installed 32bit vista and Ubuntu. At this point all was well. I had used Gparted a few times to resize the NTFS partition for the vista and resized the HFS+ as well for the OSX. This triple boot setup was working fine until I tried to load my military copy of windows xp. I work as a localized NA and computer maintenance for my army unit. After loading the fourth OS, being the windows xp, the vista, ubuntu, and the xp all showed up as xp boots in rEFIt. Soon after I loaded Gparted again and deleted the xp partition thinking that the xp was causing the problem. Afterward I only had OSX and xp on the rEFIt panel and the xp wouldn't boot. When I boot into OSX I can still read and write to my vista partition via NTFS-3g so I know the partition is still intact. I then booted Ubuntu live and re-setup grub. This made Ubuntu visiable again, but now there are two Linux OSs and neither are booting along with vista still not booting. Even more so, when I tried to sync in rEFIt I see that I have no GPTs I only have MBRs. Normally I wouldn't post in a forum for help. I would normally search forums for answers and search the entire web for answers and never post but for once I have given up. I do believe I am stumped.

---

### Post by hajk on 2009-04-23
Well, you've run up against a limitation of Apple's EFI replacement for the old BIOS: "legacy" OS'es (like Windows or Ubuntu) can only boot from one of the "primary" partitions, i.e. numbered 1 - 4. Since the first partition is a small 250MB partition reserved for EFI, that means that you can boot at most 3 legacy OS'es (OS X itself can boot from any partition, also > 4).

Now, in your case, OS X presumably occupies partition 2, and Windows and Ubuntu occupy partitions 3 and 4. So, that's why your additional OS won't boot, because it is likely installed on a partition > 4.

So, what to do? This situation is described in one of the wikis, just follow the links in the sticky FAQ at the start of this Apple forum. It would probably require moving (reinstalling with SuperDuper) your Mac OS X partition to one numbered > 4, thereby freeing partition number 2 for your third "legacy" OS.

There is another possibility, not yet entirely ready for prime time: move the Ubuntu partition to one numbered > 4, then use the grub-efi method (part of Grub2) to boot in non-MBR mode, etc. There is an active thread here showing what all's involved.

Have fun!

---

### Post by cyberdork33 on 2009-04-23
With all that you are saying, I am kinda left wondering what the state of your machine is right now... In OSX, can you use /Applications/Utilities/Partition Inspector (Tool from rEFIt) to post a report of your partition tables?

The no GPT thing is usually not good...

For Vista, you probably need to reinstall the Vista bootloader. This is done by booting the Vista CD into recovery console and using the ```
bootrec /fixmbr
``` command. You can find details on this online.

---

