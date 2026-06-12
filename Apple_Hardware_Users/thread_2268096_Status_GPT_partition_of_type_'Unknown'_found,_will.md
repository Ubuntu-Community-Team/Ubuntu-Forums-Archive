---
title: "Status: GPT partition of type 'Unknown' found, will not touch this disk."
date: 2015-03-06
forum: Apple Hardware Users
---

### Post by sam119 on 2015-03-06
Hi All,

I realise this issue has been around for a long time. I've tried the solutions in other forum posts but to no avail.

I'm attempting to create a dual boot MacBook White (2009) running OS X 10.10 (Yosemite) and Ubuntu's latest release. Follows instructions [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) and then proceeded to try the fix as instructed in post #6 of this thread [http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229).

No luck. I still can't get Ubuntu to boot. I've explored other solutions but nothing has worked.

Has anyone found a modern fix or written an updated guide to complete this process? I'm willing to start the whole process again if there are better methods out there than the one listed on Mactel's guide.

Look forward to a nice, updated discussion on this one.

---

### Post by este.el.paz on 2015-03-08
@sam:

I'm too busy to read those links . . . : - )  but I have posted numerous times here on the details of setting up a dual or triple boot system . . . using rEFInd installed via the "rodbooks" web site . . . find-able on source forge.  Some people seem to not use rEFInd on apple computers.  But, briefly, couple questions, did you check the md5sum number of the iso before burning it or making usb flash drive?  And, did you use OSX Disk Utility to create your rough partition, formatted as "free space" or "fat32" before running your install process?  Might not be necessary, but it sometimes makes it easier.  And, did you use "automatic" "install next to" option, OR did you use "manual"??

And, by "latest" ubuntu . . . which one is that?  I'd suggest the 14.04 LTS options . . . Xubuntu seems to install nicely on my '10 MBPro.

And, yes, sometimes a fresh re-install is the easiest solution . . . or try different flavors of linux until you find one that works.

e.e.p.

---

### Post by sam119 on 2015-03-11
> **este.el.paz said:**
> @sam:

I'm too busy to read those links . . . : - )  but I have posted numerous times here on the details of setting up a dual or triple boot system . . . using rEFInd installed via the "rodbooks" web site . . . find-able on source forge.  Some people seem to not use rEFInd on apple computers.  But, briefly, couple questions, did you check the md5sum number of the iso before burning it or making usb flash drive?  And, did you use OSX Disk Utility to create your rough partition, formatted as "free space" or "fat32" before running your install process?  Might not be necessary, but it sometimes makes it easier.  And, did you use "automatic" "install next to" option, OR did you use "manual"??


Hi, thanks for getting back to me :) USB boots fine, it's not an iso issue I don't think. I did create free space prior to install and havetried both the automatic install and the manual partitioning options.

> **este.el.paz said:**
> 

And, by "latest" ubuntu . . . which one is that?  I'd suggest the 14.04 LTS options . . . Xubuntu seems to install nicely on my '10 MBPro.

And, yes, sometimes a fresh re-install is the easiest solution . . . or try different flavors of linux until you find one that works.

e.e.p.

Latest Ubuntu I'm using is 14.04.2.

I've since made more discoveries. Posting below..

---

### Post by sam119 on 2015-03-11
UPDATE:

the guides I was using above are dated. rEFIt, is no longer supported but the guides haven't been updated to show this. Using a fork called rEFInd from [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) I've managed to progress but now encounter a different issue. See this new post for the new issue: [http://ubuntuforums.org/showthread.php?t=2268575](http://ubuntuforums.org/showthread.php?t=2268575)

Am updating here in case anyone else follows a similar path of discovery and gets stuck too.

Thanks :)

---

### Post by este.el.paz on 2015-03-11
Probably the mods would want you to stay with one thread, rather than adding another one . . . it's still amounts to an "install" issue . . . which is one problem.  So, you switched to rEFInd and then ran the install . . . and when you say "black screen" do you mean totally black, or, in the upper left corner there is a flashing boot prompt?  If there is the flashing prompt, then possibly GRUB is not working or installed properly.  Sometimes on some installs I will get a "GRUB has installed properly" but, it actually didn't.  If you select "manual" and use your GParted to set up at least 3 partitions, a small 10 MB partitiion set up labeled as "bios_grub," the "/home" labeled as "/" formatted as "ext4"; the "swap" as 1-2x RAM . . . then run the install.  Afterward, first shut the computer down; then boot and see if the rEFInd window opens showing you the options, many times the "linux" partition shows as "windows" . . . .  But, point being, it seems like in our era MBPro you have to manually set up a GRUB partition for the installer to "know" where to put it.

e...

---

