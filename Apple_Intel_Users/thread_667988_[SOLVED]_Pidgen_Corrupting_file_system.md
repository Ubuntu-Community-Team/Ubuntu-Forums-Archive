---
title: "[SOLVED] Pidgen Corrupting file system?"
date: 2008-01-14
forum: Apple Intel Users
---

### Post by petersrin on 2008-01-14
I have successfully installed Ubuntu twice on my MacBook Pro, for the most part. However, the first time, when I started Pidgen messenger, my hard drive began making odd sounds, and things slowed down, etc. I then started up the mac os, and the sound continued, but then the system was sluggish, and finally CRASH! So, I boot the system up on mac cd, use terminal to extract the Mac files to an external, format the disk by writing 0's on it, partition to 3 sections: mac os (the big one), Linux (6.5GB) and Linux Swap (1GB), reinstall OS X and Linux, bada-bing-bada-boom it works. Replace my information on the mac partition, and boot into my Ubuntu, update ubuntu, blah blah blah...

Finally, after using it for a bit, I try to chat, not thinking the sound had anything to do with the chat program. Suddenly, that sound, and a minor system hang!!! Woah. I start back up in OS cd, run the drive check from disk utility. Everything checks out. So far... Naturally, I won't be using the Pidgen chat, if the symptoms persist, I'll come back on here. In the mean time, any ideas as to what it might be doing, and perhaps how to prevent it? If so, good. If not, darn.

---

### Post by petersrin on 2008-01-14
To clarify: "CRASH!!!" = Complete unresponsiveness, mounting drive is hit and miss, drive registers as 0 files in CD run disk util, etc. The only thing that read it was Terminal. Not enough to even boot into the UNIX kernel before the mac, had to boot from CD.

And the sound is persisting. With one run of Pidgen. So was the unresponsiveness. Going to try to unistall linux, see if that helps for now :(

---

### Post by ryanVickers on 2008-01-14
I would say just don't use pidgin, but that makes no sense!  There's n_***o way***_ it should corrupt the filesystem!!!!

If it is a plausible bug though, it's of the highest priority and should obviously be looked at ...

one question - why not use iChat? ;)

---

### Post by petersrin on 2008-01-14
Well, I was loaded into Ubuntu, and wanted to chat. The first time I used it I didn't associate the problem directly with Pidgen. By the way, I had to erase the entire drive again. I tried just getting rid of the Linux partitions, but that was a no go after zeroing both partitions out. Still the sound, the hang. I still think it could easily be a HW problem. I'm going to go through the same steps tomorrow, see if Pigeon makes it kill again. Any suggestions about getting useful information if it does kill, so I can report the bug? (This time, I'll wait a long time while using Ubuntu, to see if the hardware'll just crap out on it's own. If it's hardware, I'll replace the drive (duh). If it's Pidgen, I want to report it. I'm quite new to Linux, I've been dabbling in Python and Unix with the mac. Anyway, let me know how to report it so I can if it happens tomorrow.

---

### Post by ryanVickers on 2008-01-14
if you run it in the terminal, it will output any errors, but a hard drive issue may not show up anywhere except experiences like this, and diagnostic tools...

---

### Post by petersrin on 2008-01-14
I'm pretty sure it has to do with Pidgen, thinking back on my experience. I was using the new install of OSX for a decent amount of time, with a LOT of usage, restoring my files, doing stuff, before the Linux install. It MAY be the Linux install, but hearing it each time ONLY after Pidgen gives me worries. Goodbye till tomorrow, and then, we'll see what's going on!

---

### Post by cyberdork33 on 2008-01-15
I say hard drive is going.... at least it sounds like many a hard drive death I have experienced.

If you are getting noises, that is likely a hardware issue. There is not really a way that pidgin could do what you are saying... writing the many files to the disk may have sped the problem along, but I couldn't say that it was any software's fault.

---

### Post by 3rdalbum on 2008-01-15
It would have to be a hardware problem, as there is nothing Pidgin can do that would cause crashes in both Mac OS X and Ubuntu. It's probably some sort of imperfection in the manufacture of your hard disk, or possibly some sand or grit has somehow entered your HDD.

You can always install Kopete onto Ubuntu. Kopete is a very capable messager, probably better than Pidgin.

---

### Post by petersrin on 2008-01-15
I was in disbelief myself - how could a messaging program cause a drive-wide failure. I did some googling this morning, and found information about hard drive manufacturer  "aggressive power saving" features which seem to be problematic for most OSs...

The sound I was hearing yesterday reminded me of a fast spin-up, then a cut-off, then another fast spin-up, etc. I uninstalled ALL OSs and I still hear the sound. This means hardware failure. I suppose somehow Ubuntu just expedited an impending failure? Fortunately I have my stuff backed up from the first crash.

When I replace my drive, will it be safe to install Ubuntu? I don't want to replace it again. Also, if it is "safe" then should I apply the modifications others have done for hard drive spin-up spin-down times?

---

### Post by cyberdork33 on 2008-01-15
> **petersrin said:**
> I was in disbelief myself - how could a messaging program cause a drive-wide failure. I did some googling this morning, and found information about hard drive manufacturer  "aggressive power saving" features which seem to be problematic for most OSs...

The sound I was hearing yesterday reminded me of a fast spin-up, then a cut-off, then another fast spin-up, etc. I uninstalled ALL OSs and I still hear the sound. This means hardware failure. I suppose somehow Ubuntu just expedited an impending failure? Fortunately I have my stuff backed up from the first crash.

When I replace my drive, will it be safe to install Ubuntu? I don't want to replace it again. Also, if it is "safe" then should I apply the modifications others have done for hard drive spin-up spin-down times?
As far as I know, aggresive power saving for hard drives is disabled in Ubuntu for this very reason. We had a discussion about this in another thread starting here: [http://ubuntuforums.org/showthread.php?t=590867&&page=4#33](http://ubuntuforums.org/showthread.php?t=590867&&page=4#33)
jdong (an admin) weighed in on the subject on this post:
[http://ubuntuforums.org/showpost.php?p=3834094&postcount=42](http://ubuntuforums.org/showpost.php?p=3834094&postcount=42)

---

### Post by petersrin on 2008-01-15
Just to finish up this thread, I am letting you all know that I'm apparently experiencing the negligence of Apple. Ever since the MacBook Pro came out, since they moved to intel, they've had problems with heat management, batteries, and one I didn't know about: hard drives. Apparently their Seagate batch has very large problems, and fail frequently. My failure seems to fit a common time line for the failure of this drive in other people's systems. Really sucks. I'm to replace it. Linux, naturally, is not at fault.

---

### Post by cyberdork33 on 2008-01-15
> **petersrin said:**
> Just to finish up this thread, I am letting you all know that I'm apparently experiencing the negligence of Apple. Ever since the MacBook Pro came out, since they moved to intel, they've had problems with heat management, batteries, and one I didn't know about: hard drives. Apparently their Seagate batch has very large problems, and fail frequently. My failure seems to fit a common time line for the failure of this drive in other people's systems. Really sucks. I'm to replace it. Linux, naturally, is not at fault.
Mark as Solved!

---

