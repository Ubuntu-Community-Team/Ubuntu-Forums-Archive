---
title: "Bug? External data devices not reading and disconnecting"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by twrock on 2007-11-03
On a fresh install of Gusty on a Dell 700m laptop. With both the internal SD card reader and my Nokia phone connected in "data" mode via USB cable, the device is disconnected when attempting any read of a folder with more than a few files in it. Error message pops up warning me about unsafe removal.

Is this happening to anyone else? I did not have the problem in Feisty.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes.
Bug.
The Main Link: [highlight]ABOVE[/highlight]

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The link you might want to comment on: [highlight]^^^[/highlight]

---

### Post by twrock on 2007-11-03
Thanks. I just noticed the same behavior on my desktop machine. Obviously a bug. I'll have a look at those links.
Thanks again.

---

### Post by twrock on 2007-11-03
Hmm, after looking through those bug reports, I'm not experiencing the same problems. Certainly they could be related, but 1) I'm not doing anything with gparted and 2) all the devices are automounting just fine. The problem is that they are "auto-disconnecting" when I try to click into a sub-folder. I'll work on following more links to see if I can find something that more closely matches my problem.

---

### Post by twrock on 2007-11-03
And might there be some relation to this thread? [http://ubuntuforums.org/showthread.php?t=403725](http://ubuntuforums.org/showthread.php?t=403725)
I had forgotten about that one (in which I had even commented), but probably because the symptoms are different. I wondered in that thread if the problem wasn't somehow related to "Automatix read/write NTFS and Fat32 Mounter". I eventually did a reinstall of Feisty and did not use Automatix ever again. The problem never came back. (Not that that proves it was related to Automatix or the NTFS and Fat 32 Mounter.) Did I read somewhere that Gusty has NTFS support enabled by default? Is this the first version that did that? Might that be part of the problem? Anyway, I'm slowly reaching the conclusion that Gusty is not the most stable Ubuntu version to date. :)

---

### Post by suchawato on 2007-11-03
Yes, Gutsy has NTSF support enabled by default.

---

### Post by suchawato on 2007-11-03
Yes it probably IS related to these bugs.
The gparted page is the technical page regarding the cause of these issues,
however it manifests as general mounting problems for external drives.
As far as I know this is a configuration code problem in Gutsy and is being worked on.
Those who are having problems on the other page you linked too are the same problem I have had and others. Hopefully they will fix it soon, as mounting problems are not only annoying, but prevent basic functionality. One of the issues I had was an external hard drive that WAS working fine, suddenly was being told to me that it was "read only" and I couldn't use it.
People have been having all sorts of problems with this issue.
Some laptop users lost complete USB use at all after installing Gutsy. This problem isn't causing just one symptom, its causing many depending on the system.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/159711](https://bugs.launchpad.net/ubuntu/+bug/159711) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Weeel, I stick my foot in my mouth,
Maybe not.
I just got an email saying taht the problems I have been having may be a different bug than these ones beforementioned.
So... 
Maybe not.
Back to square one.
I reported it so you can check the link and see if it relates to you or not.

---

### Post by twrock on 2007-11-12
So over the weekend, I decided to give it a test. I reverted to Feisty (fresh install of course). With both the x.15 and x.16 kernel, the problem is the same. So without my noticing it, something changed even for Feisty. This is not just a Gusty issue.

(However, I haven't had a Firefox crash in the last 36 hours, so maybe my frequent FF crashes in Gusty is a problem with that version. Also, for some strange reason, Feisty boots faster than Gusty. Am I mistaken that Gusty was supposed to be more optimized for boot speed? In any case, I might wait until some of these issues get worked out before I "upgrade" to Gusty again.)

---

### Post by road2elysium on 2007-11-29
> **twrock said:**
> On a fresh install of Gusty on a Dell 700m laptop. With both the internal SD card reader and my Nokia phone connected in "data" mode via USB cable, the device is disconnected when attempting any read of a folder with more than a few files in it. Error message pops up warning me about unsafe removal.

Is this happening to anyone else? I did not have the problem in Feisty.

Gutsy on Dell i700m notebook with the exact same problem with the internal SD card reader.

Here's some logs:
```
Nov 29 17:24:27 i700m kernel: [ 1380.176000] tifm_core: MMC/SD card detected in socket 0:0
Nov 29 17:24:28 i700m kernel: [ 1380.292000] mmcblk0: mmc0:9ffc SD01G 992000KiB 
Nov 29 17:24:29 i700m kernel: [ 1381.716000] tifm0 : demand removing card from socket 0:0
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 48
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 56
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 64
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 72
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 80
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 88
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 96
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 104
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 112
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 120
Nov 29 17:24:29 i700m kernel: [ 1381.716000] end_request: I/O error, dev mmcblk0, sector 128
Nov 29 17:24:29 i700m kernel: [ 1381.760000] tifm_core: MMC/SD card detected in socket 0:0
Nov 29 17:24:29 i700m kernel: [ 1381.876000] mmcblk0: mmc0:9ffc SD01G 992000KiB 
Nov 29 17:24:29 i700m kernel: [ 1381.876000]  mmcblk0: p1
```

---

