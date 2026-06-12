---
title: "[SOLVED] Mac Pro?"
date: 2006-08-11
forum: Apple Intel Users
---

### Post by brenth on 2006-08-11
Has anyone gotten a Mac Pro yet and installed any form of linux on it? So far the install how-tos for MBPs aren't working.
Brent

---

### Post by stmiller on 2006-08-11
The dual-core powermacs (not dual CPU; dual core) just recently got support in the Linux kernel. This past year. They didn't work before that.
So it will take probably a few months for Linux to run out-of-the-box on this new Mac Pro. Unless you are a kernel hacker...

---

### Post by n00bWillingToLearn on 2006-08-12
I really have no expertise in this at all but have you tried the 64 bit version of Ubuntu? Does the liveCD boot OK? Also be VERY sure that you have thermal management. If you don't have the fans and temperature sensors working then you may just melt your nice new Mac Pro. I would love to hear more about how this goes as I will probably never be able to afford a mac pro. Keep us posted :)

---

### Post by Jeroen Vernooij on 2006-08-12
>"So far the install how-tos for MBPs aren't working." 
Where do you get stuck?
Since the Mac Pro's are just x86 Xeons (Quad :cool: ) it should just install like on a non-Mac system. Just make sure you can boot off the CD-ROM.

---

### Post by brenth on 2006-08-13
Hey all, thanks for the responses. So far I have tried a few different distros, and seem to get the similar issues on all. I am trying to boot from the liveCD and it gets to the boot screen, I hit enter, and it starts to boot, but then I get alot of errors and a kernel panic.

It stops at: " Looking for CD-ROM at /newroot/dev/hda..."

and then waits a bit, then gives a bunch of these errors;
" hda: cd-rom_PC_intr: The drive appears confused (ireason = 0x01)"

then a bunch more errors ( can type them out if necessary), then;
" Kernal panic - not syncing: Attempted to kill init~"

As I say, I get similar issues from other distros ( fedora 5 for example).  

Thanks for any help everyone. I gotta say, this is one fast box:), OSX boots in like 3 seconds flat, it's unreal!

Thanks,
Brent

btw, I am xposting this to the mactel-linux-users list, sorry for the duplicate if your on that list :)

---

### Post by simmons on 2006-08-16
Brent,

As far as I can tell from Googling around, you may be the first person to attempt to install Linux on a Mac Pro!  Please post back with news if you have any further success or failure with this endeavor.  The Mac Pro sounds like an incredible machine, even for its price tag, and I'd almost be tempted to pick one up if I could run Linux on it.  (My work requires Linux.)

It sounds like Linux is having trouble with the IDE hardware (or possibly the CD-ROM).  The tasks that occur before your problem (loading the boot menu and loading the kernel into memory) are no doubt performed using the machine's firmware for accessing the CD-ROM.  The first time Linux tries to access the CD-ROM on its own, it fails.  This will probably be solved eventually by some kernel hacker writing a driver for whatever special IDE hardware exists in the Mac Pro.

David

---

### Post by 3rdalbum on 2006-08-16
One tack you might want to try is installing Linux onto a flash drive, assuming the Mac Pros can start up from USB. That would hopefully bypass the SATA/DVD-drive issues.

Or you could possibly try passing one of the following as kernel arguments:

atapicd
pnpbios=off
acpi=off

Yeah I'm just reading off a Knoppix cheat sheet ;-)

---

### Post by madgamer on 2006-08-17
brenth: You are not alone.  I got my Mac Pro yesterday and have not been able to install Linux on it.  I tried Gentoo, Ubuntu and even Knoppix.  The Live CD loads but it doesnt get past the part where it searches for the CD-ROM drive to load from.

I do have some ideas though.  I'm going to try to install from a USB drive.  I am fairly sure that the Mac Pro can boot from USB although I'm not 100% sure.  Can anyone confirm or deny this?  I will go ahead and try anyway.  Sadly, I only have a 128MB USB drive but thats where [DSL]("http://damnsmalllinux.org") comes to the rescue ;)

I will let you guys know how my experiment works out.  Wish me luck!

=======
EDIT:
Well I created a LiveUSB of DSL but I can't figure out how to actually boot from it.  I tried holding Option/Alt and also holding CMD-OPT-SHIFT-DEL but it didn't work.  One other way around this could be to connect remotely to the system and try to install that way but I'm not sure how well that will work.

This really sucks, because Linux is my main OS of choice!  Although I love Mac OS X, I prefer doing my programming projects in Linux.  I will see if I can figure this out..

---

### Post by hazelb030 on 2006-08-22
Have you tried to install ubuntu with the new version of BootCamp (make a XP Partition and then boot from cd ?)

---

### Post by madgamer on 2006-08-22
> **hazelb030 said:**
> Have you tried to install ubuntu with the new version of BootCamp (make a XP Partition and then boot from cd ?)

I have been following this tutorial:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

Well, all Boot Camp really does is let you make a Windows drivers CD and handles the partitioning.  I have already done the partitioning using diskutil in the terminal (just like the tutorial said).  In fact, the tutorial says NOT to use Boot camp to  make partitions because Bootcamp assumes you only want windows and can cause trouble for triple booting.

I would just use [Parallels Desktop Beta]("http://www.parallels.com") but that doesn't work on the Mac pro yet either! ](*,)

If only I could boot from USB then my problem might be solved.  But I don't think my Kingston 128MB USB key is bootable.  If it was I would see it as a boot option when I hold Alt at bootup (right?).

If anyone can figure out how the heck to get Linux on a Mac Pro I will send you a cookie.. seriously.  I'm not joking :)

---

### Post by hazelb030 on 2006-08-23
I thought that in addition to building the driver cd and handling the partition procedure boot camp in fact emulates something like a bios so windows can be installed.

So in my opinion even for a dual boot installation with linux you should use boot camp :confused:

Perhaps the following links will help you to proceed 

[http://ubuntuforums.org/showthread.php?t=198453]("http://ubuntuforums.org/showthread.php?t=198453")
[http://www.mactel-linux.org/wiki/Dual_Booting]("http://www.mactel-linux.org/wiki/Dual_Booting")

I know that these instructions aren't written explicitly for a MacPro but it should be worth a try.

---

### Post by gwhanson on 2006-08-25
I recieved my Mac Pro wednesday of last week.  played with OSX for 2 days then decided to install ubuntu.  I followed the directionns at bin-false [http://bin-false.org/?p=17]("http://bin-false.org/?p=17") 

The only problem that I recall was that with the new bootcamp, refit can't find some file or other to start ubuntu (after it has been installed), but I can use bootcamp (hold down the option key and coose the "windows" drive at startup)

I am currently upgrading to edgy with this machine.

---

### Post by simmons on 2006-08-25
I, too, recently bought a Mac Pro and successfully installed Ubuntu on it following the bin-false.org instructions.  I'm not sure why the original poster is running into boot-time troubles that we aren't seeing.  Perhaps the MacOS updates I installed also updated the firmware?

My only problem installing Ubuntu was that I couldn't seem to get it set up to boot from a second drive.  I bet that would be easy when using the entirely legacy-free boot stack (i.e. elilo), but I hear that the proprietary Nvidia driver doesn't work unless you boot using the BIOS compatibility mode.

David

---

### Post by Peter Hartley on 2006-09-02
*I, too, recently bought a Mac Pro and successfully installed Ubuntu on it following the bin-false.org instructions. I'm not sure why the original poster is running into boot-time troubles that we aren't seeing.*

I too have a Mac Pro and when I try to install Ubuntu (eft knot 2) I'm getting the same "The drive appears confused (ireason=0x01)" error as described above -- even if I boot with irqpoll, which the message suggests I do. Self-compiled kernels have the same problem. All this is 64-bit (amd64), though -- have the people who've got it to work been using 32-bit (i386)?

Peter

---

### Post by simmons on 2006-09-05
> All this is 64-bit (amd64), though -- have the people who've got it to work been using 32-bit (i386)?

I installed the 32-bit version of Dapper without any problems.  I did not try installing a 64-bit version.

---

### Post by daedius on 2006-09-06
I'm not sure if there is some huge misunderstanding on this thread here or what.  But Ubuntu is most definitely not working on Mac Pro.  I think some of these guys think we are talking about "MacBook Pro". I've tried gentoo, ubunto, sabayon all without success in either x86 or amd64.   The bios for the cdrom just isn't emulated correctly. Apple needs to get off butts to either fix it, or parallels comes up with a proprietary solution.  Until then, sit tight, enjoy the OSX and windows glory. Mmm, yah.  I'm hoping there is some OSX update by Sept. 12th that aids some of these problems.

---

### Post by simmons on 2006-09-06
> I'm not sure if there is some huge misunderstanding on this thread here or what. But Ubuntu is most definitely not working on Mac Pro. I think some of these guys think we are talking about "MacBook Pro".

While I have seen some people confuse "Mac Pro" with "MacBook Pro", I can assure you that I'm running Ubuntu 6.06 on a Mac Pro.  By which I mean the tower dual-processor Core 2 Duo (the so-called "quad") system released last month.

Maybe not all Mac Pro machines ship with exactly the same BIOS version or optical drive?  I'm posting my Mac's MacOS "About This Mac" information below (the "Hardware" and "Hardware->ATA" pages).  Let me know if anyone wants me to post more information (dmesg, etc.).

Hardware Overview:

  Machine Name:	Mac Pro
  Machine Model:	MacPro1,1
  Processor Name:	Dual-Core Intel Xeon
  Processor Speed:	2.66 GHz
  Number Of Processors:	2
  Total Number Of Cores:	4
  L2 Cache (per processor):	4 MB
  Memory:	1 GB
  Bus Speed:	1.33 GHz
  Boot ROM Version:	MP11.005C.B00
  SMC Version:	1.7f6

ATA Bus:

SONY    DVD RW DW-D150A:

  Model:	SONY    DVD RW DW-D150A
  Revision:	1.MD
  Serial Number:	
  Detachable Drive:	No
  Protocol:	ATAPI
  Unit Number:	0
  Socket Type:	Internal
  Low Power Polling:	No

---

### Post by daedius on 2006-09-06
Thanks for your info simmons.  I'm not really sure what to say other than I'm amazed =P  When I get home from work i'll verify some of your info against my own.  You sir, are a most lucky MacPro owner.

Random questions:

1) Did you encounter any really long startup times with ubuntu x86?
2) Did you have to use irqpoll,noapic, etc to boot up?
3) you use an refit/boot camp 1.1 beta setup?
4) Your not part of some apple developer program and getting some secret updates we are not ;) 
5) In the meantime while we suffer, how do you like linux on MacPro?

---

### Post by daedius on 2006-09-06
-- dupe post --

---

### Post by daedius on 2006-09-06
Lastly, one more thing.  What driver are you using for your cdrom driver on your linux bootup?  Does it show up as /dev/hda*?  I know i'm asking tons of stuff, but a dmesg could be helpful as well =P

Thanks in advance!

- Daedius :)

---

### Post by daedius on 2006-09-06
Whoa. .   Our specs are different for the CDROM.


Machine Name:	Mac Pro
  Machine Model:	MacPro1,1
  Processor Name:	Dual-Core Intel Xeon
  Processor Speed:	3 GHz
  Number Of Processors:	2
  Total Number Of Cores:	4
  L2 Cache (per processor):	4 MB
  Memory:	1 GB
  Bus Speed:	1.33 GHz
  Boot ROM Version:	MP11.005C.B00
  SMC Version:	1.7f6

  ATA Bus:
  PIONEER DVD-RW  DVR-111D:
  Model:	PIONEER DVD-RW  DVR-111D
  Revision:	AB09
  Detachable Drive:	No
  Protocol:	ATAPI
  Unit Number:	0
  Socket Type:	Internal
  Low Power Polling:	Yes
  Firmware Revision:	AB09
  Interconnect:	ATAPI
  Burn Support:	Yes (Apple Shipped/Supported)
  Cache:	2000 KB
  Reads DVD:	Yes
  CD-Write:	-R, -RW
  DVD-Write:	-R, -RW, +R, +RW, +R DL
  Burn Underrun Protection CD:	Yes
  Burn Underrun Protection DVD:	Yes
  Write Strategies:	CD-TAO, CD-SAO, CD-Raw, DVD-DAO
  Media:	No


Are you using an external cdrom?

---

### Post by BobSongs on 2006-09-06
I'm not sure if I'm in the wrong category or not but I just purchased a Mac**Book** Pro.

I downloaded the Parallels Demo and successfully installed Windows XP Pro SP2 *and* Ubuntu 6.06.1 i86. The MacBook isn't a week old. It has the Intel dual-core and 2 Gb RAM.

I've seen somewhere else that dual-booting Linux on a Mac has been possible for a while. I'm just hoping a new release of Dapper will support the Intel chip.

---

### Post by daedius on 2006-09-06
More importantly, there appears to be a firmware update.  I wonder if this will help fix anything.

[http://www.cdrinfo.com/Sections/Firmware/SingleModel.aspx?DriveId=1300](http://www.cdrinfo.com/Sections/Firmware/SingleModel.aspx?DriveId=1300)

It looks like the new firmware was just released 01 Sep 2006.  I hope firmware can be applied through windows.

---

### Post by breuerp on 2006-09-06
I had similar problems installing on some non-standard 64-bit processors.  Namely the sync issue.  The following worked for me.  Add this bootup parameters in grub:  nomce nosplash

Let me know if it works.

---

### Post by daedius on 2006-09-06
So here are some updates.

1. I can't install the firmware updates through windows.  I think because i'm in emulated bios ( or possibly the EFI is just wacked ) that its impossible at the moment.

2. using nomce and nosplash do nothing to help the boot on both gentoo or ubuntu.

3. There is an application out there called DVRFlash for OSX that lets you update the firmware of your PIONEER DVRs.  I'm not sure how damaging this might be to the system.  Theres probably a reason the Pioneer DVR has a custom firmware.

So tonight i'm gonna borrow an external CD rom drive (usb) and try booting off of that.  It seems the safer option for me to try before a firmware update.  Once i'm in linux and can poke around with drivers more, i'll be able to determine the next step.  Thanks for everyones help so far, if anyone has any other news.  Please post =)

- Daedius

---

### Post by DylanRE on 2006-09-06
> **BobSongs said:**
> I'm not sure if I'm in the wrong category or not but I just purchased a Mac**Book** Pro.

I downloaded the Parallels Demo and successfully installed Windows XP Pro SP2 *and* Ubuntu 6.06.1 i86. The MacBook isn't a week old. It has the Intel dual-core and 2 Gb RAM.

I've seen somewhere else that dual-booting Linux on a Mac has been possible for a while. I'm just hoping a new release of Dapper will support the Intel chip.

[http://www.ubuntuforums.org/showthread.php?t=198453](http://www.ubuntuforums.org/showthread.php?t=198453)

There are instructions for dual-triple booting the MacBook Pro.

They're pretty simple, and it works great.

---

### Post by daedius on 2006-09-06
> **DylanRE said:**
> [http://www.ubuntuforums.org/showthread.php?t=198453](http://www.ubuntuforums.org/showthread.php?t=198453)

There are instructions for dual-triple booting the MacBook Pro.

They're pretty simple, and it works great.


This thread has nothing to do with MacBookPro.  Please avoid posting links or information on MacBookPro to avoid misinformation/confusion.

- Daedius

---

### Post by simmons on 2006-09-06
1) Did you encounter any really long startup times with ubuntu x86?

No excessively long startup times.  The LILO kernel loading may be a tad slower than usual.  (Although it's been a long time since the last time I used LILO.)  I don't recall any particular slowness in booting from the DVD.

2) Did you have to use irqpoll,noapic, etc to boot up?

I have never specified any custom kernel arguments on this machine.

3) you use an refit/boot camp 1.1 beta setup?

The Ubuntu disc booted up right away without refit or boot camp.  I was pleasantly surprised, since I was expecting to run into the problem that others have posted.  I was anticipating doing some driver debugging/tweaking to get Linux on this machine. :)

I did end up installing refit and Boot Camp 1.1 beta in the process of trying to get Linux installed on a second hard drive.  I eventually gave up and used Boot Camp to create a 30GB "Windows" partition onto the first drive, which I used to install Ubuntu.

4) Your not part of some apple developer program and getting some secret updates we are not

Nope.  This is the first real Mac I've owned, and I've never done any Apple development.  I always intended to install Linux on this machine, since I need Linux for work.  I read about the optical drive problems people were having, and took that as a challenge. :)

5) In the meantime while we suffer, how do you like linux on MacPro?

It screams!  GNOME comes up REALLY fast after I log in.  Subsequent logins (i.e. all the GNOME stuff is still in the buffer cache) are almost instantaneous.  A software project I'm working on takes about 30 minutes to build on my Pentium-M 1.5Ghz notebook, but it compiles in about 5 minutes on the Mac Pro with "make -j 4".  (And it's not 100% optimized for parallelized builds.)

I've posted my dmesg output here: [http://davidsimmons.com/files/macpro-dmesg.txt](http://davidsimmons.com/files/macpro-dmesg.txt)

It's interesting that the last line in that dmesg output is:
[4322109.062000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
...which is the same message others are talking about.  The drive seems to work, though.  I tested reading data from a Kororaa LiveCD, and playing a video from a DVD-ROM of video files.

I've posted "lspci" and "lspci -vv" output here:
[http://davidsimmons.com/files/macpro-lspci.txt](http://davidsimmons.com/files/macpro-lspci.txt)
[http://davidsimmons.com/files/macpro-lspci-vv.txt](http://davidsimmons.com/files/macpro-lspci-vv.txt)

Is your Ubuntu disc a CD or a DVD?  I've been using a DVD.

David

---

### Post by daedius on 2006-09-06
Thank you so much Simmons for your information! =P  I really hope I can try to put this to good use.  I haven't been using the DVD version myself. Hehe, though I doubt missing out on a few packages isn't a huge deal.  I'm going to give this external cdrom drive a try tonight. *crosses fingers* Ti'll then, i'll be browsing through these infos you sent me to get some ideas. Thanks again for all your help! =)

- Daedius

---

### Post by simmons on 2006-09-06
> Whoa. . Our specs are different for the CDROM.
...
Are you using an external cdrom?

No, I'm using the internal optical drive that came with the machine.  That's weird!  I noticed that you have the 3.0Ghz version of the Mac Pro.  I wonder if they're using different optical drives in those.  I picked my Mac Pro up at CompUSA (instead of an Apple store).  I don't know if that makes any difference.

> What driver are you using for your cdrom driver on your linux bootup? Does it show up as /dev/hda*? 

The cdrom shows up as /dev/hda.

> I haven't been using the DVD version myself. Hehe, though I doubt missing out on a few packages isn't a huge deal. I'm going to give this external cdrom drive a try tonight.

I was wondering about the disc type not so much because of the extra packages on the DVD, but because the disc type and/or the particular ISO9660/UDF variant/extensions might be triggering an issue.  That's a pretty far-fetched idea, but perhaps it's a variable to consider if you find yourself scraping the bottom of the barrel.

David

---

### Post by daedius on 2006-09-06
So, apparently Mac can detect and use external cdrom drive in OSX and Windows, but cannot boot from it.  I dallyied with fate by attempting to upgrade my PIONEERS firmware and was met with a nastygram.  Apparently I have a pioneer cdrom drive that looks like a PIONEER DVR-111D but under the hood is a completely other beast.  I'm running out of options and it seems like Apple only has the solutions.

My last chance to check is to try booting up and try telling the kernel to use a more generic ATAPI DVD drive.  Of course, i have to figure out how to do that first...

---

### Post by daedius on 2006-09-07
So, more updates.  Apparently I was using the generic drivers. I just tried booting up from a little usb stick using gentoo liveusb instructions and that did not work.  Bootcamp did not even detect it, rEFIt detected it but did not know how to boot it.  I'm at the point where all options are starting to get exhausted.

---

### Post by daedius on 2006-09-07
Forgot to mention that last night, I randomly tried the mactel-linux livecd (based of ubuntu).  That project seems way dead.  No luck with it.  At this point I have this feeling that the only option left ( assuming I didn't do anything wrong in the previous steps ) is to try to figure out how to somehow use elilo.  If that fails, all I can do is wait.

---

### Post by simmons on 2006-09-07
daedius -

A few ideas spring to mind.  Maybe you could borrow an internal CD-ROM drive and put it in the Mac temporarily to boot and install Ubuntu?  The Mac Pro has a great case and it's easy to swap out components.

Also...  It's my understanding that you can load and execute the kernel from a CD; the problem is when the loaded kernel needs to use the CD-ROM drive to mount a filesystem.  Perhaps a kernel could be loaded from the CD, and instructed to mount a filesystem from another device such as the USB stick?  That would require the usb_storage driver, and possibly others.  These extra drivers would probably need to be compiled into the kernel.

David

---

### Post by daedius on 2006-09-08
Hey there Simmons,

Thanks for the ideas.  I think you may be on the right track with the swapping out cdroms.  Last night I took apart my old computer and my girlfriends computer.  Unfortunately I only found another pioneer ( which strangely enough exhibited the same problem ) and my GF's Sony DW-U10A was practically bolted on in her G5.  Part of my confusion in this whole problem is i'm just completely not aware of what Apple supports and to what level.  Its all undocumented. I think it may be time for a pilgramage to Fry's to see if I can find some Sony DVD-r that fits my need.

I wish there were another solution at the moment, but my options are becoming slim. Elilo just isn't a clear solution to this problem from my experience last night.


Edit & Update
- so far, i've tried 4 hard drives, only 1 (the Pioneer) seemed any where near successful ( but I kept getting the EXACT same cdrom errors I get with the DVR-111D

You know, its funny you mentioned that solution about booting from cd, then loading from USB.  I experimented with that a little yesterday with a liveusb I made.  It looked like it tried to boot up something, but ran into path errors.  Who knows, maybe its worth another look.

- Daedius

---

### Post by forkbeard on 2006-09-08
If anyone is still wondering how to get their Macs to boot off a USB drive, I had to go into DiskUtility (either from the OSX install cd or from within OSX) then repartition the USB drive. When you repartition though, you have to hit the "Options" button and select the GUID partition scheme. After that it'll be perfectly bootable by any Intel Mac afaik. 

I've tested this on Intel iMacs, MacBooks and MacBook Pros but not Mac Pros, although the partition schemes across all four lineups are exactly the same so it should work with them too.

---

### Post by daedius on 2006-09-08
Thanks forkbeard, I can try to verify this over the weekend.  I've not had much time to do liveusb boot testing, but what little I saw it looked optimistic.

---

### Post by daedius on 2006-09-08
On another note, it appears Apple has made is practically impossible to find any internal optical drives other than the lame poorly EFI supported Pioneer DVR-111D.I called a local apple store, the online apple store, applecare, sony store, and the sony parts department.  Its like the Sony DW=D150A just doesn't exist.  It must be some OEM deal that just kept completely away from the market, that, or i'm barking up the wrong tree with the name.  Maybe theres an OEM in Retail's clothing.

---

### Post by daedius on 2006-09-08
So after work today I went down to Fry's to pick up a DRU-810A, I stick it in, ok, it comes up in apple.  I boot up on it "cannot detect boot medium", for chance I try again to boot on the sony, if finds it this time, and I get those same "device looks confused messages!" (grar).  Then something interesting happens....

After I rebooted, there is a part where it takes forever to "::mounting CD to tmpfs /dev/hda".. and I randomly decided to eject and re-enject the machine.  It finds the cd! if only for a few seconds, it found it, and proceeded to try to load it over to tmpfs.  Then something just stalled big time.  I rebooted and i never saw that happen again (maybe I was just lucky).  Anyhow, this weekend I continue the battle most noble. 

This round!: Revenge of the LiveUSB

- Daedius

Edit:

In other news, I had very good indian food tonight at Taj Mahal in Houston

---

### Post by daedius on 2006-09-11
w007!  Linux is GO GO GO!~!~!

I figured out a way to trick the gentoo boot into working even though the cdrom is hosed.  I create a partition on the hard drive, dd the minimal image to the hard drive, burn an iso to, boot the cd, on boot up the bootloader will take the image from the hard drive rather than the cd.  And your in business!  I used the sabayon linux distro and was able to see instantly amazing stuff, long live linux!  Thankyou for all your help! I probably would have returned my MacPro if not for your encouragement!

- Daedius

---

### Post by kwanghui on 2006-09-11
Just to let you know that I just tried the recently updated Parallels Desktop with my Mac Pro (dual 2.66 woodcrest xeon with 2gb RAM... NOT the macBOOKpro). 

it installs and runs ubuntu 6.06 fine.

Just save the ubuntu ISO file on your mac hard drive, then point to it as the boot cdrom instead of the actual cdrom. Create a linux2.6 VM, then boot the livecd and install. Works really nicely, and a good way for you to bypass these problems with the hardware.

At least on my setup, the ethernet bridging didn't work. However, host-based networking worked, and I used systempreferenes->sharing->internet from osx to allow ubuntu to access the internet. 

Best regards.

---

### Post by daedius on 2006-09-11
yah, I used parallels too.  I prefer the real thing though.  For the benefit of people who want to work on linux open source on real drivers.

---

### Post by daedius on 2006-09-12
Simmons, if your still around. I have another question for you about your setup.  Which boot loader to you use and could you send us any configs (lilo.conf / grub.conf ) and any manual step you did to get it to work =)

thanks as always,

- Daedius

---

### Post by simmons on 2006-09-12
> **daedius said:**
> Simmons, if your still around. I have another question for you about your setup.  Which boot loader to you use and could you send us any configs (lilo.conf / grub.conf ) and any manual step you did to get it to work =)

I used LILO.  Here's my lilo.conf:

```
boot=/dev/sda3
default=Ubuntu
map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/sda3
label=Ubuntu
read-only

```

I pretty much followed these instructions for installing Ubuntu 6.06:

[http://bin-false.org/?p=17](http://bin-false.org/?p=17)

I installed Boot Camp, made a "Windows" partition to install Linux on, and played around with the rEFIt tool for syncing the GUID partition table with the legacy partition table.  I did a lot of extra work and fooling around trying to get Linux to boot off the second hard drive, but I ended up giving up on that and installing to a partition on the first hard drive.

To boot into Linux (if I've been in MacOS), I have to hold down the option key at startup and select "Windows".

That's about all I can recall.

David

---

### Post by daedius on 2006-09-13
Thanks a bunch simmons! I was unaware that refits partition tool did anything other than partition.  After it synched up the disks, penguins were flying!  :D 

- Daedius

---

### Post by DarkDave on 2006-09-13
I had some success getting the installer to run on my Mac Pro and mount the Superdrive, finally!!!

Try adding the following boot switches to the command line at boot time:

irqpoll acpi=off

Using these options, the installer mounted the DVD without the interrupt or DMA error messages.

---

### Post by daedius on 2006-09-13
DarkDave, do you have a Pioneer? =) I could have SWORN I tried these.  I remember getting kernel lockups right at the very beginning when it was loading its core sata modules.

---

### Post by DarkDave on 2006-09-13
Yes, I have the Pioneer drive in mine.

Actually, the line I posted is not quite correct, oops!

Try this one:

 irqpoll acpi=force

The acpi=force makes all the difference in the world.  With these options I had no problems with the HD or the DVD.

---

### Post by daedius on 2006-09-13
Strange, I have no lcuk with this method either. Wonder whats different.

---

### Post by DarkDave on 2006-09-14
I had better luck with a Fedora Core 5 installation DVD.  The Kubuntu 6.06 Live CD was giving me fits with the SATA driver still.

One thing to try would be to place the Kubuntu installation files onto a second drive in the system, either another SATA drive, or an IDE drive in the spare Superdrive bay.

---

### Post by toddbyrne on 2006-09-18
Any have any luck getting more then 2GB of ram to show up? 

I am not sure if I have something wrong my kernel config or what. Any help would be appreciated.

---

### Post by DarkDave on 2006-09-24
I'm running a Mac Pro with Fedora Core 6 Test 3. *I've noticed several people have had problems with IDE/SATA and their DVD drives under Linux. *I have been working to resolve some of these issues, and have had good success, as well as making some compromises.

First, there seems to be an issue with the standard Linux IDE DMA drive and the Intel 5000X chipset. *Upon loading of the driver, the kernel gets hit with interrupts with IRQ #90, which is the legacy IDE controller on the ESB2 chip. *The kernel usually ends up disabling the IRQ, and any hope of accessing any device on the controller. *This affects all DVD or CDROM devices hooked up, not just the Superdrive that comes with it.

The workaround at install time is to add the kernel command line parameters:

acpi=force irqpoll

This works for the Fedora Core 6 installer, other distros maybe, maybe not. *Gentoo 6.06 didn't work. *And the irqpoll setting seems to screw up the CPU spinlocks when booting an SMP kernel. *So that won't work after installation.

Once you do get Linux installed either via DVD or HD image, then there's another issue. *The ESB2 is detected as the 4 port SATA device in the ICH6, not the 6 port SATA controller it really is. *ESB2 is an offshoot of one of the ICHes.

For this, two things must be done. *First is to edit and re-build the AHCI driver. *Edit the file ahci.c and add the following line in the Dev ID list:

{ PCI_VENDOR_ID_INTEL, 0x2680, PCI_ANY_ID, PCI_ANY_ID, 0, 0, * * * * *
board_ahci }, /* ESB2 */

This will tell the driver to claim Dev ID 0x2680, which is the AHCI controller ID in the Mac Pros. *According to the ESB2 datasheet, the ID could be 0x2680, 0x2681, 0x2682, or 0x2683 depending on the fusing options. *In this case, 0x2680 was not claimed by default in the AHCI driver.

Also, when you rebuild the AHCI driver, it's a good idea to either not build the ata_piix driver in your kernel, or delete the module altogether. *It won't work, and it's really the wrong driver for the ESB2 chips. *We only need the AHCI driver here, the ata_piix is for older chipsets like ICH5, ICH5, etc. *The ata_piix tries to claim the 0x2680 Dev ID, which is the ID 
presented in these older chipsets for their 2 or 4 port SATA controllers.

Now rebooting with the fixed AHCI driver should report all 6 SATA ports on boot, yea!!!! *Those two SATA connectors on the motherboard just below the first hard drive bay are now usable.

Now for the second major problem. *The DVD drive still won't work on the IDE controller. *The kernel reports:

ESB2: 100% native mode on irq 90

I've read on other forums that the IDE controller might not be getting set to the legacy or compatible mode, and thus the IDE driver is trying to set it up incorrectly. *Also, I don't know how to change the controller mode in the EFI firmware.

Until there's driver update for this or an EFI update, here's two things you can do. *First is to swap it out with a SATA DVD drive. *OS X will see it and use one just fine, and you can use one of the extra SATA connectors on the motherboard to hook it up. *

Alternatively, (and much cheaper) you can buy a SATA to IDE bridge card that will allow you to connect an IDE device to one of the extra SATA connectors. *I did this, but be careful to make sure the bridge card you buy physically fits between the DVD and the power supply. *There's only about 2 inches of room in there. *I had to bend the IDE 40 pin connector up to a 45 degree angle to get it to fit.

Let me know if you have more specific questions, or you have some other ideas that have worked for you.

---

### Post by cbetancourt on 2006-09-25
Hello All,

We recieved a MacPro where I work last week and have been trying to put linux
on it since getting it.  My first inclination was to try Fedora, but I wasn't having any luck.  When that didn't work I decided to try Ubuntu.  Here is 
where things get interesting.  When I boot the live cd version I get no 
no video, just a blsck screen.  BUT if I wait for the cd drive to quiet down
(so that I can be sure it's done booting) I can drop into a virtual terminal,
log in, and start issuing commands.  I know this works because I used 'eject'
to open and close the cd drive.  Any thoughts on how to get the video 
working?

Also should mention, it's got one of the pioneer drives.

Thanks for your time,
C. Betancourt

---

### Post by simmons on 2006-09-25
cbetancourt -

That's a new one on me!  What video card do you have in your Mac Pro?

DarkDave -

I'm surprised there are issues with the chipset on the Mac Pro.  I'm wondering if my Mac Pro (which Linux installed on fine) has a different chipset.  (It definitely uses the Sony optical drive instead of the Pioneer, which seems to be some sort of a clue.)  The following is what my lcpci reports with regards to IDE/SATA hardware:

0000:00:1f.1 IDE interface: Intel Corporation Enterprise Southbridge PATA (rev 09)
0000:00:1f.2 IDE interface: Intel Corporation Enterprise Southbridge SATA cc=IDE (rev 09)

Numeric vendor/device id's are:

0000:00:1f.1 0101: 8086:269e (rev 09)
0000:00:1f.2 0101: 8086:2680 (rev 09)

David

---

### Post by daedius on 2006-09-25
Amazing investigations DarkDave.  I'm happy this thread isn't ending off in these hacks to try to install linux.  You certainly know your stuff and the available options.  I do think our end goal would be to get linux stable atop MacPro -- no modification or special hacks required.  I'd really like your opinion on what the next step and options are.  As I see the assertions throughout this thread, there are a few issues:

- linux IDE DMA with x5000
- 6 port SATA drives being improperly detected
- unclear state of large memory

We need to define which of these issues are limitations(bugs?) of linux operating system ( and could possibly included as fixes within future kernels ), and which of these are corrections that need to be made within the EFI/SCM and should be notified to Apple.   I'm not as technically familiar with the Linux operating system, so your help would be greatly appreciated to answering these questions.  I'll gladly search for what I can.

---

### Post by sergiez on 2006-09-26
Hi all!

I am following this thread from the begning. I assume all the errors related to the superdrives comes installing the Ubuntu Dapper x86_64 bits version. I have bin able to install the x86 distro (32bits) without problems. Just solving the issue with the instalation of lilo instead of grub at the system partition, not the MBR.

Actually my system is currently instaled, up and running the 686-smp kernel. 

I can reproduce the same problem as the rest of the people when trying to install the 64bits version. I tried with acpi=force irqpoll but no way. The DVD drive stoped mounting the root filesystem. And that´s all.

I know this is not too much... in fact it is nothing, but well, that´s how the things are. I will continue trying with 64 bit distro.

---

### Post by sergiez on 2006-09-26
Hi all!

I am following this thread from the begning. I assume all the errors related to the superdrives comes installing the Ubuntu Dapper x86_64 bits version. I have bin able to install the x86 distro (32bits) without problems. Just solving the issue with the instalation of lilo instead of grub at the system partition, not the MBR.

Actually my system is currently instaled, up and running the 686-smp kernel. 

I can reproduce the same problem as the rest of the people when trying to install the 64bits version. I tried with acpi=force irqpoll but no way. The DVD drive stoped mounting the root filesystem. And that´s all.

I know this is not too much... in fact it is nothing, but well, that´s how the things are. I will continue trying with 64 bit distro.

---

### Post by cbetancourt on 2006-09-27
simmons,
sorry for the dellay in this, but the specs reported by OSX are:
```
ATI Radeon X1900 XT:

  Chipset Model:	ATY,RadeonX1900
  Type:	Display
  Bus:	PCIe
  Slot:	Slot-1
  VRAM (Total):	512 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x7249
  Revision ID:	0x0000
  ROM Revision:	113-A52027-140
  EFI Driver Version:	01.00.140
  Displays:
Cinema HD:
  Display Type:	LCD
  Resolution:	1920 x 1200
  Depth:	32-bit Color
  Core Image:	Supported
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
Display:
  Status:	No display connected
```
But I don't suppose it matters too much for me anymore, the powers that be have decided to just run with OSX:(

---

### Post by DarkDave on 2006-09-27
> **simmons said:**
> cbetancourt -

That's a new one on me!  What video card do you have in your Mac Pro?



My Mac Pro has the Nvidia GeForce 7300 GT card in it.  I bet there's some issue going on with the ATI cards then, perhaps the driver in the installation image isn't working with it.

---

### Post by DarkDave on 2006-09-27
> **daedius said:**
> Amazing investigations DarkDave.  I'm happy this thread isn't ending off in these hacks to try to install linux.  You certainly know your stuff and the available options.  I do think our end goal would be to get linux stable atop MacPro -- no modification or special hacks required.  I'd really like your opinion on what the next step and options are.  As I see the assertions throughout this thread, there are a few issues:

- linux IDE DMA with x5000
- 6 port SATA drives being improperly detected
- unclear state of large memory

We need to define which of these issues are limitations(bugs?) of linux operating system ( and could possibly included as fixes within future kernels ), and which of these are corrections that need to be made within the EFI/SCM and should be notified to Apple.   I'm not as technically familiar with the Linux operating system, so your help would be greatly appreciated to answering these questions.  I'll gladly search for what I can.


One thing I'd like to try is to get ahold of another 5000X chipset machine and correlate the Linux behavior on it.  This would help to isolate any issues due to EFI, and determnine whether or not the memory and IDE issue we see might be due to motherboard differences or driver issues.

It's very interesting that the 32bit kernel version in Ubuntu works fine with the IDE controller.  I'll take a look at running a i686 compiled kernel on my machine.  

Dave

---

### Post by SealFriend on 2006-09-27
Hi,

Good job man on getting Ubuntu on MacPro. It appears you did not have to do anything special like loading a new reflt or something.

Just used bootcamp to create a windows partition and booted Ubuntu off that ?

No changes to LILO settings nothing ?

---

### Post by sergiez on 2006-09-28
> **SealFriend said:**
> Hi,

Good job man on getting Ubuntu on MacPro. It appears you did not have to do anything special like loading a new reflt or something.

Just used bootcamp to create a windows partition and booted Ubuntu off that ?

No changes to LILO settings nothing ?

Hi,

In fact nothing speciall is needed to boot the LiveCD (talking about 32bits version). The only problem I got was with the Bluetooth keyboard and mouse. Bluez-utils makes them not working so when gnome starts it looks frozen. I noticed this because the first Ubuntu I try to install was n custom liveCd build by the Open Source Group of the Catalonian Open University. This custom LiveCD boots with no problems. Then, when I try the standard LiveCD, the keyboard and the mouse didn´t work. So I install the custom CD and I install the ubuntu-desktop package later. As soon bluez-utils was installed, the mouse and the keyboard stop working. I think if you have both USB devices there will be not problems to install the standard LiveCD. If you have the wireless Apple keyboard and mighty mouse you can use reconstructor to build your own custom Ubuntu liveCD (reconstructor.aperantis.com).

I installed rEFIt, but I think it is not necessary at all. In fact some people of this forum has Ubuntu installed on the MacPro and they are not using rEFIt. They said that is possible to boot the linux system jus keeping pressed the option(alt) key during the booting time. Then select the windows partition as you say. I did not try this point.

Yes. There are few issues when installing lilo. First of all, lilo does not come in the liveCD. The steps to follow in order to install lilo in the boot sector of the ubuntu partition are [here]("http://bin-false.org/?p=17").

---

### Post by cbetancourt on 2006-09-28
DarkDave,
I'm not sure that it's necessarilly a driver issue as it does it with
whatever cd's I try.  Granted, I've only tried Ubuntu and Fedora,
but since they both behave the same way I'm going to assume that 
it's an EFI issue.  on the other hand you know what they say about
assumptions...

---

### Post by sergiez on 2006-09-29
Hi all,

Yestarday I was trying with Edgy 64bits. The LiveCD boots with the irqpoll option and giving the error messages such "device confused" or something like this. But finally it runs gnome... but the blutooth bug is still there so I was unable to do anything. I will take a USB mouse and keyboard from my workplace today in order to try with them during the weekend.

Has anyone try to boot from a HD partition build with dd and the liveCD?

---

### Post by daedius on 2006-09-29
Yes, I currently dd a livecd iso of gentoo to a partition, and boot off a livecd cd.  I suspect you could do the same thing with an ubuntu livecd.

---

### Post by daedius on 2006-09-29
10.4.8 came out today.  I wonder if any of our problems have been changed.

---

### Post by sergiez on 2006-10-01
> **daedius said:**
> Yes, I currently dd a livecd iso of gentoo to a partition, and boot off a livecd cd.  I suspect you could do the same thing with an ubuntu livecd.

I have been looking for instructions on how to dd a iso livecd to a partition and then make it booteable but I didn´t find it. Can you please post the steps you follow or a url as reference?

---

### Post by daedius on 2006-10-02
Hmm, sorry if I came off vague, my steps are pretty simple:

1) download gentoo livecd iso  ( I like the Sabayon distrobution[gentoo based] )
2) insert a blank cd
3) "hdiutil burn <NAME OF ISO>.iso" to burn the cd
4) "sudo if=<NAME OF ISO>.iso of=/dev/diskXsY" where X and Y correlate to a free disk partition (i.e. disk0s5 )
5) install refit 0.8 ( which has specific support for mac pro)
6) reboot and boot from the cd, hit alt+f1 to get into the console mode, and it should say that it found the CD image on /dev/sdaX

---

### Post by daedius on 2006-10-02
considering the chances that Apple may never fix the EFI problem,  I wanted to put a call out for information on the cdrom drives.  


A)  We know for certain there have been reports that the SONY DVD RW DW-D150A works for linux cd boots.  Does anyone have an sources for where these can be purchased.  I called up and down sony and apple to try to find these, but had no luck.  If anyone has any knowledge on where to get these, sharing would be appreciated.

B) There've been some posts about using SATA cdrom drives and or SATA->IDE conversion.  If anyone has success with this method, could you please post your setup method and specifically the cdrom model you used. 

Thanks.
- Daedius

---

### Post by sergiez on 2006-10-03
> **daedius said:**
> Hmm, sorry if I came off vague, my steps are pretty simple:

1) download gentoo livecd iso  ( I like the Sabayon distrobution[gentoo based] )
2) insert a blank cd
3) "hdiutil burn <NAME OF ISO>.iso" to burn the cd
4) "sudo if=<NAME OF ISO>.iso of=/dev/diskXsY" where X and Y correlate to a free disk partition (i.e. disk0s5 )
5) install refit 0.8 ( which has specific support for mac pro)
6) reboot and boot from the cd, hit alt+f1 to get into the console mode, and it should say that it found the CD image on /dev/sdaX

OK! I did it! I dd the sabayon liveCD to disk0s4 and everything goes as you said. I install the distro to /dev/sda3 but it takes a very long to boot. It did not crash, but looks like thinking too much analysing all volumes. As it was too late (1am) I decided to reboot in OSX (CTRL+ALT+DEL) and will try again today. This was so strange because the clone liveCD was booting without problems.

Unfortunately the ubuntu LiveCD does not boot in the same way as sabayon. It stops when the dvd drive is dissable because its confussion so after clone the liveCD to a HD partition I have to find the way to make this partition booteable. I think configuring lilo to boot it will be enough. Has someone try this point?

---

### Post by daedius on 2006-10-03
My experiences are the same as yours Sergiez, long boot up times.  I think the volume detection slowdown must be a problem with shoddily supported hard-drive SATA drivers in linux, because I have an intel mac mini that just zooms past those parts.  DarkDave suggested a fix that will get all 6 sata drives up and running, perhaps this fix makes SATA detection faster on bootup?

---

### Post by Kunimodi on 2006-10-03
Hi, folks.  I've been following this thread and would like to know if anyone has had any success installing Ubuntu (or another distro) on a **second** drive.  I have three drives in my Mac Pro and am trying to install Ubuntu on either the second of third drive.  I initially was trying with RAID, but now am simply trying to do one drive and have been able to install the OS and lilo, but on boot it gives a ton of file/directory not found messages and is stuck at the BusyBox login prompt.  Has any one seen this and found a work around?  Thank you very much.
Cheers,
Kunimodi

---

### Post by DarkDave on 2006-10-03
> **daedius said:**
> considering the chances that Apple may never fix the EFI problem,  I wanted to put a call out for information on the cdrom drives.  


A)  We know for certain there have been reports that the SONY DVD RW DW-D150A works for linux cd boots.  Does anyone have an sources for where these can be purchased.  I called up and down sony and apple to try to find these, but had no luck.  If anyone has any knowledge on where to get these, sharing would be appreciated.

B) There've been some posts about using SATA cdrom drives and or SATA->IDE conversion.  If anyone has success with this method, could you please post your setup method and specifically the cdrom model you used. 

Thanks.
- Daedius


I don't have any clue as to why the Sony drives might be working.  In addition to the Pioneer DVR-111 drive, I have also tried my older BenQ 1620 DVD writer in the Mac Pro.  This drive also reported the same IDE failures as the Pioneer.

With the SATA to IDE adapter, I have had success with every device I've tried hooking up to it, even when running under Mac OS X.  Hard drives and DVD drives seem to work great with the adapter.

As for the boot speed, the only booting delay I saw was due to the DVD drive when hooked up to the IDE connector.  The kernel had to time out and disable the IDE IRQ #90 before continuing on with the boot process.  Ever since I have switched to the AHCI drive and moved my DVD to SATA, I don't see any slowdown on boot anymore.

Dave

---

### Post by DarkDave on 2006-10-03
> **Kunimodi said:**
> Hi, folks.  I've been following this thread and would like to know if anyone has had any success installing Ubuntu (or another distro) on a **second** drive.  I have three drives in my Mac Pro and am trying to install Ubuntu on either the second of third drive.  I initially was trying with RAID, but now am simply trying to do one drive and have been able to install the OS and lilo, but on boot it gives a ton of file/directory not found messages and is stuck at the BusyBox login prompt.  Has any one seen this and found a work around?  Thank you very much.
Cheers,
Kunimodi

I could never get lilo to work on my Mac Pro.  I ended up using GRUB instead.

I would suggest switching to GRUB as the bootloader.  The secret to getting GRUB to work is not running the EFI partition sync tool from rEFIt or the command prompt when installing Linux.  

As long as your Linux boot partition is listed as a Linux (0x83) type in the legacy partition table (not the EFI GPT table), then GRUB will have no issues detecting partitions or booting Linux.  Also, if you set your grub.conf to boot=/dev/sda, then when running grub-install, GRUB will update the MBR, but only the MBR of the legacy partition table and won't corrupt the GPT.

GRUB seems to work great with rEFIt with the following steps:

1.  At install time, and before rebooting after the install tool is finished, drop to a shell prompt.  Run fdisk, and make sure the Linux boot partition is set to a non EFI GPT type, so that the type is either 0x83 (Linux) or vfat depending on your install.  Save table and exit.

2.  Now run grub-install or grub with install commands, and make sure that you install grub to the MBR of /dev/sda.  This is safe since it will only update the legacy partition table, not the GPT table.  This should not ever hose the GPT table.  If successful, GRUB will complete without any errors.  If it hangs or errors when installing, then most likely the partition type didn't get updated.

3.  Reboot, and do _not_ run the rEFIt partition sync tool.  This tool will try and fixup the Linux boot partition to a GPT partition type, usually 0xEF.

4.  Boot to Linux partition from rEFIt.  GRUB should boot normally after that.

Dave

---

### Post by Kunimodi on 2006-10-03
Thank you, Dark Dave.  Last night when I fiddled with Grub it got to Stage 2 and told me to wait, but after a few minutes I got impatient and went back to trying with lilo as it seems like most people have had success with that.  I'm glad it works for you and I would think this is how it should be integrated into the Ubuntu installer.

Anyhow, I just tried a simple idea to get Ubuntu running on its own drive: swapping the drive so that it was in the leftmost (first) position.  To my delight, this actually worked and now it is booting fine into Ubuntu Server 64-bit.

I expect there will be some rough edges as I get video, sound, etc working (I intend to use it as a workstation and not a server, but I like to build everything by hand), but that's the fun of it. :)

---

### Post by xpediant on 2006-10-04
I'm attempting a install of just Ubuntu straight ( No dual boot).  I don't have the CD's for OS X so solutions requiring running OS X i've been unable to attempt. The problem is after installation and reboot to run Ubuntu the system hangs on loading second bootloader. A small window pops up alternating with a picture of a question mark and a picture of a outline of two faces (i'm assuming this is a Mac thing). The system then reboots. This cycle continues with the system appearing to run harder with each cycle ( Fans speed up incrementally with each boot.)
The system is a a1047 model G5. 
2.0 dual core processor
160gb HD
single optical drive ( not sure of the model but the optical drive didn't seem to be an issue.)

I'm using the latest Dapper Drake Cds. The install works correctly with the Mac install disc and the x86 disc is not even recognized(tested x86 disc in another PC to make sure it burned correctly). 
I've read up on the Ubuntu forums and the general net. I've used mac-fdisk with the b option to create the bootloader partition. I've used the c option and created a 16MB partition for the bootloader as one forum mentioned the 800K size was not large enough for GRUB.
I've reconfigured yaboot to to see the bootload correctly.
I've run out of ideas as to what is going on ](*,) and i'm hoping that someone could clue me in. Thanks:)

---

### Post by sergiez on 2006-10-04
> **daedius said:**
> My experiences are the same as yours Sergiez, long boot up times.  I think the volume detection slowdown must be a problem with shoddily supported hard-drive SATA drivers in linux, because I have an intel mac mini that just zooms past those parts.  DarkDave suggested a fix that will get all 6 sata drives up and running, perhaps this fix makes SATA detection faster on bootup?

Not only long boot time, but also crashed after more than 30 minutes. I will check for DarkDave fix as soon I can. 

Thank you again.

---

### Post by sergiez on 2006-10-04
> **xpediant said:**
> The system is a a1047 model G5. 
2.0 dual core processor

So it is not a MacPro and not even an Intel based Mac so it is not the correct thread to post this question. Even that, I can´t help you. I have no acces to G5 PowerPC based Mac right now.

Sorry.

---

### Post by daedius on 2006-10-04
sergiez,

Hmm.  I do not experience crashing at all =/  You might wanna look into that.

---

### Post by belphanior on 2006-10-07
Hi everyone!

I just thougt I'd pop in here, because I've gotten the CD-Drive on my MacPro to work :) 

Once you have linux installed you simply need to upgrade your kernel to 2.6.19-rc1, which now includes the libata-base PATA drivers. If you then use that new driver for the PATA ports (it's called CONFIG_PATA_MPIIX in menuconfig) instead ov the "classical" IDE drivers the CD drive works fine.

Now someone will just have to make a livecd that includes this driver :p :p :p 


Other things to note:
I installed linux on a seperate hdd and partitioned it with the traditional MBR partition scheme, no GPT at all. This allows me to have as many partitions as I want.

Sound does not work. It is detected (Intel HDA with Realtec ALC885 codec), but I get no sound.

Edit:
Btw: Linux boots like lighning, no slowdowns at all when detecting volumes.

---

### Post by DarkDave on 2006-10-07
> **belphanior said:**
> Hi everyone!

I just thougt I'd pop in here, because I've gotten the CD-Drive on my MacPro to work :) 

Once you have linux installed you simply need to upgrade your kernel to 2.6.19-rc1, which now includes the libata-base PATA drivers. If you then use that new driver for the PATA ports (it's called CONFIG_PATA_MPIIX in menuconfig) instead ov the "classical" IDE drivers the CD drive works fine.

Now someone will just have to make a livecd that includes this driver :p :p :p 


Other things to note:
I installed linux on a seperate hdd and partitioned it with the traditional MBR partition scheme, no GPT at all. This allows me to have as many partitions as I want.

Sound does not work. It is detected (Intel HDA with Realtec ALC885 codec), but I get no sound.

Edit:
Btw: Linux boots like lighning, no slowdowns at all when detecting volumes.

Good to know some of the IDE fixes have been integrated into 2.6.19-rc1.  I couldn't tell from the changelog what was integrated, so I'll have to try it out.

I've been able to get the ata_piix driver in 2.6.18 to recognize the legacy IDE controller, but it won't detect any devices.  Looks like rc1 has the fix we need.

Still, we should be using the AHCI driver for the SATA ports, I'll check and see if they added the Mac Pro ESB2 PCI dev id to it.

Sound does work, just not through the speaker jacks.  For some reason the current ALSA driver doesn't control the audio outputs correctly.  This is a known issue and hopefully will be resolved soon.  The optical output plug works, and I currently use this to get sound through an amplifier.  Just make sure the IEC958 port is turned on in alsamixer.

Dave

---

### Post by SealFriend on 2006-10-07
> **belphanior said:**
> Hi everyone!

I just thougt I'd pop in here, because I've gotten the CD-Drive on my MacPro to work :

[/FONT]
Once you have linux installed you simply need to upgrade your kernel to 2.6.19-rc1, which now includes the libata-base PATA drivers. If you then use that new driver for the PATA ports (it's called CONFIG_PATA_MPIIX in menuconfig) instead ov the "classical" IDE drivers the CD drive works fine.

Now someone will just have to make a livecd that includes this driver :p :p :p 


Other things to note:
I installed linux on a seperate hdd and partitioned it with the traditional MBR partition scheme, no GPT at all. This allows me to have as many partitions as I want.

Sound does not work. It is detected (Intel HDA with Realtec ALC885 codec), but I get no sound.

Edit:
Btw: Linux boots like lighning, no slowdowns at all when detecting volumes.

-[FONT="Fixedsys"] Congratulations - that too on a second harddrive. Exactly what I am looking for. My naive question is how did you install linux on the second hdd if the cd driver was not even recognized during boot of the linux? 
Did you follow the steps to dd an iso of a ubuntu/gentoo onto the second hdd and boot the first version off that ? I am tryin to follow the steps on the gentoo-wiki by daedius for loading on Mac Pro - did you follow similar steps of install reFIt and levergaging bootcamp ?
Also this new version of the kernel is it 32-bit x86 or the amd64bit ?

---

### Post by belphanior on 2006-10-08
[quote=SealFriend]Congratulations - that too on a second harddrive. Exactly what I am looking for. My naive question is how did you install linux on the second hdd if the cd driver was not even recognized during boot of the linux?
Did you follow the steps to dd an iso of a ubuntu/gentoo onto the second hdd and boot the first version off that ? I am tryin to follow the steps on the gentoo-wiki by daedius for loading on Mac Pro - did you follow similar steps of install reFIt and levergaging bootcamp ?
Also this new version of the kernel is it 32-bit x86 or the amd64bit ?[/quote]

Right. I partitioned the harddisk under OS X (you can simply select MBR partitioning in diskutil).

My partitioning scheme (which I've used elsewhere for a long time) is:
Primary 1 (sdb1): 100 MB ext2 /boot
Primary 2 (sdb2): 100 GB windows
Primary 3 (sdb3): 2 GB swap
Logical 1 (sdb5): 5 GB reiserfs /usr/portage
Logical 2 (sdb6): 15 GB reiserfs /
Logical 3 (sdb7): 100 GB reiserfs /home
leaving ~80GB free (it's a 300 GB hdd)

Then I installed refit into the efi partition (the small fat32 partition on the original hdd). The benefit of this (as opposed to a standard refit install) is that i can update refit or change it's settings without having to boot into OS X. The steps to do so can be found [here]("http://felipe-alfaro.org/blog/2006/09/19/installing-refit-on-the-hidden-efi-system-partition/")

I dd'ed the gentoo amd64-minimal iso onto my future windows partition. Then I did a normal stage1 amd64 gentoo install.
So obviously I built a 64-bit kernel. The driver should work just as well in 32bit, but I'm not sure why you'd want a 32bit kernel.

As my linux bootloader I installed grub into the /boot partition
The most recent version of grub in portage includes a fix that allows it to work, however I couldn't use a background image, because that made grub's menuscreen stay blank. Still, I like grub a lot more than lilo...

Then I installed bootcamp on OS X, used it to burn a windows XP driver disk, but didn't do any partitioning or anything else.

Then I inserted an XP CD and installed XP. I found that this caused XP to become the default boot disk, I had to hold down alt while booting to get into refit again. I found that this can be changed via a control panel applet.
I seem to recall that I had to repeat the steps to install refit after that...

---

### Post by daedius on 2006-10-09
> **belphanior said:**
> Hi everyone!

I just thougt I'd pop in here, because I've gotten the CD-Drive on my MacPro to work :) 

Once you have linux installed you simply need to upgrade your kernel to 2.6.19-rc1, which now includes the libata-base PATA drivers. If you then use that new driver for the PATA ports (it's called CONFIG_PATA_MPIIX in menuconfig) instead ov the "classical" IDE drivers the CD drive works fine.

Now someone will just have to make a livecd that includes this driver :p :p :p 


Other things to note:
I installed linux on a seperate hdd and partitioned it with the traditional MBR partition scheme, no GPT at all. This allows me to have as many partitions as I want.

Sound does not work. It is detected (Intel HDA with Realtec ALC885 codec), but I get no sound.

Edit:
Btw: Linux boots like lighning, no slowdowns at all when detecting volumes.
Thats great news!  You just made my day =)

---

### Post by simmons on 2006-10-09
Earlier in this thread, someone was asking about how to replace their Mac Pro's Pioneer optical drive (which seemed to be Linux-phobic) with the Sony DW-D150A drive that my Mac Pro came with (which works fine, but it's an oddball model number that you can't buy in stores).  Since my Mac Pro works fine, I haven't been following the thread too closely to see if the Pioneer issue has been resolved.

However, Engadget had an interesting article today about this drive:

[http://www.engadget.com/2006/10/09/how-to-supersize-your-mac-pros-superdrive/](http://www.engadget.com/2006/10/09/how-to-supersize-your-mac-pros-superdrive/)

It turns out that the Sony DW-D150A drive is actually a rebranded NEC ND-4570A drive, only with a firmware tweak that makes it slower.

David

---

### Post by daedius on 2006-10-10
> **belphanior said:**
> Hi everyone!

I just thougt I'd pop in here, because I've gotten the CD-Drive on my MacPro to work :) 

Once you have linux installed you simply need to upgrade your kernel to 2.6.19-rc1, which now includes the libata-base PATA drivers. If you then use that new driver for the PATA ports (it's called CONFIG_PATA_MPIIX in menuconfig) instead ov the "classical" IDE drivers the CD drive works fine.

Now someone will just have to make a livecd that includes this driver :p :p :p 


Other things to note:
I installed linux on a seperate hdd and partitioned it with the traditional MBR partition scheme, no GPT at all. This allows me to have as many partitions as I want.

Sound does not work. It is detected (Intel HDA with Realtec ALC885 codec), but I get no sound.

Edit:
Btw: Linux boots like lighning, no slowdowns at all when detecting volumes.

I tried out linux kernel 2.6.19-rc1 last night and recieved no more errors in detecting PATA/SATA. W00h00!  I used gentoo and I had some trouble when building my nvidia drivers, but I just had to modify my sources Kbuild.include to get things to compile properly without violating the sandbox.  Everything seems to be running smoother than ever.  I'm going to attempt to smoothe out my kernel to only what I need in the next few days, and see if I can figure out why udev is taking so long to get started.  Do any of you who have udev have that problem?  Thanks to everyones help =)

---

### Post by belphanior on 2006-10-10
> **simmons said:**
> However, Engadget had an interesting article today about this drive:

[http://www.engadget.com/2006/10/09/how-to-supersize-your-mac-pros-superdrive/](http://www.engadget.com/2006/10/09/how-to-supersize-your-mac-pros-superdrive/)

It turns out that the Sony DW-D150A drive is actually a rebranded NEC ND-4570A drive, only with a firmware tweak that makes it slower.

David

I've just done this, it worked fine. I've been testing the flashed drive with Nero CD-Speed under Windows (the best cd-drive testing tool I know of ... anyone know of something equivalent for linux?), reading & burning both went to 48x. Writing a CD in 3 minutes is nice :)

[Write-speed benchmark]("http://dthaler.de/benchmark-write.png") (Forgot to change the UI language for this one ...)
[Read-speed Benchmark]("http://dthaler.de/benchmark-read.png")

---

### Post by daedius on 2006-10-10
hmm, soo I have  CONFIG_PATA_MPIIX and scsi support on, but still no luck on getting the cdrom going.  I get some wierd message on it at the end of every boot.

hda: lost interrupt
hda: lost interrupt
ide-cd: cmd 0x3 timed out
hda: lost interrupt
hda: request sense failure: status=0x51 { DriveReady SeekComplete Error }
hda: request sense failure: error=0x44 { AbortedCommand LastFailedSense=0x04 }

I've tried various things, but i'm getting errors with my PIONEER.  Does anybody have a workable config to share?  Reading through the previous posts i'm reminded of the indication that these PIONEER drives may still need that sata-PATA-adaptification.

---

### Post by belphanior on 2006-10-11
> **daedius said:**
> hmm, soo I have  CONFIG_PATA_MPIIX and scsi support on, but still no luck on getting the cdrom going.  I get some wierd message on it at the end of every boot.

hda: lost interrupt
hda: lost interrupt
ide-cd: cmd 0x3 timed out
hda: lost interrupt
hda: request sense failure: status=0x51 { DriveReady SeekComplete Error }
hda: request sense failure: error=0x44 { AbortedCommand LastFailedSense=0x04 }

I've tried various things, but i'm getting errors with my PIONEER.  Does anybody have a workable config to share?  Reading through the previous posts i'm reminded of the indication that these PIONEER drives may still need that sata-PATA-adaptification.

That's because you still have the old IDE driver in your kernel and it's claiming the IDE interface instead of the new driver.
When the new driver is active your cd drive will be called /dev/sr0.

I'd be interested to know how everyone else is configuring their kernel? My config is [here]("http://dthaler.de/macpro_config_2.6.19-rc1").

---

### Post by DarkDave on 2006-10-12
On 2.6.19-rc1, I compiled my kernel much the same way, turning off the legacy IDE layer, and only using the ATA drivers, but I've been compiling them as modules.  I noticed under 2.6.19-rc1 on my machine, the pata_mpiix driver module never gets loaded.  This driver might not be needed at all to get the IDE ports working.

I still prefer to compile in the AHCI driver since this one fully supports the SATA features in the ESB2 chip.  To do this, you have to still edit the ahci.c driver to claim the 0x2680 PCI device ID, and edit the ata_piix.c driver to not claim the 0x2680 device ID.  This is the only way you can detect devices on all six SATA ports.  After patching, both the ahci and ata_piix drivers will co-exist, with the ahci controlling the SATA ports, and the ata_piix controlling the IDE ports.

With 2.6.19-rc1 I was still not able to get the Pioneer DVR-111D drive working, but my old BenQ DVD+RW and other misc hard drives worked just file.

There is a firmware update out there from Pioneer for this drive.  This might help.  I believe the latest version was 1.29.  I'll need to find a Windoze machine to upgrade the firmware as the update file is a Windoze executable.  I doubt it'll run under wine.

Here's a link to the Pioneer page:

[http://wwwbsc.pioneer.co.jp/product-e/ibs/device_e/dev00001r_e.html]("http://wwwbsc.pioneer.co.jp/product-e/ibs/device_e/dev00001r_e.html")

Dave

---

### Post by daedius on 2006-10-12
My experience is the same DarkDave

---

### Post by daedius on 2006-10-13
DarkDave, random question, did you see that 6 sata issue again with 2.6.19?  Also, whats the highest memory configuration thats been successfully tested out there?

---

### Post by DarkDave on 2006-10-13
> **daedius said:**
> DarkDave, random question, did you see that 6 sata issue again with 2.6.19?  Also, whats the highest memory configuration thats been successfully tested out there?

Yes, the 6 port SATA problem is due to the fact the base ahci driver file does not claim the PCI device ID entry for the Mac Pro ESB2 SATA controller.  On the Mac Pro, this shows up as ID 0x2680.  The driver does try and claim devices 0x2681, 0x2682, 0x2683.  By the same token, the ata_piix driver tries to claim 0x2680.  I think this is because other ICH based chipsets present their 4 port SATA controllers on device ID 0x2680, but I'm not 100% on this.  I'd have to search through some Intel ICH user guides.  According to the ESB2 guide, the lower 3 bits of the PCI device ID are set by the fuse bits in the chip.

With an unmodified build of the drivers, the ata_piix driver will end up claiming the legacy IDE controller on ID 0x269e, and the SATA controller on ID 0x2680.  This will work, but only the first four SATA ports will get probed.

I'd like to see a patch in the driver for this, but I don't know if this will break other ICH chipsets.  ICH6 supposedly uses 0x2680.  I don't know if the other ones that use ID 0x2680 support the AHCI functionality.

As for memory support, I only have 1GB in my Mac Pro, and I haven't heard any reports of issues with more memory.  The expansion boards can support up to 64GB.

Dave

---

### Post by belphanior on 2006-10-15
> **DarkDave said:**
> Yes, the 6 port SATA problem is due to the fact the base ahci driver file does not claim the PCI device ID entry for the Mac Pro ESB2 SATA controller.  On the Mac Pro, this shows up as ID 0x2680.  The driver does try and claim devices 0x2681, 0x2682, 0x2683.  By the same token, the ata_piix driver tries to claim 0x2680.  I think this is because other ICH based chipsets present their 4 port SATA controllers on device ID 0x2680, but I'm not 100% on this.  I'd have to search through some Intel ICH user guides.  According to the ESB2 guide, the lower 3 bits of the PCI device ID are set by the fuse bits in the chip.

With an unmodified build of the drivers, the ata_piix driver will end up claiming the legacy IDE controller on ID 0x269e, and the SATA controller on ID 0x2680.  This will work, but only the first four SATA ports will get probed.

As far as I can tell, what PCI-ID the ESB2 reports for SATA depends on some setting made by the firmware at boot time.
The PCI class code changes with the PCI ID; 0x2680 sets the class code to "IDE", ie it makes the contoller look like a PATA device. ID 0x2681 would apparently have the SATA class code. I'm not sure about the others, could be RAID and SCSI.

It doesn't make any (noticable) difference to how the chip operates though. For example the ahci driver reads in the class code, prints it out and the ignores it completely :D 

> **DarkDave said:**
> I'd like to see a patch in the driver for this, but I don't know if this will break other ICH chipsets.  ICH6 supposedly uses 0x2680.  I don't know if the other ones that use ID 0x2680 support the AHCI functionality.

As for memory support, I only have 1GB in my Mac Pro, and I haven't heard any reports of issues with more memory.  The expansion boards can support up to 64GB.

Dave

64? I thought 32 :)
Not that it matters; I have 1 GB also because I wasn't willing to buy RAM from Apple: it seemed overpriced.
I expect I'll be getting some elsewhere fairly soon

---

### Post by DarkDave on 2006-10-16
> **belphanior said:**
> As far as I can tell, what PCI-ID the ESB2 reports for SATA depends on some setting made by the firmware at boot time.
The PCI class code changes with the PCI ID; 0x2680 sets the class code to "IDE", ie it makes the contoller look like a PATA device. ID 0x2681 would apparently have the SATA class code. I'm not sure about the others, could be RAID and SCSI.

It doesn't make any (noticable) difference to how the chip operates though. For example the ahci driver reads in the class code, prints it out and the ignores it completely :D 



64? I thought 32 :)
Not that it matters; I have 1 GB also because I wasn't willing to buy RAM from Apple: it seemed overpriced.
I expect I'll be getting some elsewhere fairly soon

I wonder if we can modify the rEFIt code to program up the correct PCI ID before booting.  This would solve our issue without having to patch the ahci driver.

Dave

---

### Post by daedius on 2006-10-23
Sorry if this is just a real lamer question, but I purchased a IDE/PATA to SATA adapter ([http://www.newegg.com/product/product.asp?item=N82E16812206002](http://www.newegg.com/product/product.asp?item=N82E16812206002)), I have it plugged into the back of my dvd-drive.  I cannot see where to connect a SATA cable at all.  I've honostly never had a computer that had SATA and i'm not immediately seeing 2 available slots when I open the box.  Any advice?

- Daedius

Update:  Ok, so I see what looks like a SATA connector port.  Unfortunately it is behind the massive fan unit.  Hmm, from the posts on this thread it sounded alot easier ;P

---

### Post by sergiez on 2006-10-24
Well. Finally I had succes installing Ubuntu Edgy Eft RC 64bits in my MacPro!! It was late on night and I still have the problem that I can not access to my user account. Maybe was a problem with the keyboard and the password. I will try to solve this point tonight. But the important thing is that is possible to boot the x86_64 Altenate CD just with the irqpoll option when booting the kernel. Then the installation process is quick (not so quick as if the DVDROM drive was running in the correct way) but it take me half an our or so.

The process is basically the same as explained in  [http://bin-false.org/?p=17](http://bin-false.org/?p=17) for the MacBook Pro but pressing F6 at boot time and adding "irqpoll" at the end of the line of the kernel parametres. Then follow the installation process taking care of the partitioning process (Manual partitioning to keep safe the OSX system). When finisihing it will give an error installing Grub. At this point we have to select "Go Back" (RETROCEDER in spanish which is my default language) and select something like "open a terminal" in the menu (I don´t remember exactly the name of the option, and also it was in spanish). In the terminal just follow the instructions of  [http://bin-false.org/?p=17](http://bin-false.org/?p=17) to chroot into the installed system partition.

I was not able to edit lilo.conf (nano was not working... now I am thinking that maybe nano was not installed by default... I will check tonight) but installing lilo with -b was OK for booting the system.

If you have an Apple wireless keyboard and mouse you must remove bluez-utils before reboot. Do "aptitude remove bluez-utils" into the chroot system. Then Exit twice and abort the installation proces from the menu.

If you have rEFIt already installed then you will be able to boot your new Ubuntu Edgy system!! In my case, rEFIt is a little bit confused and it is showing 2 linux icons for booting from the Hard Drive. The first one is not running. I must select the second one in order to boot Ubuntu.

That´s all.

P.D. One time during the installation process, a message appears saying that the CDROM was not munted and suggest to try to mount it again. I just answered yes to this point.

---

### Post by daedius on 2006-10-25
So tonight I have been trying something new.  After digging into the innards of my MacPro, I finally got a sata enabled PIONEER 111D.  It shows up perfectly fine in OSX.   Linux, bootcamp, and refit however are another story.  Boot camp does not register bootable cds with the sata enabled drive.  Neither does refit.  And i've been having difficulties within the linux kernel getting any recognition of the drive at all on boot ups with the various SATA drivers.  Any help out there?

---

### Post by shaninho on 2006-11-04
Hello, I have read this thread several times in order to get my Mac Pro ubuntu setup working on my machine, so first of all, thanks. 

I installed 6.10 from the CD. I am experiencing performance issues, however - the mouse/keyboard input is excruciatingly slow. has anyone seen this/know a fix? 

Thanks in advance.

shaninho

---

### Post by daedius on 2006-12-12
Hey there =) I know this thread drifted off into a bit of oblivion, but I found some useful information the other day related to MacPro and audio.

[http://comments.gmane.org/gmane.linux.alsa.devel/42774](http://comments.gmane.org/gmane.linux.alsa.devel/42774)

Apparently some people are really close to having a functional solution with alsa.

---

### Post by sergiez on 2006-12-13
> **daedius said:**
> Hey there =) I know this thread drifted off into a bit of oblivion, but I found some useful information the other day related to MacPro and audio.

[http://comments.gmane.org/gmane.linux.alsa.devel/42774](http://comments.gmane.org/gmane.linux.alsa.devel/42774)

Apparently some people are really close to having a functional solution with alsa.

That is a great new. In fact, sound is the only reason why my Mac Pro is not fully running Linux.

I have to say that Ubuntu 64 bits can run on this machine using the kernel 2.6.19 downloaded from kernel.org and compiling it with the Intel PATA and SATA support and deselecting the ATAPI/IDE classic driver (as explained in an old post of this thread).

Doing this no more problems with the sony DVD drive and no perfomance issues. 

daedius: Did you try the alsa patch? I can´t wait to try this until new alsa releases. I will try it as soon I can and repport back on comments.

Thank you again for the good news and the link.

---

### Post by daedius on 2006-12-13
Nope =) haven't tried it yet.  Been a busy week! =P  I'm excited bout it though.

This weekend I'll probably give it a shoot.  Hopefully by then my
NEC ND-4570A ( sony mac drive clone ) will have arrived too.  My big issue still is with the Pioneer 111D optical >_<

Glad to hear your machine is up and running near full capability linux wise, Sergiez! <('')< >('')>

- Richard

---

### Post by sergiez on 2006-12-20
Yeah!!

I got sound!!! It is low, but it sounds enough to listen the music while working.

I just applied the patch (I really don´t know if I did it right) to the alsa drivers. Compiled it and installed it.

It looks like almost everything is running almost at 100% ;-)

---

### Post by daedius on 2006-12-20
w007@! =)  Congratz sergiez! I'm so excited, today I get my NEC ND-4570A  ( the true identiy of the sony super drive!)   I can't wait to burn up some Sabayon and boot it up. =P

---

### Post by sergiez on 2006-12-21
> **daedius said:**
> w007@! =)  Congratz sergiez! I'm so excited, today I get my NEC ND-4570A  ( the true identiy of the sony super drive!)   I can't wait to burn up some Sabayon and boot it up. =P

You will be able to boot from the Ubuntu edgy 64 bits alternate CD (I think you will be able to boot also form the liveCD) passing "irqpoll" to the kernel at boot time. At least I did it several times. It is quicker than booting with the sabayon liveCD (even stored in a separate HD partition). Maybe you prefer sabayon to ubuntu. Then it is OK ;-)

---

### Post by ububug on 2006-12-21
sergiez
could you describe a bit how you got sound working?
what kernel do you use? what patch do you use (there are 4 on the homepage linked above)?
sound is the only thing not working for me yet, and the patches dont work properly on kernel 2.6.19.1 for me
/thnx

---

### Post by sergiez on 2006-12-21
> **ububug said:**
> sergiez
could you describe a bit how you got sound working?
what kernel do you use? what patch do you use (there are 4 on the homepage linked above)?
sound is the only thing not working for me yet, and the patches dont work properly on kernel 2.6.19.1 for me
/thnx

I am using the kernel 2.6.19.1 
I used the last patch of the page aginst the alsa-driver-1.0.14rc1 driver.

If edgy is running fine for you with the 2.6.19.1 kernel:
1. download the driver from [here]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc1.tar.bz2")
2. Copy the patch file to the directory where the alsa driver has been uncompressed.
3. Apply the patch with the command "patch -p1 < MacPro.patch.bin "
4. Then configure and install the driver with the commands:
./configure
make
sudo make install
5. restart.

In fact the sound is very low. I have to turn high the wheel of my speakers almost to max to have a normal sound.

Note that I have the speaker conected to the analogic line in.

That's all!

---

### Post by daedius on 2006-12-22
> **sergiez said:**
> You will be able to boot from the Ubuntu edgy 64 bits alternate CD (I think you will be able to boot also form the liveCD) passing "irqpoll" to the kernel at boot time. At least I did it several times. It is quicker than booting with the sabayon liveCD (even stored in a separate HD partition). Maybe you prefer sabayon to ubuntu. Then it is OK ;-)


Hey their sergiez, =) are you saying you've had success with ubuntu 64- bit and NEC ND-4570A?  I unfortunately have had no luck with NEC ND-4570A and Sabayon.  I get the exact same messages I do with my Pioneer.

---

### Post by sergiez on 2006-12-22
> **daedius said:**
> Hey their sergiez, =) are you saying you've had success with ubuntu 64- bit and NEC ND-4570A?  I unfortunately have had no luck with NEC ND-4570A and Sabayon.  I get the exact same messages I do with my Pioneer.

Yes, at least with the edgy 64 bits alternate cd. I was not able to boot from the sabayon liveCD neither.

Try with edgy. The alternate CD was booting passing the "irqpoll" to the kernel (press F6 when grub appears at booting time and add irqpoll at the end of the kernel options line). Then you can install the system.

---

### Post by mflaig on 2006-12-25
Hi there,

I', running Edgy on the Macpro and Debian Etch. Both are amd64
My MacPro ist 
2 Dual Core Xeons at 2,66
2 x 250GB Disks (setup with Raid, LVM and DM_Crypt)
2048 Megs Ram
Radeon X1900
Sony DVD
Cinema (you know which one ;-))

What I know so far:
the ireason error is a problem with the sony dvd drive. It is fixed in 2.6.19.1 (debian etch with a custom kernel image works smoothly)

Edgy 2.6.17
- ireason problems with sony dvd
- installation from a external usb drive does work
- installation from sony dvd does not (at least for me)
- addititonaly the MacPro stops working frequently to think about 

Edgy 2.6.18
- When booting 2.6.18 gets drive seek errors and that was it. Will never come up

Edgy 2.6.19.1 (custom image)
- Working on an kernel package for 2.6.19.1 (debian package already done)
- One question: Where can I find information on how to build a linux kernel image the ubuntu way (means: which patches to use, how to get the bootsplash, etc.)

With Debian etch I had quite success, the kernel image of 2.6.19.1 works nicely. It is still missing patches from mactel-linux. Haven't checked if sound works corretly.

I'm still having a problem to get 2560x1600 resolutions with xorg to run on the ATI Radeon (fglrx is installed and kernel module present). If I start in 2560x1600 even with correct modeline for the cinema I get only 1280x800 :-( 

Anyone got ATI+Cinema working at 2560x1600?

My Debian kernel image and some additional notes can be found on [http://macpro.netzblock.org](http://macpro.netzblock.org)

Thanks,

Michael

---

### Post by daedius on 2007-01-02
I just wanted to be the first to notify everyone that I have successfully booted from live cd out-of-the-box no special configuration with Sabayon Linux 3.25 ([http://www.sabayonlinux.org](http://www.sabayonlinux.org))  ( with backports of PATA drivers from the 2.6.20 kernel -- among other great and wonderful things ).  I am running this on my Mac Pro with NEC ND-4570A CDROM drive.  Sound problems still exist, but as noted above, they are quickly on the way out to being solved.  Today is a great success for for free software and a great way to start off the new year.  Thank you to everyone for their support and effort!

---

### Post by sergiez on 2007-01-03
> **daedius said:**
> I just wanted to be the first to notify everyone that I have successfully booted from live cd out-of-the-box no special configuration with Sabayon Linux 3.25 ([http://www.sabayonlinux.org](http://www.sabayonlinux.org))  ( with backports of PATA drivers from the 2.6.20 kernel -- among other great and wonderful things ).  I am running this on my Mac Pro with NEC ND-4570A CDROM drive.  Sound problems still exist, but as noted above, they are quickly on the way out to being solved.  Today is a great success for for free software and a great way to start off the new year.  Thank you to everyone for their support and effort!

Great news!!

It is time to give Sabayone a chance, even if my Edgy is running great with the custom 2.1.19.1 kernel.

Thank´s daedius!!

---

### Post by daedius on 2007-01-10
Got sound working using the patch from the website [http://comments.gmane.org/gmane.linux.alsa.devel/42774](http://comments.gmane.org/gmane.linux.alsa.devel/42774) . Sound is still a little too soft =) and the headphones not working right.  But I did notice it was louder than it has ever been. =)  I mark this as a semi-success!

---

### Post by SRS2 on 2007-01-12
Hi all,

Im thinking about buying a Mac Pro to use as a home / dev server:

- Install 64-bit linux
- Install VM ware Server
- Run Windows XP or 2003 Server, Solaris etc. as virtual machines

This means that I dont really need graphics, audio etc, only basic functionality:

- Software RAID
- Dual boot - OSX and Linux
- ReiserFS
- USB, Firewire

Anyone know if this setup might work?

---

### Post by AntonioRubio on 2007-01-13
i've got my mac pro running nicely under the 2.6.15-27-686 kernel.  the on-board sound card doesn't work but i was able to get a USB soundcard working well (Creative Labs Audigy).

i worked off of [http://bin-false.org/?p=17]("http://bin-false.org/?p=17"), making appropriate changes for hardware.  if people are interested i'll post more details.

---

### Post by zbittner on 2007-01-16
I was able to get my Mac Pro to boot using the 6.10 live cds for both x86 and x86-64 (the only thing I had to do was type in the irqpoll command). There was more documentation on getting Intel Macs to boot using the 32 bit version, so I went with that, and was able to follow the directions, except when I pick the Linux partition in rEFIt, I get a blinking cursor, and then a message that says, "Unabe to load Operating System".

I had Mac OS X on the stock hard drive, and I was trying to run Linux and Windows on a second drive. I originally had Windows working through boot camp, but it stopped working. I got the same message from Windows that I did for Linux through rEFIt. Is this a problem with using two hard drives?

Anyways, I decided to put a Mac OS X boot partition on the second drive, and link the User stuff to my current user profile on the original drive. When I have time, I'll follow the triple boot instructions again, and see if I can get something working while triple booting from one hard drive.

I have no idea if my on-board sound card is working or not, but my USB speakers work fine.


I don't exactly know what I'm doing, so if someone who did could give me a few pointers, that would be greatly appreciated.

---

### Post by sergiez on 2007-01-17
> **AntonioRubio said:**
> i've got my mac pro running nicely under the 2.6.15-27-686 kernel.  the on-board sound card doesn't work but i was able to get a USB soundcard working well (Creative Labs Audigy).

i worked off of [http://bin-false.org/?p=17]("http://bin-false.org/?p=17"), making appropriate changes for hardware.  if people are interested i'll post more details.

Hi Antonio,

Yes, it is posible to instal older 32 bits ubuntu version on the Mac Pro. You will have no sound and the DVD drive will run but not fine.

We were having problems instaling 64 bits linux versions. Now the problem is known. There was problems with the older IDE/ATAPI drivers. New kernel versions solve this problems, but they are still not available for the stable ubuntu distro. So latest version of sabayon linux includes the most recent kernels and they boot from the Live DVD without problems (no irqpoll). There are patches to make the internal Intel HDA audio card run under linux. Link to it is posted in previous messages.

---

### Post by sergiez on 2007-01-22
Hi all!

God news also from ubuntu! 64bits of Feisty Herd 2 is able to be installed in the Mac Pro without problems. Everythings looks to run fine except sound (it should be patched).

Well, things are getting better.

---

### Post by incubus on 2007-01-28
> **sergiez said:**
> Hi all!

God news also from ubuntu! 64bits of Feisty Herd 2 is able to be installed in the Mac Pro without problems. Everythings looks to run fine except sound (it should be patched).

Well, things are getting better.

Hi sergiez,

Did you get everything else working?  What about the touchpad, the right click and scrolling?  Did you patch the ALSA drivers?  I'm thinking about following the same track you pursued, installing Ubuntu 64bit.

Thanks,
incubus

---

### Post by sergiez on 2007-01-29
Hi incubus,

Note that the Mac Pro is a tower computer. It has not touchpad. There is no problems with the mighty mouse and the right click, but scrolling using the little ball is not running. Sound is working just downloading and installing the last alsa drivers.

But I think you ask for an Apple laptop, isn´t it? so you are in the wrong thread.

---

### Post by sjatkins on 2007-03-02
Please give the details of exactly how to bypass the cd by using dd, iso to dmg or whatever to boot from something other than cd.  The above claim is not easy to parse.   Thanks.

---

### Post by ssergio on 2007-03-03
Hi

I'm new to Linux in general.
I've made an install of Feisty Herd 4. I chose to install it on one of the 4 hard drives in my Mac Pro (2 HFS+, 1 NTFS XP, 1 dedicated to Linux). The problem is I don't know how to boot it since bootcamp doesn't see it as a bootable disk. What is the right way to do it ?

Thanks for your help

---

### Post by sergiez on 2007-03-03
Hi ssergio!

That's easy! Just reboot and keep pressed the key ALT.

---

### Post by sjatkins on 2007-03-03
> **daedius said:**
> I just wanted to be the first to notify everyone that I have successfully booted from live cd out-of-the-box no special configuration with Sabayon Linux 3.25 ([http://www.sabayonlinux.org](http://www.sabayonlinux.org))  ( with backports of PATA drivers from the 2.6.20 kernel -- among other great and wonderful things ).  I am running this on my Mac Pro with NEC ND-4570A CDROM drive.  Sound problems still exist, but as noted above, they are quickly on the way out to being solved.  Today is a great success for for free software and a great way to start off the new year.  Thank you to everyone for their support and effort!

That is pretty darn odd.  I try installing the same thing on a Mac Pro that is brand new and it fails on mounting the cdrom just like all the other distros I have tried.  I am beginning to wonder if Apple made it difficult to install linux on the hardware (directly) on purpose.  I have been fighting with this for an outrageous amount of time now.  I tried Ubuntu on a netboot from a USB stick but it did not want to deal with that either.  Very odd and starting to really tick me off.

---

### Post by ssergio on 2007-03-04
sergiez

That's what I did, I pressed the Alt Key. I even tried rEFIt but it didn't work.
the Alt key didn't see my Linux hard drive and rEFIt sees several Linux bootable partitions but GRUB doesn't start. I must have done something wrong ... might the partitioning under OS X.
Now I have two HFS disks and two free disks. How to configure one of them to be able to install lInux on it and easily boot it. I've tried UBuntu, SLED and Fedora without sucess.

---

### Post by sergiez on 2007-03-05
> **ssergio said:**
> sergiez

That's what I did, I pressed the Alt Key. I even tried rEFIt but it didn't work.
the Alt key didn't see my Linux hard drive and rEFIt sees several Linux bootable partitions but GRUB doesn't start. I must have done something wrong ... might the partitioning under OS X.
Now I have two HFS disks and two free disks. How to configure one of them to be able to install lInux on it and easily boot it. I've tried UBuntu, SLED and Fedora without sucess.

Well... first of all, did you install boot camp? I supose the answer is yes.
Did you finish the installation of Ubuntu Feisty without errors?
Did you sincronize the partion table with with rEFIt?
So you have 4 physical dsiks on your MacPro and you are trying to install ubuntu in the third one, isn´t it? When trying to boot from one of the penguined partitions with refit, which is the error message it tells yo? Something like "there is no operating system"? or it just hangs?

In my case, my ubuntu is installed in the first partition of the second physical disk. Even that, GRUB was not able to boot the linux system untill  I modified it. I had to edit /boot/grub/menu.lst and change the lines "root (1,0) to root (0,0) as if linux was in the first physical disk. Then it boots without problems.

I don´t know why it happends. I also have noted that disk0s0 or disk0s1 or disk1s0... is changing in Mac OSX as well, but no problems to boot OSX.

---

### Post by sergiez on 2007-03-05
> **sjatkins said:**
> That is pretty darn odd.  I try installing the same thing on a Mac Pro that is brand new and it fails on mounting the cdrom just like all the other distros I have tried.  I am beginning to wonder if Apple made it difficult to install linux on the hardware (directly) on purpose.  I have been fighting with this for an outrageous amount of time now.  I tried Ubuntu on a netboot from a USB stick but it did not want to deal with that either.  Very odd and starting to really tick me off.

Did you try with the LiveCD of the Ubuntu Feisty Herd 5? It has also the kernel 2.6.20 and it is booting my Mac Pro without problems.

Try and tell us!!

---

### Post by zbittner on 2007-03-07
Has anybody been able to triple boot on their Mac Pros. I have the SONY optical drive with the default SONY firmware(the region free NEC firmware seemed to cause problems). I tried Edgy a few weeks ago, and whenever I installed it following MacBook/MacBook pro triple boot instructions (with lilo) it wouldn't boot, and it would break my Windows install.

Drive Bay 1:
232.6 GB HFS+ Partition (OS X Boot disk)
Drive Bay 2:
74 GB HFS+ Partition (Extra room for media stuff)
74.7 GB NTFS Partition (XP)

I currently have Windows installed (via bootcamp) on a partition on a second HDD, and I'd like to take 20 GB out of my Windows partition and install Ubuntu(Feisty), but I have a few questions.

1. Is this possible?
2. Does the new version of GRUB support the EFI?
3. Which drive should I have GRUB install on(The one I'm installing Linux on(HD1), or my OS X drive HD0)?
4. Should I just yank my OS X drive out before installing it?
5. Should I use the 32 bit version of Ubuntu, or is there adequate driver support for the AMD64 version?
6. I already have rEFIt installed on the drive I boot OS X from. Should I remove it and install it on my HFS+ partition on the drive I'm installing Linux on?

I'm a bit of a linux newbie, but after playing around with it in VMWare, I would like to try a real install.

If I need to wipe my Windows partition, I don't really care. All I use Windows for now is playing X3, and that is coming to Linux.


I have a pair of USB speakers (Harman/Kardon Soundsticks) and they work fine with the live CD. A lot of companies make USB headsets, so if there is a problem with the audio chipset drivers, the easiest thing to do seems to be to bypass it.

Edit: Will I still need to type in irqpoll to boot from a live cd?

---

### Post by sergiez on 2007-03-07
1. It is possible to triple boot using bootcamp.
2. No. Grub does not support EFI but... you are using bootcamp so... there is no problem. I have noted and improve in the Grub version of Feisty. It is not guving errors during installation anymore. I thought the problem before was with the MBR and GRID (or somthe like this) kind of partition tables. Even that, booting from boot is still giving some problems as I described few posts before this.
3. I thing it does not matter. I have it in the second one.
4. It is not necesary. But may be will be better if you do it.
5. For a linux newbie I think is better to use 32 bit versión. You will have more available software.
6. No. In fact, rEFIt is not needed. But if you have it installed, keep it like it is.

The problem with the sound looks like will be solved in next Feisty previews. But is good to know that are other solutions.

---

### Post by zbittner on 2007-03-07
I pulled my OS X drive, and booted using the Live CD. When I try resizing my NTFS partition in gparted, it fails, and it says check filesystem for errors. I rebooted my computer, and without the OSX drive in, it went right into Windows, and found problems with the filesystem on boot so it fixed them and restarted where I then held down C to boot back onto the live cd, and I tried resizing the partition again and got the same message. I'm going to shut down, put my main hard drive back in, and see if I can get stuff sorted out.

Edit: Problem solved (in a sense). I tried again, and gparted destroyed my windows partition while attempting to resize it. Now I have 2 working Fat32 partitions to work off of.

Edit 2: I couldn't get Linux to boot even after changing the menu file. Anyways, I'm back to having both drives formatted as HFS+ Drives.

Sergiez, did you have both Windows and Ubuntu installed, or just Ubuntu, and to get Ubuntu to work, did you just use Boot Camp to partition your drive and to start the installer(as if it was Windows)? Thanks for your help.

---

### Post by sergiez on 2007-03-08
zbittner: I have 3 OS in the Mac Pro (OSX, Windows and Ubuntu). Which is the Grub error message you get when booting?. I assume that you can see the message Bootin grub... if not just let me know.

You said that you change the lines in the menu.lst file of your installed system, so Ubuntu was correctly installed. But I don´t understand why finally you have 2 fat32 partitions. At least one of them must be typed as a linux partition (not FAT32). May be the problem is there. You can check this point with gparted and change the partition type using fdisk.

---

### Post by ssergio on 2007-03-08
Hi sergiez

Bootcamp is installed.
I've tried Feisty Herd 5. This time, the installation finished with an error trying to remove some sort of mouse package at 98%. Anyway, I installed rEFIt on one of my HFS hard drive, tried to boot the Linux HD partition and got a "no bootable partition" message.
What do you mean by synchronizing the partition table with rEFIt ? How do you do this ?

I then boot from the CD again and below is my /boot/grub/menu.lst file

title		Ubuntu, kernel 2.6.20-9-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-9-generic root=UUID=7388e9d9-6a70-4a46-b9d9-d59b29e87d4f ro quiet splash
initrd		/boot/initrd.img-2.6.20-9-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-9-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-9-generic root=UUID=7388e9d9-6a70-4a46-b9d9-d59b29e87d4f ro single
initrd		/boot/initrd.img-2.6.20-9-generic

title		Ubuntu, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

Thanks again for your help

---

### Post by sergiez on 2007-03-08
ssergio: 
To sync the partion table with rEFIT you must acces to the partitioning tool in the refit menu. Then say yes to sync.
did you check if grub was installed during the installation?
The menu.lst file is the one placed at /boot/grub directory of the first partition on your 4th physical disk? If so try changing "root (hd3,0)" to "root (hd0,0)".

If grub was not installed try booting again from the LiveCD and from a terminal type:
- sudo mkdir /mnt/ubuntu
- sudo mount /dev/sda3 /mnt/ubuntu/
- sudo mount -t proc none /mnt/ubuntu/proc
- sudo mount -o bind /dev /mnt/ubuntu/dev
- chroot /mnt/ubuntu /bin/bash
-grub-install /dev/sda (may be /dev/sdd will work better to install grub on the mbr of the 4th disk. Other option is try with /dev/sdd0 to install it in the boot sector of the first partition of the 4th disk).

Then try to reboot and select the linux partition. If Grub boots but shows an error message (a message from grub, not from you Mac Bios/EFI) then change again your menu.lst file will be necesary.

I hope it will help.

---

### Post by zbittner on 2007-03-08
I just split a fat32 partition into 2 fat32 partitions.

I ended up getting rid of everything and starting over. I broke 60 GB off with bootcamp and installed Linux. I restarted but the cd didn't eject, so it restarted back to that so I chose boot from first hard drive, and the three options came up, but it wouldn't boot. I was able to edit the configuration, and saw the line Root(1,3). I changed it to Root(0,3) and it booted fine. I'm in Ubuntu now doing updates. After the updates finish, I'll reboot and see if I can boot from rEFIt to Ubuntu.

Can I just use gparted to create room for Windows?

Edit: I installed Beryl and the NVidia drivers, but it doesn't let me set my resolution to 1440x900, my panel's native resolution. My other question is about screen spanning. Is there an easy way to do this?

Edit2: After booting back up in OS X, and then trying to boot back into Linux, I get the "Missing Operating System" message right after selecting that drive to boot from. GRUB doesn't even begin to load. I went into rEFIt and according to it, the partition tables are already synced. I reinstalled GRUB, but that didn't do anything.

---

### Post by sergiez on 2007-03-09
zbittner: Well, at least you have booted once in ubuntu! You are in the right way!

1. Remember: You must check your menu.lst file every time you update the system. In case there is a Kernel uptade, ubuntu will reinstall grub and it will update the menu.lst file. Take this in account.

2. You can create fat32 partitions with gparted without problems. And resize them and a lot of things more.

3. May be you will need to modify the /etc/X11/xorg.conf file in order to achieve resolution of 1440x900. If you don´t find the way I will look for it later (now I don´t have any xorg.conf file to check it). I don´t know anything about screen spanning. Sorry.

4. Be sure that menu.lst file is correctly modified. Then try booting without rEFIt. Just press key ALT at boot time. It will show the bootcamp boot menu. If you have OSX, Windows and Linux installed it must show you 3 big hard drive icons. 2 of them will have the name "windows". One of them will be your Linux booting partition. Try it. In case bootcamp menu does not show you the big windows hard drives or only the windows installation, then is possible that the partition type where linux is installed is wrong. You can check this with Disc Utility in your OSX or with gparted in the ubuntu LiveCD. Try to be sure that this partition type is a Linux one.

---

### Post by ssergio on 2007-03-09
Hey Sergiez

Happy to report that I now have an Ubuntu bootable partition, no need to go through rEFIt to boot it. What is weird is I am able to boot it from the bootcamp menu, not from the rEFIt menu. Anyway, it does'nt matter after all.

Two more things  :-) (no Jobsian announcement here)
The 7300 GT doesn't seem to be recognized (1024x768, very slow windows movement, ). Where can I get this driver ?
Is there a way to get the root under Ubuntu, I indeed might to install stuff (SAP) that might need root access. Is there a 1.4.2 or later JVM available for Ubuntu ?

Thanks again

Serge

---

### Post by zbittner on 2007-03-09
You need to get the NVidia drivers which I'm pretty sure you can get them through apt-get(synaptic package manager?).

GRUB doesn't load for some reason. I'm not sure linux is even showing up in the default bootloader. rEFIt shows Mac OS X, something called "Legacy OS"(Which also gives the missing operating system message), and Linux, but bootcamp only shows two bootable drives.

---

### Post by sergiez on 2007-03-09
Hi ssergio!

Great news! I am not using rEFIt. I found it slow and a little bit confused. Depending on the quanity of partitions it shows dozens of penguins!!

Well, now you have minor problems. In order to install the nvidia driver you must be sure that linux-restricted-modules and nvidia-glx packages are installed in your system. You can do it via synaptic or apt-get. Remember that Ubuntu has no root user enabled. In fact it runs as OSX. When a user has administrator account jus has to type the user password in order to act as root.

Something like this:
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by sergiez on 2007-03-09
> **zbittner said:**
> You need to get the NVidia drivers which I'm pretty sure you can get them through apt-get(synaptic package manager?).

GRUB doesn't load for some reason. I'm not sure linux is even showing up in the default bootloader. rEFIt shows Mac OS X, something called "Legacy OS"(Which also gives the missing operating system message), and Linux, but bootcamp only shows two bootable drives.

It looks like the partition type where ubuntu is installed is not set as linux type. Did you chek it in Disk utility? May you can try disconecting the rest of disks and reinstalling ubuntu using only the disk in where it will be installed. One finish, reboot and see. If everything is OK, then connect the rest of the disks again and try booting via bootcamp or refit. I know that this is not a good solution, but may be as last chance...

---

### Post by zbittner on 2007-03-09
In Disk Utility, it says the partition is Microsoft Basic Data, which doesn't seem right.

---

### Post by zbittner on 2007-03-11
I decided to try the 64 bit version for the heck of it. I took out my hard drive with OS X, and installed Ubuntu. When I restarted, I held down alt, and all that showed up was the cd. The partition with Linux on it doesn't show up.

I am able to choose "Boot from first Hard Drive" from the live cd, and it boots right up so I know the install works, but booting from the live cd every time I want to use Linux isn't the best solution.

---

### Post by sergiez on 2007-03-11
A lot of extrange things are happening in your boot camp menu!

Did you try conecting your OSX drive again in the first physical conection? I don´t know how important is for boot camp to find the OSX system in order to boot correctly. Did you try to boot with ubuntu disk only conected and without pressing ALT key?

---

### Post by sameo on 2007-03-21
I have a 2x2.66 Ghz, 250 Gb, Nvidia graphics macpro, and I just wanted to let you guys know that I succesfully installed **feisty 5 **on it.
By succesfully, I mean no boot options, no tweak, no extra lilo install. It all went very smoothly. Very nice work from the Ubuntu installer team.

---

### Post by zbittner on 2007-03-24
I am extremely close to getting this to work. Now I can boot into the live cd and choose the option to boot from first hard drive, and GRUB will pick up, but the partition does not show up when I hold alt, and trying to boot it from rEFIt gets me stuck at a white screen. REFIt claims the partition tables are synced. GRUB and Linux are both on the second drive.

---

### Post by sergiez on 2007-03-24
zbittner: It looks like something is wrong woth boot camp.

Sorry, but I am lost :-(

---

### Post by resistor2004 on 2007-04-02
Has anyone experienced a total lack of sound?  lsmod shows 'snd_hda_intel' running, and I have the latest kernel, etc.  I've check the mixers I could find (the Sound preference pane, the Volume adjuster in the sytem tray), but I can't get anything to come out.

Any ideas?

---

### Post by cyberdork33 on 2007-04-03
> **resistor2004 said:**
> Has anyone experienced a total lack of sound?  lsmod shows 'snd_hda_intel' running, and I have the latest kernel, etc.  I've check the mixers I could find (the Sound preference pane, the Volume adjuster in the sytem tray), but I can't get anything to come out.

Any ideas?

Did you mark "Line In as Output"?

[http://www.ubuntuforums.org/showthread.php?t=393015&highlight=Sound](http://www.ubuntuforums.org/showthread.php?t=393015&highlight=Sound)

alsamixer will show ALL the switches, try that too.

---

### Post by resistor2004 on 2007-04-04
I don't have an option in my Switches tab for that.  I tried unmuting/maxing the volume of everything in alsamixer to no avail.  I don't know how to find the "Line In as Output" option in it, though.

---

### Post by sergiez on 2007-04-04
> **resistor2004 said:**
> I don't have an option in my Switches tab for that.  I tried unmuting/maxing the volume of everything in alsamixer to no avail.  I don't know how to find the "Line In as Output" option in it, though.

The problem with the sound in the Mac Pro is a known issue that has been reported to the Ubuntu developers. In fact it depends on the kernel. The patch for the alsa driver is summited but it is not in the linux kernel yet. If it is not in the kernel at freeze time of ubuntu 7.04 we will be forced to install de alsa driver from source.

The current situation is that there is sound in the Mac Pro in ubuntu Feisty beta, but at a very low level. Try to put your speakers at full level. You will have sound and even you can listen music at night :-)

Be patient or try install the [alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2") from the alsa project page and tell us...

---

### Post by cyberdork33 on 2007-04-04
My apologies... works on all the other Macs...

---

### Post by resistor2004 on 2007-04-04
> **sergiez said:**
> 
The current situation is that there is sound in the Mac Pro in ubuntu Feisty beta, but at a very low level. Try to put your speakers at full level. You will have sound and even you can listen music at night :-)


Actually, I'm using Feisty beta, and I'm not getting any sound, even quiet sound.  Everything is maxed/unmuted in alsamixer, and my speakers are all the way up.

---

### Post by sergiez on 2007-04-10
> **resistor2004 said:**
> Actually, I'm using Feisty beta, and I'm not getting any sound, even quiet sound.  Everything is maxed/unmuted in alsamixer, and my speakers are all the way up.

Ups. I forgot to tell you that you must open the mixer and turn on your "surround" level. The sound is there.

Has someone try with the latest alsa drivers installed by hand?

As last kernel series of feisty have problems with the Mac Pro I will wait until RC appears in order to check if the problem with the sound is solved.

---

### Post by mflaig on 2007-04-11
Hi folks,

I just wanted to mention, that there is a patch for the sound driver available from alsa.
And since 2.6.21rc4 this driver is also in the Mainstream Kernel Development.

I'm using a self compiled 2.6.21rc6 and sound is alright. Correct Mixer for analog audio output would be front. without the proper patch it is surround. Ubuntu does not have 2.6.21 and I doubt that 2.6.21 will make it into Feisty. Maybe later.

If you want debian packages of a kernel 2.6.21rc6 that works (incl nvidia drivers) please reply. I would put it on my website ... 

I most certainly cannot help people with an ati graphics card. 
fglrx won't compile but if someone has ATI please say so, i will check if my bugreport has been even assigned after 4 month now and try to compile fglrx modules.

If you have ATI and want after nearly 1 month of trying to get it to run on 2560x1600


Michael

---

### Post by tretlo on 2007-04-12
I have followed the advice on this thread, which led me to install Sabayon rather than Ubuntu. It is now working great except for the sound. It seems like I'm having the same audio problem as other people people here.
I'm using alsa-driver-1.0.14_rc3.
I  have sound, but it is very, very quiet. In my case, it is not usable. Does anyone actually have proper, full-volume sound using the hda-intel alsa module? If so, how did you configure it. In alsamixer, I don't have any "surround" options. The "Front" channel controls the volume I hear, and only at the maximum setting can I hear anything at all.

I would love to be using linux full-time on this machine. Sound is the only major thing stopping me. Any advice?

Some useful info:
# cat /proc/asound/devices 
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 26: [ 0- 2]: digital audio capture
 33:        : timer

# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x92f00000 irq 23

# lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)

---

### Post by JayRx1981 on 2007-04-12
I've got sound working through the TOSlink out port, but I had to switch the default mixer from ALSA to the ALC885 OSS mixer and enable the Digital1 port to get it to work. I've had no luck with the ALSA driver on it's own.

Correction: I got it working through ALSA as well by enalbing the IEC958 switch. NONE of the volume controls work through this method, but given that i've got the TOSlink out going into my sound system and it's controlling volume for me, I'm cool with that, I guess. :P

---

### Post by tretlo on 2007-04-12
Thanks for the advice JayRx. I bet that would work for me...if I were using the digital out. But unfortunately I'm just listening on headphones in my office.

Anybody have analog outs working well?

---

### Post by sergiez on 2007-04-13
Hi all,

Bad news:
Just to inform you that there is a acpi kernel bug in the latest kernel released with Ubuntu Feisty Beta and on (2.6.20-13 and 2.6.20-14). This is a critical bug that makes the Mac Pro system unboteable.

It looks like it won´t be solved for the final release of Feisty. It means that it won´t be possible to install the next release of ubuntu if the bug is not solve in the comming days.

---

### Post by sergiez on 2007-04-13
> **sergiez said:**
> Hi all,

Bad news:
Just to inform you that there is a acpi kernel bug in the latest kernel released with Ubuntu Feisty Beta and on (2.6.20-13 and 2.6.20-14). This is a critical bug that makes the Mac Pro system unboteable.

It looks like it won´t be solved for the final release of Feisty. It means that it won´t be possible to install the next release of ubuntu if the bug is not solve in the comming days.

The acpi bug has been solved and now kernel 2.6.20-15 runs on Mac Pro. But sound has not been patched.

---

### Post by spdorsey on 2007-04-14
I'm looking forward to trying out Ubuntu on my new 8-core Mac Pro. It arrives on Wednesday, April 18. 

  I'll be installing the 64-bit version, if possible. Mainly for Maya work. I want to use Maya in 64-bit, and that's not gonna happen in Windows. OS X Maya is an odd beast.

  I've been following this thread, and I'm eager to see these audio problems solved. I hope this installation is not over my head!

Thanks,

-----------------S

---

### Post by sergiez on 2007-04-14
> **spdorsey said:**
> I'm looking forward to trying out Ubuntu on my new 8-core Mac Pro. It arrives on Wednesday, April 18. 

  I'll be installing the 64-bit version, if possible. Mainly for Maya work. I want to use Maya in 64-bit, and that's not gonna happen in Windows. OS X Maya is an odd beast.

  I've been following this thread, and I'm eager to see these audio problems solved. I hope this installation is not over my head!

Thanks,

-----------------S

8-core!! such a beast machine!!
I don't know if the 8-core Mac Pro has many differences in front of the classical 4-core. If there are not too much differences everything will run quite well. I hope you report back your experiences with Maya under Ubuntu 64bits.

The problem with the sound is still there and I don know if will be solved for the Feisty final relase. Ubuntu Feisty will have the 2.6.20 kernel and, if I am not wrong, the problem with the sound is solved at 2.6.21 kernel series. In the [bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/89980") about this issue openened at launchpad is not clear if the ubuntu team will patch the 2.6.20 kernel, but is very simple to solve the problem installing the alsa driver by hand. I did it this mourning and sound works great now.

Enjoy your super-machine!!

---

### Post by spdorsey on 2007-04-14
Thanks!

  I'll be reporting back with Maya updates - I expect it to be VERY difficult to install. The last time I tried was Maya 5 on RedHat, and I never got it working. I hope that it works better this time around. I'll be installing Maya 8.5 on the latest 64-bit Ubuntu that I can find.

  I have heard that Autodesk has support for installation. I may be calling them for help. We'll see.

-------------------S

---

### Post by tretlo on 2007-04-18
I have tried installing alsa-driver-1.0.14rc3 both from a package and compiled from source, but both ways I have the same problem: very quiet sound. Could this be a problem with my alsa configuration files? Is anyone using a special .asoundrc?

Sergiez, since you seem to have sound working well, is there any chance you could post your .asoundrc?

Really want to get this to work...

---

### Post by sergiez on 2007-04-18
tretlo: Yes, it is working!
Did you follow these steps?
Download the ALSA driver archive (you won't need alsalib or alsautils) from the ALSA site ([ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2)](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2)). Extract and build the drivers for just the hda-intel card:

% tar xvjf alsa-driver-1.0.14rc3.tar.bz2
% cd alsa-driver-1.0.14rc3
% ./configure --with-cards=hda-intel
% make -j 8
% sudo make install

If so then you must double check your alsa values. Maybe you have a wrong selection for the output.

Where is supose to be this .asoundrc file? I did not find it in my home dir.

---

### Post by tretlo on 2007-04-18
> **sergiez said:**
> tretlo: Yes, it is working!
Did you follow these steps?
Download the ALSA driver archive (you won't need alsalib or alsautils) from the ALSA site ([ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2)](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2)). Extract and build the drivers for just the hda-intel card:

% tar xvjf alsa-driver-1.0.14rc3.tar.bz2
% cd alsa-driver-1.0.14rc3
% ./configure --with-cards=hda-intel
% make -j 8
% sudo make install

If so then you must double check your alsa values. Maybe you have a wrong selection for the output.

Where is supose to be this .asoundrc file? I did not find it in my home dir.

Yes, I followed those steps exactly. Still only very quiet sound. (I should probably mention again that I am using Sabayon, not Ubuntu, but I don't think this should really matter, should it?)

On my system I have neither ~/.asoundrc or /etc/asound.conf. I only have /etc/asound.state. I don't understand the architecture of alsa well enough to know why. But if you have either of these files, maybe that could help me solve my problem.

Thanks for your help!

---

### Post by tretlo on 2007-04-18
Also, I just compiled a brand new 2.6.20.7 kernel, but I'm still having the same problem.

---

### Post by spdorsey on 2007-04-19
Well,

  the 8-core is CRAZY fast! It boots into OS X in 10 seconds from pressing the power button to the Desktop. Simply amazing.

  I'm having a hard time getting the triple-boot to work. I'm uaing a tutorial at:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

  But I don't wat to use three partitions, I have three internal hard drives, and I want to use one each for OSX, Windows, and Ubuntu. The main problems involve formatting the hard drives (that's as far as I got). In the tutorial, they use diskutil in the OS X terminal to format the partitions before installing Linux and Windows. 

  Apparently, diskutil will not aloow me to format partitions larger than 100GB. My hard drives are both 300GB (275 useable), so I'd be giving up mots of space on each drive.

  Can anyone point me to a better tutorial for doing this? I'm afraid I need more specific instruction.

Thanks,

-----------------S

---

### Post by sergiez on 2007-04-19
> **tretlo said:**
> Also, I just compiled a brand new 2.6.20.7 kernel, but I'm still having the same problem.

Kernel 2.6.21 Vanilla has the correct versión of the alsa driver ready for the MacPro. You can try with this one.

Sorry tretlo, I can't find this file on my system.

---

### Post by sergiez on 2007-04-19
> **spdorsey said:**
> Well,

  the 8-core is CRAZY fast! It boots into OS X in 10 seconds from pressing the power button to the Desktop. Simply amazing.

  I'm having a hard time getting the triple-boot to work. I'm uaing a tutorial at:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

  But I don't wat to use three partitions, I have three internal hard drives, and I want to use one each for OSX, Windows, and Ubuntu. The main problems involve formatting the hard drives (that's as far as I got). In the tutorial, they use diskutil in the OS X terminal to format the partitions before installing Linux and Windows. 

  Apparently, diskutil will not aloow me to format partitions larger than 100GB. My hard drives are both 300GB (275 useable), so I'd be giving up mots of space on each drive.

  Can anyone point me to a better tutorial for doing this? I'm afraid I need more specific instruction.

Thanks,

-----------------S
I don't thing you need to make and format partitions using disk utility of OSX. In fact you only need to install boot camp and select the hole drive where windows will be installed. In order to install Ubuntu just put the ubuntu liveCD (or alternateCD if you have wireless mouse and keyboard), reboot pressing the "ALT" key, select to boot from the CDROM and proceed with the installation as usual (assuming you are installing Feisty).

You should make partitions under Ubuntu or Windows during the installation process.

8-core Mac Pro... lucky you!!

---

### Post by ZacharyPruckowski on 2007-08-19
> **sergiez said:**
> I don't thing you need to make and format partitions using disk utility of OSX. In fact you only need to install boot camp and select the hole drive where windows will be installed. In order to install Ubuntu just put the ubuntu liveCD (or alternateCD if you have wireless mouse and keyboard), reboot pressing the "ALT" key, select to boot from the CDROM and proceed with the installation as usual (assuming you are installing Feisty).

You should make partitions under Ubuntu or Windows during the installation process.

8-core Mac Pro... lucky you!!

Hi.  My problem is sort of like his problem.  I have 4 HDDs, divided thusly:

A+B = 160 GB drives in a RAID 0, HFS+.  This is my Main Mac Partition with the OS install and applications
C = 250 GB, divided about 160ish NTFS and 70ish HFS+.  I want Linux on this HFS+ partition.
D = larger media drive (400 GB).  HFS+, no OS loaded.  Contemplating removing journaling to enable Kubuntu to read.

I tried when I first got the computer (a year ago) to install Dapper Drake, hit the DVD drive issue, and gave up for a little while.  I wound up installing 6.10 in a VM briefly.

I just tried to install 7.04, but when I ran the installer, it crashed as it was loading the partitioner.  It threw up a warning about hde having sector size of 2048 or something and then stopped with the partitioner at 38 percent.

This was with the alternate install CD, and I had to burn it to a DVD-R (because that's all I had laying about).

Any ideas as to what I should do (ideally not involving nuking the Windows partition).

---

### Post by sergiez on 2007-08-19
Looks like Ubuntu have problems with the Raid in the first 2 disks. I really don´t know how you can solve this issue. Maybe you can report the problem as a bug at Launchpad or look for a solution in the bug tracker.

Maybe you can try disabling first two disks (I mean physically disconnecting them), install ubuntu where you want and the connecting again the disks.

I don´t think is possible to install ubuntu on a HFS+ partition. EXT3, XFS or other linux native filesystems needed. Also I think is not necessary to remove journaling in a HFS+ partition in order to be readable for linux. At least I don´t need it. So you neither.

---

### Post by Maverick88 on 2007-09-25
Good News!!

Yes, you can get Linux to work on a Mac Pro but there are some hurdles you must overcome especially if your Mac Pro came with Pioneer DVD drives!  

If your Mac Pro uses SONY DVD drives, then you should not have any problems, booting from any modern Linux LiveCD.  My first Mac Pro had Sony Drives and was able to boot the Ubuntu LiveCD (and the LiveCD for my favourite disto for development, Arch Linux) without any problems.  

But if your Mac Pro came with Pioneer DVD Drives, you will not be able to boot a LiveCD Successfully.  Apparently, If you have a Pioneer dvdrom, the current drivers have problems with the emulated bios drivers for the cdrom,  When you try to boot from Pioneer drives one of two things happens:

1)  You see a nice blank grey screen and hear the disk spinning.  About 20 seconds later, the Mac Pro spits out (ie ejects) the LiveCD.  And about 5 seconds later, the Mac Pro boots into Mac OS X.

OR

2) You get to see the LiveCD boot Menu.  When you choose to run the LiveCD, it loads the kernel but gets hung up when it tries to load the CD/DVD Modules (or drivers).

I have seen both problems on my replacement  Mac Pro from Apple that came with Pioneer drives.  There are two known workarounds:

Option 1:
burn the amd64 iso image to a hardware partition (or USB drive)
burn the amd64 iso image to a cd
boot off the cd
the computer will be tricked into using the hardware partition image

Optione 2:
Or simply boot off an external usb cd/dvd drive. 

For more info, see the GENTOO wiki which has the most extensive info on using the Mac Pro on Linux.   see [http://gentoo-wiki.com/MacPro](http://gentoo-wiki.com/MacPro).

I hope this helps.  Please let me know  whether you were successful and what tricks you needed to do to get Ubuntu running on your Mac Pro.

Maverick
P.S.  The main developer for SimplyMEPIS, Warren uses a Mac Pro for his main development machine but I suspect his Mac Pro came with Sony Drives!

---

### Post by nikitavfx on 2007-10-29
Check out [http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/) for some howtos about getting Ubuntu Gutsy running on the Mac Pro.

There's a post about compiling a custom 2.6.23 kernel with the mactel patches there, too.

---

### Post by darkstr2o4 on 2008-02-24
I just got a new mac pro and it installed easily with the 64 bit version. How do i know if I have thermal support though? I DON"T want to fry this thing.

---

### Post by metallicamaster3 on 2008-02-24
The PowerMac G5s were one thing with Linux, having trouble with the kernels and whatnot, because they were/are different processor architectures and were just... well different and linux wasn't friendly.

The newest Mac Pros shouldn't really have any problems except for perhaps some addressing issues due to the 8 cores with the dual quads. 

They are 64-bit Xeons, so there should be a pretty good chance of linux working without a hitch. I have not gotten myself the newest one net, hopefully it will be my next purchase sometime in the upcoming months.

---

