---
title: "[SOLVED] Problems with NTFS configuration utility"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-09
I am one of those new users of Feisty with an XP-Linux dual boot machine, and I just installed the NTFS tool a few hours ago [COLOR="Blue"]**_[following these directions]("http://ubuntuforums.org/showthread.php?t=217009")_**[/COLOR].

When I attempted to run the NTFS Configuration utility, one of my Windows disks was recognized (I have two). The message said:
[INDENT]The following new partitions were detected and can be configured:
/dev/hda1 [/INDENT]
But when I clicked the APPLY button to "*Enable read/write support for internal drive*," I got this message:
[indent]Error : An error occured when trying to configure
 /media/WINDOWS, please retry. Thanks.[/indent]

As I was composing this message and going through these steps one at a time, the NTFS Configuration utility apparently worked, and it enabled one of my Windows drives. I was able to save some notes successfully to it.

Delighted, I tried to run it again. But it did not seem to see the other drive at all, which is the drive I had "My Documents" on.

Can anyone tell me how to get this working?

---

### Post by gn2 on 2007-10-09
By far the simplest way I know is using the FAT32 and NTFS Auto-Mounting Utility available through Automatix.
It's in the Miscellaneous category after you've got Automatix installed.

Be aware it's believed by some that using Automatix may cause problems.
Should you encounter any difficulty Automatix has it's own excellent support.
(however most who use it have no problems at all)

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Joeb454 on 2007-10-09
If you don't want to use Automatix like gn2 suggested, you could always wait 9 days until Gutsty is released (Ubuntu 7.10)

That has NTFS support from the word go. (To get gutsy you just need to check for updates using the Update Manager on or after the 18th of October)

---

### Post by Alan Stancliff on 2007-10-10
> **gn2 said:**
> By far the simplest way I know is using the FAT32 and NTFS Auto-Mounting Utility available through Automatix.
It's in the Miscellaneous category after you've got Automatix installed.

Be aware it's believed by some that using Automatix may cause problems.
Should you encounter any difficulty Automatix has it's own excellent support.
(however most who use it have no problems at all)

[http://www.getautomatix.com/](http://www.getautomatix.com/)

I did a bit of reading about Automatix, and being a beginner and not wanting to spend time fixing avoidable mistakes, I decided not to use it. The UbuntuGuide Wiki gives a [***_[COLOR="RoyalBlue"]very strong warning[/COLOR]_***]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2") against using it.

> **Joeb454 said:**
> If you don't want to use Automatix like gn2 suggested, you could always wait 9 days until Gutsty is released (Ubuntu 7.10)

That has NTFS support from the word go. (To get gutsy you just need to check for updates using the Update Manager on or after the 18th of October)
That's good advice. There's plenty I can learn and do over the next week and a few days. I'll wait for the next release of Ubuntu.  I am going to mark this thread **RESOLVED** and move on

Thanks to both of you, GN2 and JoeB454 for helping me learn more about Ubuntu.

---

