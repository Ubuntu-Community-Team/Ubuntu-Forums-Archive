---
title: "Win XP &amp; ubuntu Dual-Boot new system"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by LeberMac on 2007-05-03
Greetings!

OK, first time poster, long-time Mac user. I lost my mind recently and built a PC, using hopefully using great-quality components. Well, it's not built yet, but I have lots of boxes of parts which "I get to assemble!" If all goes well, it will be up and running tonight.

What I'm looking to do is get everything stable in Windows XP SP2 first, while leaving a partition for ubuntu later on. Some of the documentation makes this seem entirely too complex, but I have no fear and shall attempt to muddle through.

So, I've read this:[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)
(BTW Thanks Matt)

And, I will download the Linux System rescue CD ISO image from here:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
And make the CD, no problemo. (Just in case.)

When I set everything up in the BIOS with the initial Windows XP Install, I'll make sure to configure it to begin looking for systems on the CD drive first, then on HDD's. (Both my DVD/CD and my HDD are SATA, never worked with that before, but I assume that it's essentially like designating the E: to the DVD, the C: to the HDD partition 1, and then just telling it to look in "E:" first for the OS, right?)

I've got an Abit AW9D-MAX motherboard, so I assume that the BIOS is pretty recent on this thing. I've got a 320 GB HD which I'll "hard" partition into something like 220 GB for WinXP partition, and 100 GB for ubuntu partition.

I have some specific questions before I'll attempt this:

1. Any advice on how best to partition the HDD? NTFS file format on all partitions? Should I let WinXP do the partitioning or some other utility? Whatever will allow me to install ubuntu on the smaller partition would be great.

2. I have an nVidia 8800 GTS videocard, which will support DX9, DX10, and OpenGL. If I set up the initial BIOS with Windows XP to use DX9, can I setup the ubuntu install to use OpenGL? Or will this cause my card to have a schizophrenic episode and break on me? I see drivers for this card at: [http://www.phoronix.com/scan.php?page=news_item&px=NDAzOA](http://www.phoronix.com/scan.php?page=news_item&px=NDAzOA)

3. I do not have a standard keyboard or mouse. (Hell I forgot that I might actually need a Floppy Drive and hastily added it to my order at the last minute.) Both input devices are USB. Should I be worried? Some accounts make it seem like you'd BETTER have PS2-style mice and kybds or the computer won't recognize your input devices. (As in, you won't be able to type stuff because the USB drivers have not loaded before the BIOS starts asking you a buncha questions.)

I'm sure I'll have other questions as I attempt this. :)

---

### Post by jvc26 on 2007-05-03
Dual Boot Ubuntu and Linux, there is a simple guide [here]("http://www.psychocats.net/ubuntu/installing") You want to partition for the Ubuntu file system iteslf in ext3 probably. You have a choice for data partitions of ext2 (I think) with Windows drivers for it, or NTFS, with the ntfs-3g drivers for Ubuntu, as Ubuntu doesn't support ntfs read-write out of the box as it is a Microsoft proprietary file system.
Il

---

### Post by LeberMac on 2007-05-03
Perfect. Thanks, Illuvator!
I'll go like this route:
[IMG]http://www.psychocats.net/ubuntu/images/partitioning4.png[/IMG]

Except with a smaller Fat32 partition, I'll just use it as a swap area in case I have to go back & forth.
I'm thinking, that from a 320 GB HD (more or less, probably only 300 GB when formatted)
200 GB for Windows XP C:
20 GB for Fat32 Swap partition D:
20 GB for ubuntu system install E:
75 GB for ubuntu /home partition F:
5 GB for swap partition G: (I've got 2 GB RAM, may upgrade to 4 GB eventually...)

FDD will be A:
DVD-R will be H:

---

### Post by Vekin on 2007-05-03
Consider:

[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

There's now a Windows driver that lets your Windows boot read and write EXT3 partitions.  Also, note that there's a simple download that will let your linux partition read NTFS partitions as well.  The above image is what I use, and I like it fairly well.  Though I have to be honest, I haven't really used windows since I installed Ubuntu.  :wink:   The only real reason I would is for games, which I don't play much anymore, and still, I hear Wine would let me do that on Linux anyway. 

There's no problem with your partitioning scheme from what I can see, it's just something to think about :-)

---

