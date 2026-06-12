---
title: "Video performance of Ubuntu 16.04 on Mac Mini 2,1 (Intel Integrated 945GM/GMS)"
date: 2017-01-17
forum: Apple Hardware Users
---

### Post by petermacrobert on 2017-01-17
[B]Background
[/B]
I recently installed Ubuntu 16.04 on a Mac Mini 2,1 to give it a new lease on life as a media player. I followed [this excellent guide]("https://ubuntuforums.org/showthread.php?t=2287767") for booting Ubuntu from EFI because my old Mac Mini prevents booting from USB. The guide is focused on 15.04 but works just fine for 16.04 too.

(For what it's worth, I only followed steps 1-5. Instead of installing Ubuntu in step 6, I booted into the "try Ubuntu" mode, and then followed the GUI installer from there, choosing all the default options. The machine booted fine and I never needed to amend the boot loader.)

[B]Problem
[/B]
Soon after installing Ubuntu 16.04 I found the overall performance substandard, with video quality being particularly bad (specifically lagging and tearing during playback). I followed a couple of other guides to enable (and even disable!) vsync, to no avail. 

If you're experiencing tearing, then enabling TearFree mode in X is a **must** ([this guide]("https://community.linuxmint.com/tutorial/view/2304") was helpful). However, as soon as I did, the video playback became really slow, jerky and unpredictable. The tearing was gone but the video playback was unbearable.

[B]Solution
[/B]
I started digging around the system and came across an additional driver which looked interesting:

[ATTACH=CONFIG]273237[/ATTACH]

This screen located at "System Settings" -> "Software & Updates" -> "Additional Drivers".

Researching the intel-microcode package, I stumbled across [this comment ]("http://askubuntu.com/a/812684/643545")which sounded interesting. I disabled the intel-microcode driver, restarted my system, et voila! Video playback is now **flawless** – even HD video. The system feels snappier too: The mouse no longer lags and windows open and close faster. Happy days.

[B]Conclusion
[/B]
[Note: this is my reckon, and is not fact.]

The intel-microcode driver is a tool to automatically update the system BIOS and firmware. Its purpose is to make BIOS updates easier and to roll out hotfixes from Intel and to correct processor behaviour.

However, given that I'm running a Mac which has custom BIOS and firmware loaded, and a ton of differences to a "standard" PC, the driver is probably loading something that's sub-optimal for a Mac hardware configuration, and which is inadvertently causing a slow-down. 

[B]Should you do it too?
[/B]
My Mac Mini 2,1 is old (2007) and it's unlikely there will be any more updates for its BIOS or CPU, so I don't think I'm harming my system by removing the driver. However, if you are running Ubuntu on a more modern Mac then you may wish to keep this driver enabled.

---

