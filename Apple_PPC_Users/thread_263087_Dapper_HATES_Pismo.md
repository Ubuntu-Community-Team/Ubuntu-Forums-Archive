---
title: "Dapper HATES Pismo"
date: 2006-09-22
forum: Apple PPC Users
---

### Post by KesslerB on 2006-09-22
This is long -- please bear with me.  I'm going to be very explicit here to show that I've been through the forums, I've Googled the Web, and I do have a clue, and am still utterly unsuccessful when it comes to installing Dapper onto my Pismo.

Starting from scratch, I've erased my entire hard drive, repartitioned it as desired, and have already installed two Apple-supplied operating systems, so I know the hardware is fine.

I downloaded Dapper version 6.06.1 for the PowerPC earlier today using a PC.  I successfully burned the ISO image (not the ISO file itself) onto a blank CD-R.  When I insert the CD into the DVD-ROM in my Pismo, I can browse the directory tree, including seeing the INSTALL directory and the YABOOT files therein, etc.  The label on the disc is "Ubuntu_PowerPC_dapper", using 738,250,752 bytes; the root of the disc has 8 folders and 2 files, including the "md5sum.txt" file.)

I double check and see that of my 60GB hard drive, I have a 1GB partition named CLASSIC with OS 9.2.2 installed, a 40GB partition named TIGER with 10.4.7 installed, and the remainder (around 19GB) is available space (for Dapper).

I reboot the machine while holding down the C key so as to boot off the CD-R.  No dice; it takes me right into Tiger.

So I reboot the machine with the CD in and hold down the OPTION key.  I get the blue boot disk selection screen, and it shows me my CLASSIC and TIGER partitions, and a few seconds later, a CD icon with Tux in the lower right corner. Pismo sees the CD-R I'd burned and can read it.

Now I select the CD-R and click the right arrow to start the boot process from the CD-R.  My screen goes blank, and that's the end.

I've tried this with the same results using the original 6.06 version, the Alternate Ubuntu disc, an XUbuntu CD, and even the Ubuntu Server disc, all with the same results.

I've zapped the PRAM.  No difference.

I've booted into Open Firmward (CMD-OPT-O-F), and entered
[INDENT]0 > boot cd:,\install\yaboot[/INDENT]
and am always greeted with
[INDENT]can't OPEN: cd:,\install\yaboot[/INDENT]
so that doesn't work either.

I've tried connecting an external DVD+-RW drive via the built-in USB, but Pismo doesn't support booting from that.

So now I'm stumped.  Here's some additional details about my hardware according to System Profiler under 10.4.7 (edited and reformatted for clarity and brevity):

[INDENT]Machine Mode:      PowerBook3,1[/INDENT]
[INDENT]CPU Type:          PowerPC 750 (83.0)[/INDENT]
[INDENT]CPU Speed:         500 MHz[/INDENT]
[INDENT]Memory:            1 GB[/INDENT]
[INDENT]Boot ROM Version:  4.1.8f5[/INDENT]
[INDENT]Optical Drive:     LG DVD-ROM DRN-8080B[/INDENT]
[INDENT]__Firmware:          2.03[/INDENT]
[INDENT]Video Chipset:     ATY,RageM3[/INDENT]
[INDENT]__VRAM:              8MB[/INDENT]
[INDENT]__Device ID:         0x4c46[/INDENT]
[INDENT]__Revision ID:       0x0002[/INDENT]
[INDENT]__ROM Revision:      113-XXXXX-119[/INDENT]
[INDENT]Memory:            2x512 MB SDRAM, PC100-222S[/INDENT]

As far as I can tell, the only thing wrong with this is that my battery is only good for about 5 minutes of run time.  But since I'm plugged in full-time, that shouldn't matter.

If anybody out there can tell me why things are so awful, I'd love to know.  I'm no newbie; I've been doing multiple Linux distro installations for just about a decade now, dating back to Red Hat 4.2 on ThinkPads.  But I'm truly stumped.

Help, please.

---

### Post by zxee on 2006-09-22
I read through your description a few times and my best guess is that you haven't actually "successfully burned" the iso image. 
It, the iso image, does want to be burned as a raw image, and in my experiance with a G4 pbook mac/apple often has a problem with that.
How, exactly, are you burning the iso? You may want to use a program that correctly burns cd images. Hope that's helpful.

Added-ok sorry, I see you said you burned with a pc. Are you using linux to burn the iso? I've booted cds I've burned on older macs than a pismo (300ghz beige G3's) so it should work. If the iso/cd is ok I can't understand why it won't boot.

---

### Post by KesslerB on 2006-09-22
Thanks for the reply.  I burned the ISO using Roxio Easy CD Creator under Windows XP SP2.

---

### Post by avtolle on 2006-09-22
Wnen you burned the iso, did you burn at as slow a speed as possible? For some reason, the older CD drives don't like disks burned at high speed; a popularly suggested speed is 4x.

---

### Post by KesslerB on 2006-09-22
No I didn't.  I can certainly try that, though I'm pretty sure that's not it.  Like I said, the DVD-ROM drive can read the CD just fine when I'm booted into Tiger; it wouldn't make sense that it can read it when booted into an OS but can't read it when trying to boot from the disc itself.

Oh -- one more thing that I'd forgotten about until your suggestion.  I tried all of this with the Ubuntu 5.10 discs as well.  Those were discs that Ubuntu shipped to me, not discs I'd burned myself.  Both the install disc and the Live disc exhibited the same problem -- an inability to boot.

Having said all of that, I'll try it over the weekend.  In the interim, are there any other suggestions for me to investigate?

---

### Post by zxee on 2006-09-24
Well just to eliminate the drive as a problem-can you boot the orginal or whatever apple system discs from that drive?

---

### Post by KesslerB on 2006-09-24
Yep.  Just before my attempted installation, I wiped the entire hard drive and booted from an OS 9.2.1 CD to install Classic.  When that was done, I booted from an OS X 10.4 DVD to install Tiger.  Both went without a hitch.  So I'm reasonably sure that my hardware is not at fault here.

---

### Post by zxee on 2006-09-25
Have to admit I'm stumped-I did a search on pismo and ubuntu and there have been reported successful installs-so it's not some OEM design flaw.

---

### Post by KesslerB on 2006-09-25
Just burned a new CD-R with Ubuntu 6.06.1 at 4x... but no dice.  Could it be the RAM?  The HD?  The DVD-ROM drive?  Those are the things that have been upgraded and/or fixed over the years.  (Specifically, I'm at a full 1GB of RAM, the HD was upgraded to a 60GB drive, and the DVD-ROM was replaced a few years ago with the same model number.)

Of course, I have no way of undoing those changes....

---

### Post by h00k00 on 2006-09-26
Did you boot the OSX dvd by holding down C-key? I noticed that you couldn't get ubuntu cd to boot this way. I installed Xubuntu dapper to my Pismo by holding down C-key while booting and that worked.

---

### Post by KesslerB on 2006-09-26
I tried booting from the CD in multiple ways:

(1) By holding down the C key at boot time.

(2) By holding down the OPT key at boot time, selecting the appropriate icon, and clicking the right-arrow icon.

(3) I tried selecting the CD within the Startup Disk control panel in Tiger, and I also tried selecting the CD within the Startup Disk control panel in OS 9.2.2, but in neither case could I actually select the CD.

I'll try Xubuntu and see how that goes.

Hmmm.  A new thought.  Should I be able to verify the Ubuntu CD-R that I've already burned using Apple's tools?  Here's what I mean: I tried to verify the CD-R using the Tiger Disc Utility, but that wouldn't work.  I then tried to verify it using the OS 9.2.2 Disc First Aid application, and that didn't work either.

---

### Post by KesslerB on 2006-09-28
I've now burned Xubuntu 6.06.1 at 4X speed and tried to boot my Pismo off of it with no luck.  I'm going to try and remove some RAM.

---

### Post by KesslerB on 2006-09-28
Still no luck.  After removing the upper 512MB of RAM (leaving me with only 512MB in the lower slot), I'm still unable to boot from the Xubunut 6.06.1 CD-R.

Could it be the hard drive?  The stock hard drive in this machine has been replaced.  I've now got a 5400-RPM 60-GB Hitachi Travelstar 1C25T060ATCS05-0 hard drive in there.  Any known issues with the drive?  (I no longer have the stock drive.  What was it, 8GB?)

---

### Post by zubun on 2006-10-25
Hi KesslerB,  for what it's worth, I have a pismo 400 that I've just partitioned and I get the same black screen symptom after booting from the disk. When I had OS 10.3.9 on the book with all my files a week ago it ran the live CD without a problem, now neither a pressed Ubuntu CD or a downloaded Xubuntu one will work

---

### Post by thornomad on 2006-10-26
Seems strange that you can't get it to boot straight from holding down the C key with Ubuntu but that you can with your Mac System Disks ...

Do you have another Mac you can test the Ubuntu disk you burned on?  See if it is a problem with the disk you are burning or the mac you are mounting on ?

---

### Post by KesslerB on 2006-10-26
Thornomad, thanks for the suggestion... I'd thought of that too.  I successfully booted a PowerMac G4 with the disc.  I didn't do the install -- I didn't feel like recreating a Tiger server from scratch -- but I booted into Ubuntu Live with no problem.  (* Sigh. )

---

### Post by zubun on 2006-10-27
HI KesslerB, I downloaded the 6.06.1 version last night and it worked, ubuntu is installed and running. 

I had made it as far as a 'framebuffer, no address pci4000000 etc' error message after a few tries with the pressed CD. The 6.06.1 CD gave the same error but seemed to overcome it and carried on to make a live CD user (albeit slowly) so I installed while the going was good. Also, the install CD was not verified by Disk Utility (it failed) so I guess verification has no bearing on the success of burning the iso. Have you tried with 6.06.1?

---

### Post by KesslerB on 2006-10-27
Yes, Zubun, I've tried 6.06.1.  At this point, I've tried 5.10, 6.06, and 6.06.1, and I'm currently downloading 6.10 to try over this weekend.  I've tried with a full 1GB of RAM and only 512MB of RAM.  I've tried using the internal DVD-ROM drive and swapping that out for an internal CD-RW drive.  I've tried both with and without an Ethernet cable.  I've not tried removing my Airport card (nor am I planning to).

For the life of me, am I doing something wrong?  Is there something about my Pismo that's different from so many others?  (I don't think so -- I'm not that adventurous, hardware-wise.)

---

### Post by zubun on 2006-10-29
I'm no expert (I  failed to get Easy Ubuntu working today, just to illustrate!) but...

It might be worth losing the airport card just to see if it makes a difference, it's not a big job to take it out for ten minutes, just pop up the keyboard and slide it out. 

I think (again, not an expert) that the Live CD does a hardware scan when it's setting up the session, so if it sees something it doesn't like it might not play nice. Also, unless the CD-RW drive is Apple branded it may not allow you to boot from the CD, even if it allows you to boot an Apple OS CD - the stock DVD-ROM drive should work though.

---

### Post by fisherdmin01 on 2006-10-30
I'm running Edgy on a Lombard.  I had the same issues you experienced when I tried to install Dapper.  I too tried it from a CD I had burned.  I finally got a CD I rec'd from the shippit program (Hoary, I think) to work, then did a network upgrade to Dapper.  I used it for awhile, then did a network upgrade to Edgy.

The actual installations went surprisingly smoothly, but I'm stuck with the known issues of Linux on PPC (crappy flash/shockwave support, no Quicktime, iffy recovery from sleep, etc.)

Still for a 7 year old laptop with 256 MB of RAM, it's amazingly fast, esp. w/ Xubuntu desktop.  I just think there are some weird issues with CD's burned from PC's being used to boot old Macs - that's just my experience.

Hope it helps.

---

### Post by dpny on 2006-11-08
I am now having this same problem. I know it isn't the hardware because I installed 9.2.2 and 10.4 today on the same machine without a hitch.

edit: I just tried to verify the CD I burned for 6.10 using Disk Utility (the same program I used to burn it) and got an error: *Invalid number of allocation blocks. The volume needs to be repaired*. So I verified both of the .isos I downloaded, one for 6.06.1 and one for 6.10, and got the same error on the .isos. Could there be a problem with the .isos themselves?

---

### Post by rcas on 2006-11-09
Been having issues of my own with a powerbook TI...

I found that my OpenFirmware alias for the CD is incorrect.
(Drive was upgraded at some point...)

So, try this:

Boot into OpenFirmware (power on holding down
Open Apple, Option, O and F) at the prompt
type 'devalias' not quotes... you should see what
the cd alias is.

from a prompt try 'ls cd:,\' if this works then your
cd alias is good.  If not, you need to determine where
you cd is.  Mine is
/pci@f2000000/mac-io@17/ata-3@20000/disk@1

Once you determine where your cd is you need to
replace your alias like so:

'devalias cd /pci@f2000000/mac-io@17/ata-3@20000/disk@1'

then you should be able to boot from it like so:

'boot cd:,\\:tbxi'

Hope this helps.

As a side note, I get the install started but then I get no
video on my TI book.  I installed using the video=ofonly option
and then on reboot no luck.  Any thoughts?

Thanks,
Ray

---

### Post by dpny on 2006-11-09
> **rcas said:**
> As a side note, I get the install started but then I get no video on my TI book.  I installed using the video=ofonly option and then on reboot no luck.  Any thoughts?

Thanks,
Ray

I will try that. Here's a more accurate description of what happens:

The machine boots from the CD and everything seems normal: blank screen and CD spinning. At some point the screen goes weird. It's difficult to describe, but it's as if there is a bright flash on the screen which slowly fades, during which time it looks as if the screen is divided up into twelve or so rectangles. After a little while I hear a few notes played, as if there's a screen to which I should be reacting and the CD stops spinning. So the problem seems to be something with the video. Like I said, I installed both 9.2.2 and 10.4.8 on the machine yesterday without a hitch.

---

### Post by oswaldkelso on 2006-11-09
Hi just my two penny worth hope it give you some ideas.

I had problems getting an imac 333mhz to boot, what I did may help.

On older hardware use the alternate cd.

Dont burn with the "finder"it can corrupt the iso, drag into "disk utilitys", select and burn from there.

If it hangs with a black screen. But its still reading the disk wait when the hard drive stops (ctl opt F1) gives you the shell and you can checkyour xwindows settings.

code

 nano /etc/X11/xorg.conf 

code

 startx

Ctl opt F7 exits the shell 

hope it helps if not you the someone

---

### Post by dpny on 2006-11-09
> **oswaldkelso said:**
> Hi just my two penny worth hope it give you some ideas.

I had problems getting an imac 333mhz to boot, what I did may help.

On older hardware use the alternate cd.

Dont burn with the "finder"it can corrupt the iso, drag into "disk utilitys", select and burn from there.

If it hangs with a black screen. But its still reading the disk wait when the hard drive stops (ctl shift F1) gives you the shell and you can checkyour xwindows settings.

code

 nano /etc/X11/xorg.conf 

code

 startx

Ctl shift F7 exits the shell 

hope it helps if not you the someone

Just got a different variation on a messed up screen. What's different about the alternate install?

---

### Post by oswaldkelso on 2006-11-09
> **dpny said:**
> Just got a different variation on a messed up screen. What's different about the alternate install?

"An alternate install disc using the text-mode debian-installer is available for download, and is aimed at people with lower system specifications, administrators installing on many systems, and for complex disk partitioning including the use of LVM or RAID."

Basically as I see it. Its the old breezy type install with more options, more user friendly in some ways and kinder to older macs:) Its worked on my lower end macs where the standard install has failed.

Whats messed up?

---

### Post by dpny on 2006-11-09
> **oswaldkelso said:**
> Whats messed up?

My guess is that there seems to be a problem either 1) recognizing the Rage 128 mobility in my Pismo or 2) a serious problem with the X settings. Essentially there's no usable video whatsoever, so even trying to get to a terminal doesn't work.

edit: grabbing the alternate install right now.

---

### Post by Zarephath on 2006-11-09
I didn't see that you could actually get to a boot point where you can actually try and get to a tty to check out what is going on. So what you can do is try a different burning software...look for a freeware version that will burn iso's..there are some out there...or even try booting into OS X and using the system utility to burn the iso image to cd-r..you could also try a rewriteable in case there is something about the cd-r's you are using that it doesn't like.

---

### Post by dpny on 2006-11-09
> **Zarephath said:**
> I didn't see that you could actually get to a boot point where you can actually try and get to a tty to check out what is going on. So what you can do is try a different burning software...look for a freeware version that will burn iso's..there are some out there...or even try booting into OS X and using the system utility to burn the iso image to cd-r..you could also try a rewriteable in case there is something about the cd-r's you are using that it doesn't like.

I actually did burn it from Disk Utility on my G5. I will try the alternate CD and see if that works.

---

### Post by dpny on 2006-11-09
The saga continues. . .

I tried installing from the 6.10 alternate CD. No luck.

I want to make sure I haven't been too vague so far, so this is what happens when I try to boot from one of the installer CDs:

I start the Pismo with the option key down. Up comes the screen from which I can select the boot media. I select the Ubuntu CD. The drive spins up. The screen is completely blank. The drive spins down. If I hit the return key at this point, the screen gets weird: it flashes white and slowly fades. I took a picture to illustrate my point. This is the screen fading:

[IMG]http://img.photobucket.com/albums/v292/noewun/Pismo_1.jpg[/IMG]

The screen eventually fades away entirely. If I let the machine keep going I hear a musical sound as if I've hit a screen I can't see which is welcoming me to something.

Now, I've tried holding down control-option-F1 when the CD starts spinning, but no combination of key commands I can find will give me a screen I can use. The 6.10 alternative CD gave me a slightly different weird screen:

[IMG]http://img.photobucket.com/albums/v292/noewun/Pismo_2.jpg[/IMG]

I then tried to follow the suggestions [here](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html#boot-newworld), but my main partition is HFS+, which yaboot can't boot from. It's a 40 gig drive with one 20 gig HFS+ partition which has 9.2.2. and 10.4.8 on it and the other half free space. I tried to format the free space as HFS, from which yaboot can boot, but I can't do it. OS X's disk utility will not format HFS. OS 9's disk setup utility won't show me multiple partitions. I tried to use **diskutil** from OS X's command line, but it will not allow me to change any partitions on the boot disk. I booted from the OS X install CD and got into the Terminal, but I do not know enough to format a partition on my Pismo's internal drive when booted from the OS X install DVD.

So far I have tried both 6.06 and 6.10 install CDs, the 6.10 alternative CD and my old 5.10 install CD. No luck.

Weirdness: this is a stock Pismo with a 500 MHz G3 and a gig of RAM. It used to have a flaky 900 MHz G3 upgrade from Powerlogix. Using that processor the 5.10 install was (if I remember) easy as pie. For some reason that 5.10 CD is now giving me the same weird screen with a 500 MHz processor. I have no idea why this would make any difference.

The machine's internal keyboard is also mostly kaput. I spilled water on it years ago and, I think, damaged the keyboard connector. It works flawlessly with an external keyboard. I thought maybe the damage to the internal keyboard might be preventing me from hitting the key combo to get into the shell when installing, but I was able to boot into open firmware using the external keyboard, so it seems to work well. I'm pretty sure it isn't a hardware problem, as I nuked the drive, partitioned and formatted it and installed both 9.2.2 and 10.4.8 from scratch yesterday. The machine works well in both OSes.

The only thing I can think of is trying the live CD.

---

### Post by dpny on 2006-11-14
Finally got it to work, and I'm not sure what I did different. I ran the Pismo hardware test CD, which reported everything was fine. Then I rebooted the 6.06.1 install CD holding down the "C" key and it all worked. It could've been something as stupid as needing to hold down the "C" key instand of option.

Thanks for all who offered suggestions.

---

### Post by oswaldkelso on 2006-11-16
Great!!!!! sometimes we can't see the forest for the trees:) I was going to suggest Debian or Gentoo as they seem committed to ppc, though not quite as popular as Ubuntu I hear their hardware support is generally good. Anyway I'm pleased your up and running you had me scraping the gray matter!!!

---

