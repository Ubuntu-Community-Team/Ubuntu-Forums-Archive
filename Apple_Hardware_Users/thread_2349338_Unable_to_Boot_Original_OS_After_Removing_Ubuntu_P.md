---
title: "Unable to Boot Original OS After Removing Ubuntu Partition"
date: 2017-01-13
forum: Apple Hardware Users
---

### Post by cal2u on 2017-01-13
[COLOR=#000000]Hi all,[/COLOR]

[COLOR=#000000]SHORT VERSION:[/COLOR]

[COLOR=#000000]I decided to dual boot OS X Sierra and Ubuntu 16.04 using this guide ([/COLOR][http://courses.cms.caltech.edu/cs171...and_Ubuntu.pdf]("http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf")[COLOR=#000000]), and everything worked fine. After deleting that partition, though, I'm no longer able to boot into OSX. I'm not sure what the Ubuntu install process does to make itself bootable, so any help getting my original system running again would be greatly appreciated![/COLOR]

[COLOR=#000000]LONG VERSION:[/COLOR]

[COLOR=#000000]After installing Ubuntu 16.04 onto a partition I created on my mac, I was able to boot into OS X by holding down the option key at startup and selecting "Macintosh HD" as my startup disk. This was without installing anything like rEFInd.[/COLOR]

[COLOR=#000000]At this point there weren't any problems, but later I needed to have Ubuntu 14.04 instead of 16.04 installed, and the partition I had created for Ubuntu was too small. I wasn't able to remove the Ubuntu 16.04 partition using OS X's Disk Utility (a warning sign, maybe), so I booted up a Ubuntu 14.04 live cd and deleted the Ubuntu partition using gparted. At that point I wanted to resize my OS X partition, but Ubuntu wasn't able to do anything with my encrypted hsf+ partition, so I tried to boot back into OS X to resize it. I then discovered that I could no longer boot into OS X from the startup options menu.[/COLOR]

[COLOR=#000000]I've installed Ubuntu 14.04 on my original 16.04 partition, thinking that perhaps it would magically make OS X bootable again on the startup options menu. Alas, the Ubuntu partition boots automatically, but Machintosh HD isn't an option when I boot up holding down the option key.[/COLOR]

[COLOR=#000000]Any advice on how to boot into my OS X partition now? Doing a network recovery is an option I think, but I'm worried about losing files I have installed on my OS X partition.[/COLOR]

---

### Post by howefield on 2017-01-13
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by cal2u on 2017-01-13
I was hoping to get insight on how the Ubuntu install process works in general, as I had not received any responses on the Apple Hardware Users subforum.

---

### Post by howefield on 2017-01-13
I see, missed that this was a duplicate thread so let's close it.

Feel free to bump your original thread daily to keep it up the pile, after all it has only been a day since it was posted.

---

