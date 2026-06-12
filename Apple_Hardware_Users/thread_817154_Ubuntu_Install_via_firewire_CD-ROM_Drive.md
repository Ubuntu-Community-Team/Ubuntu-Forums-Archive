---
title: "Ubuntu Install via firewire CD-ROM Drive"
date: 2008-06-03
forum: Apple Hardware Users
---

### Post by siabost on 2008-06-03
Hi,

G4 Powerbook, 400Mhz, 256Mb Memory, 28Gb Hardrive, OSX 10.1, External CD-RW Drive via firewire, broadband via Thomson Speedtouch USB Modem.
Knackered battery & internal DVD-ROM!

I'd like to install Ubuntu (or possibly Kubuntu) on the above laptop. It's only used for Internet browsing due to the mentioned faults (which aren't worth fixing).

I have downloaded and burned CD image (via PC) of Ubuntu 6.10 PPC.
Holding down option key, with CD in remote drive, I get to see HD (OSX) & Ext CD-ROM (Ubuntu Disk). On selecting the Ubuntu disk and clicking the arrow to proceed it considers it a moment & reverts to the HD (OSX) option.

Is it possible to boot the Laptop from a firewire connected CD-RW drive?
If not, is there an alternative method of installation?

I would be very grateful for any advice.

Thanks

---

### Post by cyberdork33 on 2008-06-03
it sounds like you have a disc error. (bad burn / download). You should probably download the latest release anyway (8.04).

---

### Post by stream303 on 2008-06-03
> **siabost said:**
> broadband via Thomson Speedtouch USB Modem.

This has me wondering if a USB modem is supported in PPC.  Just wondering, although I don't see why not.

> Is it possible to boot the Laptop from a firewire connected CD-RW drive?

Sure is.  To boot from a firewire cdrom drive, you get into openfirmware by holding down CMD-Option-O-F while (cmd = cloverleaf) powering up.  At the openfirmware prompt, issue:

```
boot fw/node/sbp-2/disk:,\install\yaboot
```

be sure to type *boot* and note there is no space after the comma.

Be sure you are burning as an iso image to a CD-R, not a CDRW, and at a low enough speed for the drive to read from.  Many suggest super low speeds just to be safe.

Unless you absolutely need the older 6.06x version, I'd recommend something a tad newer.  For a first time install, perhaps Feisty 7.04 "alternate" would be your best bet; the "alternate" especially in the case of your 256m ram.  Of course, you could just jump in with Hardy if you like.  Try this download link:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by siabost on 2008-06-04
Thanks stream303,

I will try your suggestion as soon as I get home to my mac. I have now downloaded the Hardy alternate CD image and will go for broke!

Re Modem usb modem drivers for ppc, I haven't looked yet. It was a reasonably simple job re my usb Sagem F@st modem for my Intel PC & it works well, but I remember failing to get the Sagem to work on the OSX mac - hence the Thomson Modem which now works well.

Time will tell. If all else fails I presume I can use the/an "ethernet" modem? This will be a new learning curve yet again.

In the meantime, I will post results of attempted Hardy install.

Thanks again.

---

### Post by stream303 on 2008-06-04
Hard to tell, although you may face issues of manually configuring PPPoA / PPPoE etc.

If all else fails, or the PPPoA proves difficult, you can always let a router do all the ppoa stuff, and just hook the computer directly into your modem/router combo via ethernet.  I see that Thomson offers just this kind of upgrade - so even if you only have just one computer in the house, with Linux it is sometimes easier to just use a modem / router combo.

Let's see how it goes!

---

### Post by siabost on 2008-06-05
Stream303, thanks for the info.
I decided to go for Ubuntu 8.04 (alternate CD)

"comd-opt(alt)-O-F , to get into open firmware
then : boot fw/node/sbp-2/disk:,\install\yaboot" 

then

"install"

worked a treat.

It got me as far as the partitioner where it reads:

IDE1 master (hda) 30.0 Gb IBM-IC25N030ATCS04-0
#1 32.2kB               Apple
#2 32.8kB               MacIntosh
#8 32.8kB               MacIntosh
#4 262.1kB              Patch Partit
#5 30.0Gb    hfs+       MacOS
     5.1kB     Free Space

So I have 4 Primary & 2 Logical Partitions, if my understanding is correct.

I wish to dual boot with my existing OSX 10.1. In trying to resize the MacOS partition down to 6Gb to create more free space I get the following:

"Partition Disks
Not yet Implemented!
Support for checking hfs+ file systems is not implemented yet."

Selecting "Continue" takes me back to the partition table listed above.

I presume I need some other program to resize the hfs+ partition - is there a utility that I can burn as a disk image to do this from my firewire CD-ROM? (My original Mac disks are somewhere in the house packed away as we are due to move house!)

Once all this is done (hopefully) how do I ensure that I get the option to boot either system?

Having installed Ubuntu 8.04 to dual boot on two windows PCs I am familiar with that basic process and know that I had to make the Windows partition bootable. Here I seem to have 4+2 partitions!

Which should have the "bootable" flag turned on (if any) & can/should either of the MacIntosh partitions be deleted safely?

Much obliged.

---

### Post by stream303 on 2008-06-05
I'll have to say I'm not the best to ask about partitioning - I really keep it simple by usually devoting the whole internal disk to Linux, and keep OSX on an external firewire HD.

Or, in some cases, I just cut the drive in half by reinstalling OSX and using disk utility first to set up an OSX partition for half the drive, leaving the other half unpartitioned.  After OSX is reinstalled, I have let Ubuntu's guided partitioning handle everything when it sees the "free space".

In custom cases like yours, maybe someone can jump in.

---

### Post by siabost on 2008-06-10
Hi,
Gave up trying to set up dual-boot with OSX & decided on letting the Ubuntu 8.04 PPC "alternate" installer do it's job.

My original partition table looked as detailed earlier in this thread before this install.

The install was from my firewire cd-rw.
On reaching the Partitioner I selected the first option (guided using whole hard drive) and it came back that it was installing on partitions #3 & #4 (I think this was to be SWAP). I thought this a little odd as I hadn't seen a #3 partition in the original table, but I let it go ahead anyway.
The install progressed without problem & finished with an eject-disk & reboot request.

It now fails to boot into anything!

From what briefly flickers on the screen, yaboot seems to load, it very briefly offers me "l" (Linux) or "c" (CD-ROM) boot options then proceeds to show "Please wait, Loading" for a split second then nothing... I've tried the "l" & "Linux" when I've managed to get it to stop at the "boot:" prompt but with the same results.

I can get into Openfirmware via opt/apple/f/o but it won't load the Ubuntu install disk with "boot fw/node/sbp-2/disk:,\install\yaboot" anymore.

Should I have manually deleted all partitions using the partitioner first, then gone to the "guided use whole hard drive" install option?
How do I get my firewire cd unit to fire up the install disk again so that I can have another go?

Any assistance gratefully received.

---

### Post by stream303 on 2008-06-10
Ok, don't panic - yet! :)

There are commercial utilities like iPartition that will resize your OSX hfs, and also free hfs resize procedures discussed here in the threads, but that may be a moot point now.

It sounds to me like the system used the whole drive and installed the 4 mandatory partitions needed, where #3 is your ext3 root partition, and #4 is swap.  #1 and #2 are special apple partitions.  So far so good.

When you boot, and you reach the second-stage of the yaboot: boot prompt (not the Openfirmware prompt), hit -tab- like you did during install to stop the countdown, and see if you can get any further with

```
Linux video=ofonly
or
Linux video=ofonly nosplash
```

it may get you further, but then you may have to edit your xorg.conf to get to a gui.  At least let's see if we can get some response from the display.

I don't know what's up with the firewire drive - let's try this first..  Hang in there!

---

### Post by siabost on 2008-06-10
Thanks stream303.

I had a look at the free HFS+ resizing thread (must have printed out about 30 pages) but got stuck at the "disableJournalling" step! Also noticed some folks had problems with installations where there were 4+ partitions & that's presumably what I would have ended up with. As I had little on the hard drive anyway the simple option seemed best. If required I should be able to resize the Ubuntu partition(s) to allow a reinstall of OSX at a later date.

But first things first, I will try your suggestions when I get home.

Am I right in understanding from the commands:
> Linux video=ofonly
or
Linux video=ofonly nosplash
that I might have a clash with the video driver?

Again, thanks for your help.

---

### Post by stream303 on 2008-06-10
The recent splash screen and framebuffer sometimes confuse the video card right at startup.  You can also just try

```
Linux nosplash
```

as well.  Thing is, once we get to a cli, it may be necessary to customize the xorg.conf to work well with that ATI rage 128 card.  Kind of a two-pronged problem, but the key is to get to a cli where one can fix issues.  Seems a bit of a drag, but once you find the proper parameters, we can make it permanent.

Here's the good news / bad news. It might just be simpler to install OSX first onto say half the drive.  You fire up OSX and before you actually install, you go into disk-utility, delete the old partitions, and create a partition for osx that takes up half the drive. I also normally tell the osx partitioner NOT to use Mac-os compatability, unless of course you need the older OS9 etc).  Leave the rest as free space, and then proceed to install osx.  When that is done, you can install Ubuntu to the free-space it finds, and yaboot should automatically detect the presence of osx, and place it in it's menu of options when you first boot.

That's the theory anyway. :)  This is just one way of doing it, of course you can go totally manual if one desires and keep your existing setup once we get Ubuntu rockin'.

---

### Post by siabost on 2008-06-10
Hi stream303,

> Linux video=ofvideo
worked first time.
It booted fully into Gnome desktop, so (and maybe I did wrong here) I reset the clock (which always returns to 1904 as batteries are knacked) loaded up linux driver for my usb ADSL modem, got it onto the internet, updated via the "updater" and rebooted when it asked me to.

Guess what? I'm back (almost) where I started! I tried both you original boot commands (I'll try > Linux nosplash later) & although the hard drive works away for a while it eventually stops with nothing on screen but a small dash top left.

While it was up and running I was chuffed with how well the Gnome desktop worked - my laptop must be 600Mhz+ rather than the 400 I thought.

So the good news is that if/when it works, it works very well. In fact, if I can avoid it, I don't need OSX at all! (My version is OSX 10.1. & most new software doesn't work with it).

As always, any more ideas appreciated (it does seem to be the video card/driver causing the problem).

Many thanks.

---

### Post by avtolle on 2008-06-10
Wondering, since you've a deceased battery, if you let it stay powered up a half-hour or so, then restart, and at the first chime, reset the PRAM (Command+Option+P+R simultaneously) until you hear the chime, release the keys, and then see if yaboot comes up on the screen. I've had to do this with a Cube with a battery which needs replacing, and it has worked for me to get up and going.

---

### Post by stream303 on 2008-06-10
Yes!  I'm glad you got it working.  But, you are being bitten by the date bug because of the bad battery which prevents gnome from loading (or maybe the battery has a *smidgen* of life left, but the date got confused):

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

See if you can get to a virtual terminal via Ctrl-Alt-F1 so you can reset your date, and also, be sure your firewire drive is no longer connected when booting just to cut down the variables.

Although at some point you'll need to get a new battery.

I am also VERY relieved to hear that your usb adsl modem worked.  I thought that after all this you might end up having to slog through a pppoe setup.  Outstanding.

So you might have to reset that date until you get a new battery.  And, as far as osx goes, 10.1 is a bit behind the times. :)

Let us know if the date problem can fix that issue, and also with the firewire drive disconnected...

Btw, we can make that video=ofonly setting permanent in /etc/yaboot.conf followed by a ybin, but lets see if we can get the system stable...

---

### Post by siabost on 2008-06-11
Thanks avtolle,
Tried that this morn but no luck - yaboot always comes up, gets to the second boot stage, tries to boot linux, works away for a minute or two then stalls on a blank screen.

stream303,
I had bumped into the Gnome time-bug thread earlier but this seems to affect only the loading of the desktop after logging in (correct me if I'm wrong) & after you guided me with the > Linux video=ofvideo command on boot prompt it loaded up Gnome giving me the warning that the clock was wrong and alllowing me to reset it while it was still loading. But (just a thought), it may be that the time-bug is causing a problem now that I've updated ubuntu/gnome and the re-boot (which now never finishes) is getting stuck trying to install the Gnome updates???
On the subject of my 8.04 PPC alternate install disk now not firing up using the Openfirmware command which worked for the original install, I think I may have a dodgy burn as I recall it was playing up a little before I installed. I used InfraRecorder but my work machine wouldn't let me burn it at less than max speed - I'm going to try a fresh/slower burn.#

I can see three options at mo:
1. Re-install Ubuntu using a fresh burned CD (maybe Kubuntu might be better as it is not affected by time-bug??)
2. If I can reset time/date via Openfirmware and launch Linux from there without going through a re-start procedure to allow me to do the xorg.conf amend thing + switch to KDE or XFCE desktops (need loadsa help here).
3. Replace the PRAM Battery.

Is option 2 possible?
I would do option 3 anyway eventually soon as I can confirm my CPU speed to order the right one (anyone know if it's a difficult fix on a G4 laptop?)

Well, there's more questions than you can shake a stick at!

Thanks much.

---

### Post by siabost on 2008-06-12
Hi,
Right, I'm sort of up & running (walking) again.

This is a little weird - 
Attempted to do a re-install & could not get to boot my original Ubuntu 8.04 alternate CD from Open firmware (firewire CD-ROM Drive).
So, I had an Ubuntu 6.04 Live CD which I tried to boot from Open firmware &, Great Scott, it booted straight into Ubuntu desktop! I had a good look around but couldn't figure out what to do from there so I reluctantly shut-down.
Then I tried a Kubuntu 8.04 alternate CD I had burned at x2 speed & it booted into the installer first time. Got as far as 85% into "Select & Install Software" before it failed - several times. Tried to continue with next step to no avail. Checked integrity of CD & it came back ok.

What next? OK, I raked my original Ubuntu 8.04 alt CD out of the bin, gave it a quick wipe, banged it in and ... it booted into the installer, performed a glitch free install and allowed me to boot into Gnome desktop (using "Linux video=ofonly" @ 2nd boot prompt)!
NOTE: re time-bug for Gnome (1904 & all that) - someone must have been working on this as you get a warning after signing in that the system clock/date is wrong & get the option to adjust or ignore as it's loading the desktop.

I've since booted it up again(just to be sure) and although it restarted itself at the first attempt it then proceeded to boot up fine. I get the feeling it's not TOO stable.

I don't understand why all the above has occurred & I haven't updated anything or connected to the internet just in case I upset it (like last time).

As per stream303's post, I will need to configure > xorg.conf  & I would appreciate some help as to what to do.

Hopefully then I can safely get it onto the internet, update & get going for real.

Thanks all.

---

### Post by siabost on 2008-06-13
Thanks for help etc on this thread.

Since I'm more or less up and running I'll close this thread and open a new one with the rest of my problems!

Ta

---

### Post by stream303 on 2008-06-13
With all those reinstalls, just be sure to delete the old partitions, or do the "use entire disk" option, otherwise, you might find yourself running out of room real fast. :)

Sounds like you did though.

---

