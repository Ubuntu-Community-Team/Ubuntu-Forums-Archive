---
title: "Recognizing a fifth partition..."
date: 2011-02-14
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2011-02-14
Before I begin, I'd like to point out this is not an Ubuntu problem. **However** I believe my best option for solving this issue lies with Ubuntu and its community, so hopefully someone has some ideas...

A week or so ago, I decided to reorganize my partitions a bit. Originally, I had a dual boot machine with Mac OS X (SL) and Windows 7, then a shared NTFS partition housing Firefox, Thunderbird and iTunes profiles (which are shared between Win and Mac). I was getting annoyed with how often Mac OS X crashed with NTFS-3g (using MacFuse) being the problem, so I decided to switch over to FAT. No crashing, but I started to notice iTunes slowing down when it was accessing its music library.

So I had an idea: Windows 7 can access HFS, but doesn't read to it...which honestly I don't need it to do for iTunes. I replaced my shared partition with a smaller FAT partition for my Firefox and Thunderbird profiles, and a larger HFS+ partition for my iTunes library.

So here's the problem: Windows refuses to acknowledge the iTunes partition, as it's technically the fifth partition in the MBR. And this is where I say "Crap, how do I fix this?" My old scheme was functional, but not ideal. I could put my iTunes library on the Mac OS X partition, the problem being that I would have to shift the Windows 7 and shared partitions over so I could expand the drive (there's not enough room for my iTunes library otherwise). 

My only other thought was that maybe I could somehow flag my HFS as a logical drive? To be honest, I only vaguely comprehend how an MBR works, so I have no idea if this is even possible.

Any thoughts someone might have would be vastly beneficial. Thanks in advance!

---

### Post by An Sanct on 2011-02-14
As far as I know, only 4 partitions can be made, with the fifth as a partition in a "extended" partition, thus a container, that holds it. That way windows, mac and Linux will be able to see it (according to the format you choose)

PS. Maybe only three are possible with the fifth in the extended (fourth) ... Take a look at this [wiki]("http://en.wikipedia.org/wiki/Disk_partitioning")

---

### Post by oldfred on 2011-02-14
I do not know Macs. But it is my understanding they use gpt. But then to work with windows which will not boot from gpt they create a hybrid MBR/gpt. Supposedly win7 64 bit will boot from gpt with efi and windows should read gpt.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
[http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx](http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx)

GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)

---

### Post by srs5694 on 2011-02-14
> **teamjh14 said:**
> So here's the problem: Windows refuses to acknowledge the iTunes partition, as it's technically the fifth partition in the MBR.

There is no such thing as a "fifth partition in the MBR," at least in terms of primary MBR partitions. It may be the fifth partition in the GPT, which means it probably isn't in the hybrid MBR that Windows is reading.

> My only other thought was that maybe I could somehow flag my HFS as a logical drive?

***Nonononononononononononononononononononononononononononononono!!!!!!!!!!!!***

Sorry for being melodramatic, but as the author of the [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) disk partitioning tool, those words make me cower in fear. [Hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) are ugly and dangerous enough as it is. They're a regular Pandora's Box for partitioning. Putting an extended partition (with associated logical partitions) in a hybrid MBR is sheer insanity. Doing that would be like a thousand Pandora's Boxes, all on one hard disk. Don't even think about it. (If anybody in the future has done this and reads these words, please don't contact me asking for help. Just erase your disk and start over from scratch.)

Chances are you can get your iTunes partition into your hybrid MBR, but you may need to use software other than the standard Apple fare for doing the job. My GPT fdisk (available for Linux, OS X, and Windows; see the [downloads page](http://sourceforge.net/projects/gptfdisk/files/)) will do the job, as described on my  [hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) page. You can have up to three partitions in your hybrid MBR. Presumably that will be your Windows boot partition, your iTunes partition, and up to one other partition that Windows can read. Your OS X partitions don't need to be in the hybrid MBR, so you can just omit them.

---

### Post by Tu1J4kXk8NUhMz on 2011-02-14
> **oldfred said:**
> I do not know Macs. But it is my understanding they use gpt. But then to work with windows which will not boot from gpt they create a hybrid MBR/gpt. Supposedly win7 64 bit will boot from gpt with efi and windows should read gpt.


Yes, Mac runs off a GPT. I have read, actually, that Windows XP 64 bit (or some derivation thereof, like Server edition or something) can read GPT. This intrigues me (in fact, I'm running Win7 64bit Ultimate) but I don't really have the patience or interest to try and get this working.

> **srs5694 said:**
> There is no such thing as a "fifth partition in the MBR," at least in terms of primary MBR partitions. It may be the fifth partition in the GPT, which means it probably isn't in the hybrid MBR that Windows is reading.

True. I misspoke.

> **srs5694 said:**
> 
***Nonononononononononononononononononononononononononononononono!!!!!!!!!!!!***

Sorry for being melodramatic, but as the author of the [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) disk partitioning tool, those words make me cower in fear. [Hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) are ugly and dangerous enough as it is. They're a regular Pandora's Box for partitioning. Putting an extended partition (with associated logical partitions) in a hybrid MBR is sheer insanity...

Chances are you can get your iTunes partition into your hybrid MBR, but you may need to use software other than the standard Apple fare for doing the job. My GPT fdisk (available for Linux, OS X, and Windows; see the [downloads page](http://sourceforge.net/projects/gptfdisk/files/)) will do the job, as described on my  [hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) page. You can have up to three partitions in your hybrid MBR. Presumably that will be your Windows boot partition, your iTunes partition, and up to one other partition that Windows can read. Your OS X partitions don't need to be in the hybrid MBR, so you can just omit them.

Alright, brother. Bring it down a notch. While logical drives are not my favorite animal, they are still a viable option. But yes, hybrid MBRs end up being a bit temperamental, so I don't think this is the way I'll go.

I've actually been trying to find some way to omit my OS X partition, so if you have info on doing that, please share!

---

### Post by srs5694 on 2011-02-15
> **teamjh14 said:**
> Yes, Mac runs off a GPT. I have read, actually, that Windows XP 64 bit (or some derivation thereof, like Server edition or something) can read GPT. This intrigues me (in fact, I'm running Win7 64bit Ultimate) but I don't really have the patience or interest to try and get this working.

Windows Vista and 7, and some earlier versions, can handle GPT fine as data drives, but Windows can't boot from GPT disks except on UEFI-based systems. (Note that's *U*EFI 2.x; Apple uses an earlier EFI 1.x implementation, so Windows only boots on Macs using a BIOS compatibility mode in Apple's EFI.)

> Alright, brother. Bring it down a notch. While logical drives are not my favorite animal, they are still a viable option. But yes, hybrid MBRs end up being a bit temperamental, so I don't think this is the way I'll go.I have no objection to extended and logical partitions on pure MBR drives, but on disks with *hybrid MBRs*, as under discussion in this thread, use of extended and logical partitions is outright foolhardy. To the best of my knowledge, no utility supports creating such a monstrosity. The core of the reason why is that logical partitions require data structures (known as [Extended Boot Records, or EBRs]("http://en.wikipedia.org/wiki/Extended_boot_record")) that exist just before the partitions they define. GPT has no such requirements; all GPT partitions are defined entirely within the main GPT data structures at the start and end of the disk. This will limit which GPT partitions you can turn into hybrid logical partitions. Worse, suppose you create a hybrid table with a logical partition that's legal because there's a gap between two partitions, so the EBR can reside in that gap. Now suppose you decide you want to create a new GPT partition between those two partitions. The new GPT partition now occupies space legally in the GPT, but it overlaps that critical EBR. This might work for a while, but as soon as you write data (legally from a GPT perspective) to the sector with the EBR, you'll scramble the definition of that logical partition and you'll lose all access to any subsequent logical partitions (because logical partitions are defined using what's known as a linked-list data structure, in which one entry contains a pointer to the next, so if one is damaged you lose all the rest).

There are a host of similar problems with implementing a hybrid MBR that utilizes extended/logical partitions. Although it would be possible for any one program to disentangle some or all of the messes that could ensue from this sort of system, there's no way to guarantee that other programs would do the same. That is, suppose somebody wrote RecklessGPT, the GPT partitioning tool that lets you create a hybrid MBR with extended and logical partitions. RecklessGPT might prevent you from creating a GPT partition that occupies the space needed by the EBR; however, the user might just use GParted, GPT fdisk, OS X's Disk Utility, or some other tool to edit the partition table, and those programs do not provide such protections, so you could easily get into trouble.

So to sum up, I will not "bring it down a notch." I understand you did not realize how dangerous what you were suggesting was, but I do. I've given the matter a fair amount of thought. I've seen the problems that even run-of-the-mill hybrid MBRs cause, and the thought of hybrid MBRs with extended and logical partitions gives me the screaming heebie-jeebies.

> I've actually been trying to find some way to omit my OS X partition, so if you have info on doing that, please share!

If you mean omitting the OS X partition from the hybrid MBR, please read the pages to which I linked in my earlier message. You just need to create a new hybrid MBR with a more flexible program (such as GPT fdisk or some versions of gptsync, but not the most common versions of gptsync), which let you specify which GPT partitions get included in the hybrid MBR -- and therefore, by implication, which partitions get omitted from it.

---

### Post by Tu1J4kXk8NUhMz on 2011-02-15
> I have no objection to extended and logical partitions on pure MBR drives, but on disks with *hybrid MBRs*, as under discussion in this thread, use of extended and logical partitions is outright foolhardy. To the best of my knowledge, no utility supports creating such a monstrosity. The core of the reason why is that logical partitions require data structures (known as [Extended Boot Records, or EBRs]("http://en.wikipedia.org/wiki/Extended_boot_record")) that exist just before the partitions they define. GPT has no such requirements; all GPT partitions are defined entirely within the main GPT data structures at the start and end of the disk. This will limit which GPT partitions you can turn into hybrid logical partitions. Worse, suppose you create a hybrid table with a logical partition that's legal because there's a gap between two partitions, so the EBR can reside in that gap. Now suppose you decide you want to create a new GPT partition between those two partitions. The new GPT partition now occupies space legally in the GPT, but it overlaps that critical EBR. This might work for a while, but as soon as you write data (legally from a GPT perspective) to the sector with the EBR, you'll scramble the definition of that logical partition and you'll lose all access to any subsequent logical partitions (because logical partitions are defined using what's known as a linked-list data structure, in which one entry contains a pointer to the next, so if one is damaged you lose all the rest).

There are a host of similar problems with implementing a hybrid MBR that utilizes extended/logical partitions. Although it would be possible for any one program to disentangle some or all of the messes that could ensue from this sort of system, there's no way to guarantee that other programs would do the same. That is, suppose somebody wrote RecklessGPT, the GPT partitioning tool that lets you create a hybrid MBR with extended and logical partitions. RecklessGPT might prevent you from creating a GPT partition that occupies the space needed by the EBR; however, the user might just use GParted, GPT fdisk, OS X's Disk Utility, or some other tool to edit the partition table, and those programs do not provide such protections, so you could easily get into trouble.

So to sum up, I will not "bring it down a notch." I understand you did not realize how dangerous what you were suggesting was, but I do. I've given the matter a fair amount of thought. I've seen the problems that even run-of-the-mill hybrid MBRs cause, and the thought of hybrid MBRs with extended and logical partitions gives me the screaming heebie-jeebies.

...

I believe that was the sound of me being schooled. :p

Just as a point of clarity, I was not trying to be disrespectful with my comment, as you undoubtedly (and clearly) know much more about all of this boot whatnot than I do. Just want to let you know that I was joking, and I hope I didn't offend.

---

### Post by srs5694 on 2011-02-15
No offense taken. I just want to head off trouble. There's the saying, "a little knowledge is a dangerous thing," and if somebody were to get the idea of hacking a hybrid MBR using fdisk to add extended and logical partitions, the result could get very dangerous very quickly. I just want to nip that idea in the bud.

---

### Post by Tu1J4kXk8NUhMz on 2011-02-19
> **srs5694 said:**
> 
If you mean omitting the OS X partition from the hybrid MBR, please read the pages to which I linked in my earlier message. You just need to create a new hybrid MBR with a more flexible program (such as GPT fdisk or some versions of gptsync, but not the most common versions of gptsync), which let you specify which GPT partitions get included in the hybrid MBR -- and therefore, by implication, which partitions get omitted from it.

I have gone through the first half of the link you provided, and to be quite honest this seems far too technical for me. The last thing I want to do is mess up any boot table and spend the next few days trying to "find my computer." Thanks for the input, but I think I might be better served with a simpler solution...

---

### Post by srs5694 on 2011-02-20
> **teamjh14 said:**
> I have gone through the first half of the link you provided, and to be quite honest this seems far too technical for me. The last thing I want to do is mess up any boot table and spend the next few days trying to "find my computer." Thanks for the input, but I think I might be better served with a simpler solution...

First, if I understand the problem, there is no simpler solution. There is a more complex solution: Back up the computer, create a new partition table with a different ordering of partitions, and restore everything. That's far more work and is far more likely to create problems than is adjusting your hybrid MBR.

Second, the solution is not all that hard. It's just a question of including the partitions you want to access from Windows in the hybrid MBR. The hardest part is learning enough about hybrid MBRs to understand how they work. IMHO, anybody using a hybrid MBR should do that anyhow, since they're trouble-prone. (In practice, few people have this understanding, sadly.)

Third, I can't promise there will be no problems; however, you can always back up your current partition table (using the 'b' option on the gdisk main menu), which will enable you to restore the current partition table if you do run into problems.

---

