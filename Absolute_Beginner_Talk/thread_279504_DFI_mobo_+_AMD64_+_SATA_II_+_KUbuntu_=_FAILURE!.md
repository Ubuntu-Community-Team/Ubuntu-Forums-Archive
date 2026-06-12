---
title: "DFI mobo + AMD64 + SATA II + K/Ubuntu = FAILURE!"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by sister_clamp on 2006-10-18
Hi guys--

Hope this will help someone. We originally had an issue but it seems to have resolved itself which, believe it or not, is **Not A Good Sign** when you can't definitively find root cause (read on for elucidation). We have a really nice new machine at home:

DFI LanParty UT4 SLi-D
AMD64 Socket 939 3200+ cpu
80GB SATA II HDD (sda)
320GB SATA II HDD (sdb)
1GB RAM

<<After 4 previous attempts of trying to install K/Ubuntu as a standalone o/s on our 320GB with no success...we bought a 80GB SATA II (*SATA size limitations?*)...>>

We sliced the bigger SATA drive into 3 roughly 100GB partitions. We installed Windows 2000 on the 80GB and want to install K/Ubuntu on one of the 100GB partitions. Just fyi, I have also previously installed Kubuntu 6.06 on my Compaq laptop & Dell dual-core desktop with little problem.

Attempt #1. Install Kubuntu AMD64 6.06. Falls over after trying to install a Python package. Screen freezes.

Attempt #2. Install Ubuntu AMD64 6.06. Falls over at same point after trying to install a Python package. Screen freezes.

<<Read that there is an issue with the 6.06 AMD version. Best workaround was to install 5.10 then hack part of the upgrade to 6.06. Soooooo....>>

Attempt #3. Install Ubuntu AMD64 5.10. Falls over with "Kernel panic ... Aiee, killing interrupt handler" error after screens of errors when trying to set up hotplug system. Screen freezes.

<<Read that there may be some geometry settings in the BIOS that affect dual-boot systems. Change HDD geometry from "Auto" to "Large"....>>

Attempt #4. Install Ubuntu AMD64 5.10. Falls over with "Kernel panic ... Aiee, killing interrupt handler" error after screens of errors when trying to set up hotplug system. Screen freezes.

<<Change HDD geometry back to "Auto" (quicker anyway)...Read that some people got around their problem by disabling APIC. Sooooooo....>>

Attempt #5. Install Ubuntu AMD64 5.10 with noapic & nolapic option. Falls over with "Kernel panic ... Aiee, killing interrupt handler" after screens of errors when trying to set up hotplug system. Screen freezes.

Attempt #6. Install Kubuntu i386 6.06 . Freezes during manual partitioning task after I "Prepare mount points".

Attempt #7. Reinstall Kubuntu i386 6.06 by hitting "Reboot" button on machine. Freezes during detecting filesystems. (I'll leave it as an exercise to the reader as to what was uttered at this point.)

Attempt #8. Reinstall Kubuntu i386 6.06 by hitting "Reboot" button on machine. (See above but doubly so) F*** me sideways but the ***t INSTALLS!!!!!!!!

Can't help thinking of bulldog's earlier post from today on pminmo's thread: "You should be aware the fault is not Linux but the user who try's [sic] to learn it." Yeah right! Sooooooo helpful.

FILESYSTEM: I prefer ext2 but I've been reading that the Ubuntu default is ext3. Installed with ext2 (set this up prior to Linux installation using Partition Manager via Windows 2000). No problem.

Read that some people had to disconnect their original HDD to install Linux on their second HDD. I didn't have to do that on my Dell desktop where I now have 3 o/s on 3 separate HDDs, having installed Kubuntu on the 3rd HDD (all IDE). Have now done this (2 o/s) on our DFI with 2 SATAs. It **is** possible but I don't know exactly why. *Are there some quirks to using SATA II? *

Now we just have to try to upgrade from i386 to 64-bit. (*WHY did the 64-bit version (6.06 AND 5.10) not work???*) Another new adventure....wish me luck! If anyone has insights into my questions, please feel free to post. Let's see if we can help each other without hurling rants or zero-value statements around.

S_C

---

### Post by ReaderRat on 2006-10-18
I have two 320G SATA drives, and I had to set them to be used as IDE drives (in the BIOS) before they would work. I was going to use them as a RAID array, but it was too complicated (for me). I have heard of problems if you have one SATA and one PATA drive. That's about all I got...

---

### Post by ske1fr on 2006-10-18
You mentioned noapic nolapic in the boot string in one of your attempts - I found with my motherboard that although it has ACPI it helped during installation for that string to include acpi=off .  Once I did that all the flaky freezing during installation stopped.

---

### Post by xpod on 2006-10-18
> Read that some people had to disconnect their original HDD to install Linux on their second HDD. I didn't have to do that on my Dell desktop where I now have 3 o/s on 3 separate HDDs, having installed Kubuntu on the 3rd HDD (all IDE). Have now done this (2 o/s) on our DFI with 2 SATAs. It is possible but I don't know exactly why. Are there some quirks to using SATA II?

Now we just have to try to upgrade from i386 to 64-bit. (WHY did the 64-bit version (6.06 AND 5.10) not work???) Another new adventure....wish me luck! If anyone has insights into my questions, please feel free to post. Let's see if we can help each other without hurling rants or zero-value statements around.


I dont think its so much "had to" with people disconnecting an hd.More a case of it mabey being a safer option if people want to avoid possible hassles with where grub gets written to.
The "64 bit" thing is one of the first things i noticed when checking all the pre-install advice out there and was the reason i went for the x86.Theres loads of advice out there advising against us novices going near it....Unless we want trouble.
Unfortunately i still have trouble helping myself but can tell you that everyday is a new adventure and you`ll soon start enjoying im sure...

The hassles are surely part of the fun and you never learn the right way "properly" unless you do it the wrong way a few times first i reckon..

Have fun pal

---

