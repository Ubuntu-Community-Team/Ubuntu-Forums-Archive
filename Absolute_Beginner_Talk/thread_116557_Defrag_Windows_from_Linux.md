---
title: "Defrag Windows from Linux"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2006-01-13
Is it possible to get a defragment tool that will defragment a windows partition from linux, my windows is horribly fragmented, but also i would like to defragment its page file which is ignored in a windows defragment

---

### Post by AMD64_N_Linux on 2006-01-13
[quote=notquitehere188]Is it possible to get a defragment tool that will defragment a windows partition from linux, my windows is horribly fragmented, but also i would like to defragment its page file which is ignored in a windows defragment[/quote]

While I do not know of any way to defrag a Windows partition from Linux,) anyone else ? ) I dont think it is possible.

As far as defragging the pagefile, go to

[http://www.sysinternals.com/utilities/pagedefrag.html](http://www.sysinternals.com/utilities/pagedefrag.html)

This utility will allow you to do a pagefile defrag on a reboot of windows.

This is an ubuntu forum so, I hope that this has helped, but that is the best I can do.

---

### Post by gord on 2006-01-13
i would also suggest a product called Diskeeper, its prolly the best defragmenter around and does everything you could think of, maybe more. if youv got a windows drive lieing around just for games like me, fragmentation is a big issue ;)

---

### Post by public_void on 2006-01-13
I doubt you can defrag a Windows drive from Linux if it hasn't got right access. So if the drive is NTFS then no, as the drive would be read-only to Linux. Also I haven't heard of any defrag tools for Linux (I could be wrong), so I'm not sure if what you want is even possible for Linux, let alone for a Windows drive.

---

### Post by Rinzwind on 2006-01-13
[QUOTE=public_void]I doubt you can defrag a Windows drive from Linux if it hasn't got right access. So if the drive is NTFS then no, as the drive would be read-only to Linux. Also I haven't heard of any defrag tools for Linux (I could be wrong), so I'm not sure if what you want is even possible for Linux, let alone for a Windows drive.[/QUOTE]
[http://www.oo-software.com/en/products/oodlinux/](http://www.oo-software.com/en/products/oodlinux/)

Features of O&O Defrag Linux V1.0

    * Analysis/defragmentation of EXT2 and EXT3 drive partitions, the standard Linux file systems
    * Analysis/defragmentation of individual files 
    * Analysis/defragmentation of individual partitions
    * Secure defragmentation with the unique "Security Mode". This enables you to repair an inconsistent file system when O&O Defrag Linux has been abnormally ended (e.g. by a power cut).
    * Various defragmentation methods:
          o Normal defragmentation
          o SPACE - defragmentation 
    * The static version of O&O Defrag Linux can be started from a floppy disk (1,44 MB). In this way it is possible to optimize the root partition of the system with the help of a a start floppy or CD in combination with O&O Defrag Linux.

---

### Post by public_void on 2006-01-13
@Rinzwind: Ahh, proven wrong. Didn't know that, thanks.

---

### Post by Rinzwind on 2006-01-13
Hey I just opened google to see if there was any ;) 

I was surpriced to even find one :rolleyes: :rolleyes: :rolleyes: :rolleyes:


And to stay ontopic:
NTFS. No way.
FAT? Not likely. Why would you?


Page file defragmenting: Set it to 0. Reboot. Recreate it. Done.

---

### Post by AMD64_N_Linux on 2006-01-13
[quote=Rinzwind]Hey I just opened google to see if there was any ;) 

I was surpriced to even find one :rolleyes: :rolleyes: :rolleyes: :rolleyes:


And to stay ontopic:
NTFS. No way.
FAT? Not likely. Why would you?


Page file defragmenting: Set it to 0. Reboot. Recreate it. Done.[/quote] 

*** TAKE NOTE :: that is BETA software, and see the big disclaimer, you know, the typical, if your girlfriend leaves you ,,,, if your dog loses his hair,,,, better read the fine print.

I still say that there isnt a defragmenter for Windows from Linux, at least until they release it as a finished product, you know, like windows xp,,,,,

silly me....


One more note ..... 


Linux (ie GPL) BETA testing vs. Windows (proprietery) BETA testing 

With Linux, you get to see the source code,  ask O&O Defrag to see their source code, they havent had a good laugh in a while.

---

### Post by Ptero-4 on 2007-03-31
A linux defragger capable of defragmenting your windoze partition would be good for situations where you need to resize a windoze partition and the windoze in it is unbootable.

---

