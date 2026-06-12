---
title: "Error: Can't allocate initial device-tree chunk"
date: 2006-07-23
forum: Apple PPC Users
---

### Post by conner_bw on 2006-07-23
Hi,

I just bought an iMac G3 at a garage sale and I want to install xubuntu 6.06 power pc on it. I've downloaded the ISO, burned it, booted the cd, gotten to the prompt where *live is the default. Shortly therafter I get a gray screen:

```
Can't allocate initial device-tree chunk

Apple iMac Open Firmware 3.0 f2 build on 04/23/99 at 14:31:03
Copyrught 1994-1999 Apple Computer, Inc.
All Rights Reserved
ok
0 >
```

I've tried every option available from pressing tab, including `live video=ofonly` to no avail. The machine has 160 megabytes of ram and is a G3 233 MHZ, 4 gigabyte harddrive classic bubly blue iMac from the late 90's, boots into the included Mac OS 8 with no problems.

Help?

---

### Post by elcuyabro on 2006-07-23
you´re not alone in the world, i have the same problem. it seems the grey screen is the "firmware promt " of the imac, not the installation promp. see [https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC). try typing "boot cd:,\\:tbxi"

> **conner_bw said:**
> Hi,

I just bought an iMac G3 at a garage sale and I want to install xubuntu 6.06 power pc on it. I've downloaded the ISO, burned it, booted the cd, gotten to the prompt where *live is the default. Shortly therafter I get a gray screen:

```
Can't allocate initial device-tree chunk

Apple iMac Open Firmware 3.0 f2 build on 04/23/99 at 14:31:03
Copyrught 1994-1999 Apple Computer, Inc.
All Rights Reserved
ok
0 >
```

I've tried every option available from pressing tab, including `live video=ofonly` to no avail. The machine has 160 megabytes of ram and is a G3 233 MHZ, 4 gigabyte harddrive classic bubly blue iMac from the late 90's, boots into the included Mac OS 8 with no problems.

Help?

---

### Post by conner_bw on 2006-07-23
> **elcuyabro said:**
> you´re not alone in the world, i have the same problem. it seems the grey screen is the "firmware promt " of the imac, not the installation promp. see [https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC). try typing "boot cd:,\\:tbxi"

Hi, thanks for tip but unfortunately it didn't work. The following is a transcription of what happens:

```
0 > boot cd:,\\:tbxi load-size=73f adler32=80dda6b0

parsing <CHRP-BOOT>

evaluating <BOOT-SCRIPT>

DEFAULT CATCH!. code=300 at    %SRR0:  016dd1c    %SRR1:  0000b030
 ok
0 > 
```

Thereafter, nothing.

Any other ides?

---

### Post by conner_bw on 2006-07-24
Help?

](*,)

---

### Post by avtolle on 2006-07-25
is this thread helpful? [http://www.ubuntuforums.org/showthread.php?t=190131](http://www.ubuntuforums.org/showthread.php?t=190131) and here's a bit more information: [https://wiki.ubuntu.com/DapperReleaseNotes/UbiquityKnownIssues](https://wiki.ubuntu.com/DapperReleaseNotes/UbiquityKnownIssues)

---

### Post by conner_bw on 2006-07-25
I read those links, searched for hours, but nothing seems to solve my problem. I have filled a bug report.

[https://launchpad.net/distros/ubuntu/+bug/54098](https://launchpad.net/distros/ubuntu/+bug/54098)

---

### Post by conner_bw on 2006-07-25
I just tried with Ububntu 6.06 Server powerpc, I got the exact same error.

---

### Post by gizmo90 on 2006-07-26
Similar hardware. Same error here as well. :confused:

---

### Post by Aorbus on 2006-07-30
Hi all! (1st post!)

Same problem. I have a clamshell iBook 300mhz with 288mb ram. It has 5.10 installed, but won't auto-upgrade for some reason :(

I've burnt both the 6.06 'desktop' and 'alternate' ISOs so now have two new coasters ;)

Being a n00b to linux, I was well impressed when I heard I may be able to have hardware accelerated graphics again... Something Mac OS X has left me feeling a bit miffed since upgrading from System 9. Seeing what 4mb of VRAM can do is better than nothing!

Is there an official thread about this. Like the others here, I've found loads of separate threads about pre-release problems all mixed up with current installer difficulties.

Ro :)

---

### Post by namaui on 2006-07-30
I am also having this paicular problem. I am on an iMac G3 Rev D. 333 mhz with 160 mb ram an i have tried the xubuntu 6.06 desktop release and the xubuntu 6.06 alternate with no help either. I think this may be some sort of hardware limitation that resides in the kernel, similar to how this paticular model (tray loads) cant run anything higher than 10.3.9. it is very strange indeed.

---

### Post by Aorbus on 2006-07-31
Hi folks,

I thought I was being clever last night and sorted out the update manager difficulties I had. I left the machine downloading overnight and accepted all the suggested options this morning for 6.06 to finish its install. I crossed my fingers and restarted...

Held down option on reboot and chose my Linux partition, then let it do its default startup. It went straight back onto the blue startup disk selection screen again! Just the same as holding down option on startup but with distorted icons... :(

Remembering what I had read, tried again and typed 'old' at the Yaboot prompt. This gets Dapper running but with loads of problems... like the keyboard not working properly. I can't even get the update manager to open now. :(  As I read through the "read before you install" docs, followed an auto-update and didn't see a 'specific' PPC warning, I'm a bit concerned why not. I'm new to Linux/Ubuntu and this isn't a good start! ;) How are linux n00bs (like me) meant to decide/trust what to do when "an upgrade is available" flashes up on their screen?!

Sorry to rant on my first posts, but why isn't there a "sticky" in the PPC/Mac section about this? Why wasn't there a PPC/G3 warning on the upgrade page? There are quite a few separate threads with the same problem from the last few weeks, so what's the official recommendation?

Ro :confused:

---

### Post by conner_bw on 2006-08-10
Before I download 700 MB and make another coaster, does the release of [6.06.1 LTS](http://www.ubuntuforums.org/showthread.php?t=233444) solve this problem? For anyone?

---

### Post by waldick on 2006-08-10
what is really odd is that i used the same disk to install 6.06 on 3 G3 clamshells, 2 loaded up just fine, the last gave me the error described above, so i had to install 5.10....too bad too since it was the machine for my daughter who i was trying to convince of the vast superiority of 6.06 over os 9.2... :(

---

### Post by GREGMACKENZIE on 2006-08-11
Hi,

I have a tray loading iMac G3 333 mhz 288mb of ram and I took a run at the release of 6.06.1 LTS but it did not work for me. The consensus seems to be that the "graphical" installer does not work  however I got the same error you folks did which is related to the kernal I believe. Some have tried the alternate version of the CD without the graphic installer. From the reading I've done here its hard to gauge the result. Note that the Ubuntu Desktop Guide PDF does not mention the G3s at all, the G4 is the last processor mentioned in the document. I feel left out snif snif...](*,) 

:D However, Ubuntu 5.0.6 Hoary does install without a hitch, and that's what I'm using on my Tray Loader.

Greg

---

### Post by waldick on 2006-08-11
i tried both live/alt on the clamshell and neither would work...of the three, the ones that gave me no problem were a 366 mhz, 192meg and a 466 mhz, 312 meg, but a 300 mhz, 312 meg, gave me the above error ....wonder if it has something to do with processor speed, as that seems to be the only difference, or possibly the firmware ??

i wonder has anyone with a g3 equal to or greater than 300mhz had any problems with 6.06 live or alt ?

---

### Post by GREGMACKENZIE on 2006-08-11
> **waldick said:**
> i tried both live/alt on the clamshell and neither would work...of the three, the ones that gave me no problem were a 366 mhz, 192meg and a 466 mhz, 312 meg, but a 300 mhz, 312 meg, gave me the above error ....wonder if it has something to do with processor speed, as that seems to be the only difference, or possibly the firmware ??

i wonder has anyone with a g3 equal to or greater than 300mhz had any problems with 6.06 live or alt ?

Yeah, mine is a 333 with the rage pro video. I get the following message when booting up with the live installation CD

“Cant Allocate Initial Device Tree Chunk
Apple imac open firmware 3.0.f2 built on 04/23/99 at 14:31.03
copyright 1994-1999 Apple Computer Inc
All rights reserved
ok
0 > _”

I've been in the same boat as everyone else. I ordered the live CD via shipit thinking it would install ok, but that isn't the case. ](*,)  I don't know enough about the apple side of things to say if its firmware or not. All I know for sure is that this machine, which I got used, was running OS X before I ditched it for Ubuntu. To run that your supposed to have the latest firmware upgrades installed.

It might be worth looking into the apple open firmware as a potential issue. Maybe everyone could submit what their's say and we'll start to build a picture of what version works. 

(By the way, I know when I used the apple initialization script for my modem it seemed to work a whole lot better. So maybe its an apple issue with ubuntu)

One person here recommended trying following the upgrade path from hoary, to breezy, to dapper. I haven't bothered myself as I don't have breezy. Frankly, Hoary does what I want it to do, I've an open source OS with all the features I'm looking for. I've upgraded a few packages through synaptic but I'm ignoring the upgrade issue for the moment, particularly as it looks like even if you want to run Breezy, you have to jump through hoops with regard to the xorg thing.

I don't know what else to say really. I'd welcome any thoughts on this.

Greg

---

### Post by GREGMACKENZIE on 2006-08-11
I found this:

"You can boot into open firmware by holding the command _option _o _f _keys at startup. If it showsBuild date April 23, 1999 then you have the Firmware 1.2 which is latest version currently available from APPLE."

:-k

---

### Post by bodycoach2 on 2006-08-12
I've tried to install Ubuntu or Xubuntu 6.06 on a Strawberry iMac G3, 333 Mhz. I get the same 'device-tree chunk' error message. Tried all the work-arounds on this and other threads; no go. 

5.10 installs, but boots ONLY if connected to the ethernet. If not, it hangs just after login, and won't boot to the desktop. 

I'd really like to get Xubuntu working on this old iMac. Has anyone tried nUbuntu? 

Hopefully, this will be fixed in the future. I thought one of the benefits of Linux is being able to run on old equipment. Maybe Edgy Eft will work.

---

### Post by 3rdalbum on 2006-08-12
I have no idea what causes the problems. Some people with the iMac 333 can't boot the discs. I tried my ShipIt discs in my iMac 333 and it works. My iMac runs OS 9... I'm wondering whether that might be the deciding factor, whether OS X makes some kind of secret change to the firmware or NVRAM.

It's definately not anything in Linux or Ubuntu that says "You don't have a G4, so you can't run it". There are people actually running Dapper on Oldworld machines (G2s).

The Linux kernel during the earlier stages of Dapper development couldn't boot an Oldworld - maybe a smiliar thing is happening with some of the iMacs.

---

### Post by bodycoach2 on 2006-08-12
Device-Tree Chunk problem no more:
I downloaded Xubuntu 6.06.1.
It loaded right up! Installed completely, and will run without ethernet connection (not ever Breezy would do that for me).
It even recognizes my Belkin 54G USB Wireless adapter, but has yet to connect. I'm counting my blessing though. Wired is good enough for this little toy.

That for the fix Ubuntu dev teams.

> **bodycoach2 said:**
> I've tried to install Ubuntu or Xubuntu 6.06 on a Strawberry iMac G3, 333 Mhz. I get the same 'device-tree chunk' error message. Tried all the work-arounds on this and other threads; no go. 

5.10 installs, but boots ONLY if connected to the ethernet. If not, it hangs just after login, and won't boot to the desktop. 

I'd really like to get Xubuntu working on this old iMac. Has anyone tried nUbuntu? 

Hopefully, this will be fixed in the future. I thought one of the benefits of Linux is being able to run on old equipment. Maybe Edgy Eft will work.

---

### Post by avtolle on 2006-08-12
This seems to substantiate the "kernel on the <original> CD is the problem" hypothesis forwarded by several on the Forum, at least in the case of bodycoach2. From my reading of the various threads, for those having the "can't allocate initial device-tree chunk" problem, it would seem to be worth your while to obtain a download of the 6.06.1 iso, preferably the "alternate install" one; or, download the Xubuntu iso; and try to install these. Remember, those who are on "Old World" Macs, you will need to use Boot-X in a Mac OS partition, copying the kernel (and something else, which escapes me at the moment) into the appropriate file; and boot from there. This is a Linux issue on PPC for Old World Macs. Best of luck to all who are trying to install on their G3s, in particular, and Macs of any stripe, in general.

---

### Post by conner_bw on 2006-08-14
Three stalled installs, sometimes the system rebooting on it's own for seemingly no reason, I had to type "oem" for everything to get going. It's later than I'd like and I have to crash without running exhaustive tests such as seeing the install through but this reply is to confirm that **"xubuntu-6.06.1-alternate-powerpc.iso" installed on my iMac.**

Thanks.

---

### Post by GREGMACKENZIE on 2006-08-14
:D  Well that is good news! Now, any idea when they'll make this available via shipit? Downloading this on dialup is not an option.

Greg
:-)


> **bodycoach2 said:**
> Device-Tree Chunk problem no more:
I downloaded Xubuntu 6.06.1.
It loaded right up! Installed completely, and will run without ethernet connection (not ever Breezy would do that for me).
It even recognizes my Belkin 54G USB Wireless adapter, but has yet to connect. I'm counting my blessing though. Wired is good enough for this little toy.

That for the fix Ubuntu dev teams.

---

### Post by conner_bw on 2006-08-15
This is my final follow-up from me in this thread. I now have a working version of Xubuntu on my bubbly blue iMac 233mhz. 

The installing was painful and haphazard. The system would freeze randomly, this happened half a dozen times, oem did not work, the default (finally) did. 

On my final install, like some sort of superstitious voodoo man, I pressed the escape key every few minutes thinking that it would prevent the system from "falling asleep" during the install process. At the end of the day, coupled with knocking on wood and throwing salt over my shoulder, that's what worked.

Thanks.

---

### Post by wally the duck on 2006-09-24
I had the "can't allocate initial device-tree chunk" white screen when I tried to load 6.06 (alt disk) an my imac 233 rev A (bondi).
I downloaded then 6.06.1 (alt disk), wrote from the iso and it loaded and works perfectly.

---

### Post by Childe on 2006-09-25
It looks like they've addressed the problem in the previously-mentioned bug report:

[https://launchpad.net/distros/ubuntu/+bug/54098](https://launchpad.net/distros/ubuntu/+bug/54098)

You'll need a new Alternate Install CD, it seems.

---

