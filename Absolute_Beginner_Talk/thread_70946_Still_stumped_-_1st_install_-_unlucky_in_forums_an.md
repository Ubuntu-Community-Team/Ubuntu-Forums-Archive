---
title: "Still stumped - 1st install - unlucky in forums and IRC"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by mcruser on 2005-10-01
Hi -

I'd love to get started in Ubuntu Linux, but I can't get it installed, and questions posted so far to the Forums and to IRC have yielded no response. I thought I'd post one more time before switching releases. If anyone out there has an idea for an alternative for troubleshooting - even paid - I'd be happy to try it out.

I'm trying my first linux installation with Ubuntu 5.04 on a PowerPC G3 and have even wiped a new hard disk with multiple repartitions in the process. Although the Live CD works, installation now stalls after booting from HD and displaying the text "Starting hotplug subsystem..." I've posted to that related thread, but so far haven't had success with tips posted previously.

Please - *any* suggestions appreciated. Thanks -

Marc

---

### Post by skoal on 2005-10-01
Mcruser, I saw your other installation post here: [http://www.ubuntuforums.org/showthread.php?p=370006#post370006](http://www.ubuntuforums.org/showthread.php?p=370006#post370006)
I don't have a Mac, but my best suggestion would be to use the LiveCD, mount the Ubuntu / partition under /mnt, and check log files under /var for some insight.

Is it _just_ failing here during the "hotplug" init part?  Consistently? Or on other parts of init?

From that other thread you posted, it may be a good idea for you to post your partition scheme here as well (just to exclude that possibility).

\\//_

---

### Post by mcruser on 2005-10-01
Skoal -

Thanks for the post. It seems to be consistent in stalling at the hotplug message. Right now there's company sleeping in the room with the new Linux system, so I'll try the Live CD technique and also review the latest partitioning in the morning. More later...

Marc

---

### Post by erikpiper on 2005-10-01
I have this problem on my thinkpad- I have to boot into rescue mode, shut down, and start normally. If that doesn't work, (Only times it doesn't is after repartitioning,, for me) I had to boot into window$ first. Blech. 
(Only have it for orbiter. w2k, small as it gets)

---

### Post by mcruser on 2005-10-02
Hi -

**Erikpiper**: Thanks for the tip - tried boot with _rescue_ and "shutdown 0" and got:
shutdown: timeout opening/writing control channel /dev/initctl
init: timeout opening/writing control channel /dev/initctl

**Skoal**: Well, I restarted from the _Live CD_ and found the man pages on mount, but my neophyte attempts to mount were unsuccessful:
mount /dev/hda /mnt -- read-only, looks like the Live CD
mount /dev/hdb /mnt -- can't read superblock (?)
mount -t ext3 /dev/hdb /mnt -- same
Also tried these with the rescue disc - same results.

On another reinstall attempt, I retrieved the current _partition data_:
IDE2 master (hdc) - 160GB ST3160023A
(I formatted only a portion of the HD in case its size was too large for my older system to recognize. I've tried all defaults, and get the same errors.)
#1 32.3 KB          Apple
#2 1.0 MB  boot   Boot
#3 30.0 GB ext3   Ubuntu /
#4 1.2 GB  swap   swap   swap
  128.8 GB free space

_Other findings_: 
When booting from HD, before the message "Starting Ubuntu" I find the message: 
PCI Cannot allocate resource region 0 of device 0000:01:02.0
Subsequently, continues boot procedure until stalling at hotplug message.

Also, I later recalled that when a past attempt to attach a FireWire CD-burner failed, I learned the Firewire port wasn't functional, so I installed a new Firewire/USB2 card, but during installation debugging, I've disconnected all attached devices.

Finally, here's a question - what would make the same system run normally on Live CD and not run from HD when completing installation?

This Linux thing seems so close...

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=mcruser]
Finally, here's a question - what would make the same system run normally on Live CD and not run from HD when completing installation?
This Linux thing seems so close...[/QUOTE]

Nothing should really. My best advise- Breezy comes out later this month. Wait and try again!

---

### Post by skoal on 2005-10-03
[QUOTE=mcruser]Finally, here's a question - what would make the same system run normally on Live CD and not run from HD when completing installation?[/QUOTE]
As poofy stated, nothing really.  However, after looking over your rather "unique" partitioning scheme, I really don't understand it at all.  I would assume you are using another bootloader other than grub? A powerPC BIOS requires such a partitioning layout?

I did find a somewhat relevant thread here: [http://www.ubuntuforums.org/showthread.php?t=70226](http://www.ubuntuforums.org/showthread.php?t=70226)

...althought it's on a different architecture, they are experiencing a hang on the "hotplug" init part as well.

If you are using the liveCD and your primary hdd is /dev/hdc (with / on hdc3), you would mount it something like:

sudo mount /dev/hdc3 /mnt

...and possibly may need to add the "-t ext3" switch (or reiserfs or whatever), but it should automagically detect the fs.  Then check the logs under /mnt/var/log.  If possible, attach the 'dmesg' log file back here as an attachment or try and run dmesg directly under the liveCD.

Also, can you run from the liveCD and report back the contents of:
lspci -vv -s 01:02.0

That device at the busID seems to be giving you problems.  What is it?

\\//_

---

### Post by mcruser on 2005-10-03
Poofy & skoal - thanks for the feedback -

As for the partitioning scheme, I'd almost say I don't know nuthin' 'bout partin' no disks, but I've been trying to learn along the way. It's basically the Ubuntu defaults on the PowerPC - except I limited the size of the Ubuntu partition, and I added partition labels in case it might help later with troubleshooting.

I'll keep an eye on thread 7026, but so far it seems focused on ASUS stuff (?) and BIOS updates.

Curiously, here's the output to the mount command:
>sudo mount -t ext3 /dev/hdc /mnt
mount: /dev/hdc already mounted or /mnt busy
>cd /mnt
>ls -a
[nothing but directory dots]

I tried running dmesg from a term window and got a ton of output - probably too much to display here, so if you're brave enough, it's available as an attachment. Looks handy, but I don't know where to start with it.

As for lspci, this output was a bit more brief, although, again, I'm not sure what to do with it:
ubuntu@ubuntu:/mnt$ lspci -vv -s 01:02.0
0000:01:02.0 SCSI storage controller: Adaptec AHA-7850 (rev 03)
        Subsystem: Adaptec AHA-2904/Integrated AIC-7850
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 16 (1000ns min, 1000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 23
        Region 0: I/O ports at 1000 [disabled] [size=256]
        Region 1: Memory at 80a01000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 80a10000 [disabled] [size=64K]
        Capabilities: <available only to root>

As for Poofy's suggestion about waiting for the next version, I'd be willing to try that, though I might check out another distribution in the meantime. However, as Ubuntu/Kubuntu is available on multiple architectures, I could run the same distribution on multiple systems at home, and might even get folks at work to try it out. (With distant CS training some 11 yrs ago, and some med school in the meantime that wiped it all out, I'd like to get some open source electronic medical record stuff up at the hospital where I work, like FreeMED, but for now it's just dreaming - mostly nightmares until the basic system gets up and running.)

Enough with my wild hair tangents. Still looking forward to running Ubuntu. Thanks for the tips so far!

---

### Post by skoal on 2005-10-04
[QUOTE=mcruser]Curiously, here's the output to the mount command:
>sudo mount -t ext3 /dev/hdc /mnt
mount: /dev/hdc already mounted or /mnt busy
>cd /mnt
>ls -a
[nothing but directory dots][/QUOTE]
The problem with that mount command is that you are only using /dev/hdc (which is the _entire_ disk), when you need to be using something like /dev/hdc3 (note the "3"), which from your prior post is the root partition (/).

By the way, your lspci output and the device you are getting an error with is from your Adaptec SCSI controller (AHA-2904/7850).  Is this a PCI card or integrated onto the motherboard? As best I can tell from your dmesg output, you have an ATA controller (and your IDE drive is attached to it @hdc) and you have an integrated SCSI controller (AHA-7850) which probably has just an external 50-pin port (with nothing attached to it)?  Is that right?

I realize I'm in the "Absolute Beginner" section, but here are some possible sol'n(s) and trouble shooting steps (in order of precedence to try out):

I. You are getting a "machine check" kernel oops in your dmesg output, and I think that the firewire device (pcilynx) is causing it.  If you look at the bottom of your dmesg output, a save/store register (SRR1) points to some device (41030) but I can only assume it's your firewire (and I ain't much of a kernel debugger, especially on a remote machine).  That could possibly explain the hang on hotplug, moreso than any scsi driver related problem.

Using the liveCD, add the 'pcilynx' to your /etc/hotplug/blacklist file.

1. mount /dev/hdc3 under /mnt (as explained before, but note the "3")
2. sudo nano /mnt/etc/hotplug/blacklist
3. add a line "pcilynx" (without quotes) somewhere in there, maybe at the very bottom. In nano, use the arrows keys, delete/backspace, and such to navigate/edit around.
4. ctrl-x, save=yes. reboot.

II. If you wanted to (possibly) find out what's causing the hotplugging to hang, you could do the following _after_ you mount your hdc3 correctly:

1. Boot from the liveCD, mount hdc3 under /mnt.
* 2. sudo rm /mnt/etc/rcS.d/S40hotplug
3. Remove liveCD. Reboot. And hopefully you will at least get to a command prompt, and hopefully you have a non-USB keyboard.
4. sudo nano /etc/default/rcS, and change VERBOSE=no to VERBOSE=YES. ctrl-X, save=y.
5. start hotplug with: sudo /etc/init.d/hotplug start
6. See where it hangs...

restore the step *2 before rebooting (just to tidy up) with: cd /etc/rcS.d && sudo ln -s ../init.d/hotplug S40hotplug

I wouldn't imagine the scsi controller would generate any udev events picked up by hotplug at this point in the init process anyways, but it might shed some light on what the real device offender is...

* I took a look at your dmesg output and don't really see anything out of the ordinary except the scsi and pcilynx devices.  Outside of this, I'm really tapped out of ideas.  You could try using an older aic7xxx_old driver, but I don't think that will resolve your hotplug issue. 

\\//_

---

### Post by mcruser on 2005-10-05
Cheers to skoal!

I'm writing this post on my G3, now running my first installation of Linux!!

1: Noting the 3 in mount /dev/hdc3 made a world of difference. (Yes, I'm still quite the newbie.)

2: Adding pcilynx to the /etc/hotplug/blacklist allowed the next reboot to unpack a ton of packages and run the system for the first time from the hard disk. I suspect that the pcilynx refers to the replacement Firewire card added some years ago to get the external CD burner to work. I'll have to check with the manufacturer about drivers, or maybe I'll figure how to crack into the firewire casing, possibly find an ATA drive, and install it into the main Mac unit, bypassing the PCI card. But not this minute. (Sounds like it could work, but it's still above my head, and I'm doing good to get a system up and running at all, apparently.)
   A quick Google search reveals that Lynx is a common Firewire chipset. Looks like they also do sound cards. Beyond that, I'll have to do some more research.

3. About the SCSI controller: I believe it was an Apple-installed optional card. Haven't used it since our old scanner died 4 yrs ago.

4. Haven't had enough time off work in the evening yet to figure out the hotplug snag. I've printed the info about the /mnt/etc/rcS file to try in the future, as I'd like to be able to use the blacklisted device. More pressing for now, though, is figuring out how to link to my HP printer, to my XP system with Samba, and to set up a server for access elsewhere. But I think these topics are probably spelled out already in other posts for me to explore.

Thanks a bunch for the help!!!

---

### Post by skoal on 2005-10-05
Thanks for posting back.  Some other G3 (or PPC system) user might stumble upon this thread with similiar problems.

By the way, just for kicks you might want to check out Yellow Dog Linux, instead of Ubuntu.  I hate to recommend that since I'm quite partial to Ubuntu, obviously.  However, that distro is tailored to PPC systems, IIRC.  You may or may not resolve that firewire issue there, but at least you know how to proceed from here.

Best of luck...

\\//_

---

