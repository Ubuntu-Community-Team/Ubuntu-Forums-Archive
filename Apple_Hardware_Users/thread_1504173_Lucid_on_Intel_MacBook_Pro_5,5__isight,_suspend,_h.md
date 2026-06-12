---
title: "Lucid on Intel MacBook Pro 5,5:  isight, suspend, hibernate missing after restart"
date: 2010-06-07
forum: Apple Hardware Users
---

### Post by djsutton on 2010-06-07
About 50% of the time when I reboot my MacBook Pro 5,5,  the Suspend and Hibernate options are missing in the Shut Down menu, and Ubuntu cannot find the  iSight camera (gstreamer-properties gives 'Video for Linux 2 (v4l2): Could not negotiate format' when I test video input).  When this occurs, I can resolve it by rebooting until suspend and hibernate show up in the power menu on the login screen.

As far as I can tell, I have all packages and mods indicated by [https://help.ubuntu.com/community/MacBookPro5-5/Lucid]("https://help.ubuntu.com/community/MacBookPro5-5/Lucid").  Please let me know if you have this problem, or what other logs or tests would be helpful in figuring this out. I'm not an expert on systems, but I suspect this might be related to firmware/HAL since all the symptoms are lost hardware functionality.

This has been happening to me since before the upgrade to lucid.  I search for an answer whenever it happens, but Ive never found anything for these symptoms.  Now I'm posting to see if anybody is having the same issue or knows whats going on here.

---

### Post by Bachstelze on 2010-06-08
Is your kernel up-to-date? I had the same symptoms (power-related functionality absent) after I upgraded my kernel from 2.6.32-21 to 2.6.32-22, this was fixed a few hours later by a new revision of the 2.6.32-22 kernel (2.6.32-22.36 to be precise).

---

### Post by djsutton on 2010-06-08
I am running 2.6.32-22.36 now and still have this problem.  IIRC, this has been happening  since at least 2.6.31-19 in Karmic, possibly earlier. (I was using 2.6.31-19 for a while since [Bug #535361]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/535361") broke my sound in 2.6.31-20)

---

### Post by milli on 2010-06-10
First off, I have a Macbook Pro "17, model MacBookPro5,2 with latest firmware.

I'm in the same boat as djsutton, it started intermittently doing this since around 2.6.19 kernel for me as well.  About all I've had the time to narrow down is something gets horked with the ACPI tables *sometimes* when BIOS mode is initiated, and when that happens, some key structures are not recognized including power-related functions and the iSight camera.  But there's absolutely no rhyme or reason to it.  I just reboot until it works, which sometimes can be 3 or 4 times.  There's also some strange problem with the iSight camera too coming up with two different supported mode strings, but I have a hacked kernel module (uvcvideo) to recognize the bad one too.

Suspend works fine, it always comes back okay on the ACPI front (no surprise), there are just other issues that cause a crash every once in a blue moon, or the ethernet hardware to lock up.

Hibernate is problematic.  Because of this problem, I can only effectively Hibernate once.  Pretty much every time I resume with 2.6.26-22-generic kernel the ACPI connections are horked and power functions and iSight camera are broken.  So the situation feels like it's getting worse.

Tried to get an EFI boot loader to work as a hopeful workaround, but I have been completely unsuccessful getting any of the EFI boot loaders to work at all, I get black screens.  Was hoping that would be an answer.

At this point, I think just some of the MacBookPro5,X hardware versions are flakey and just don't work well since some people with the same model as others don't have any problems at all.

Perhaps this is an Apple firmware problem at the core, it certainly points to that since there doesn't seem to be consistency in the BIOS mode initiation.

FWIW anyway.  Hate these kinds of intermittent problems. :-(

---

### Post by tenuki on 2010-06-11
Hi,

I think this is actually two problems: one bug with suspend, hibernate and one with camera. The first was solved for me using the solution posted by ace55 on this thread:

[HTML]http://ubuntuforums.org/showthread.php?t=1469819[/HTML]

The isight problems I'm having appear to be caused by this bug:

[HTML]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544469[/HTML]

(which itself looks to be 2 bugs!). Still no solution to this that I've found.

Hope that helps.

BTW: I'm on Macbook pro 5,4 ubuntu 10.04 amd64

---

### Post by tenuki on 2010-06-11
Doh! Meant to give links, not html!

[Powermanagment fix]("http://ubuntuforums.org/showpost.php?p=9318370&postcount=18")
[Bug #544469]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544469")

---

