---
title: "MacMini 4,1 rEFIt Ubuntu 11.04 - Missing Operating System"
date: 2011-10-12
forum: Apple Hardware Users
---

### Post by jonthenerd on 2011-10-12
This is the first time I've tried setting up Ubuntu on a Mac Mini, so I've tried to be diligent in following all of the documentation I can find.

Here's what I've got and what I've done:

* 2010 MacMini4,1 with OS X Lion
* Successfully installed rEFIt (had to "manually install the package" as mentioned [here]("http://forums.macrumors.com/showthread.php?t=1151242").
* Used Boot Camp Assistant to resize drive and leave 100 gigs for Ubuntu Install
* Following a [blog-posted guide]("http://blog.ravihara.in/post/6245617678/installing-ubuntu-11-04-on-macmini-4-1") and [some more blog tips]("http://dustin.li/2011/05/how-to-install-ubuntu-11-04-on-a-mac-mini/"), I've been able to boot the Ubuntu CD with vesa graphics, perform the installation steps mentioned in the first link (with my boot manager and / mountpoint going to sda5)
* Reboot into rEFIt, sync mbr table
* Reboot machine, select Linux in rEFIt

Here's where it starts to deviate from what I'm expecting to happen. The first time I do the last step, rEFIt sits on it's grey screen with the linux penguin and doesn't progress. Hard resetting the machine, I try selecting Linux in rEFIt again and it progresses to a black screen and displays "Missing Operating System".

Any pointers to what I'm doing wrong? Any guidance on what to check? I've only done the install 3 times now with the same results... I'm having the disk checked right now just to make sure that's ok.

Thanks for any and all help. I'm looking forward to some Ubuntu in the near future :)

---

### Post by jonthenerd on 2011-10-12
Disk checked out fine.

I can get into the Live CD environment and do any necessary checking - just not sure what to check. So far, I've tried reinstalling grub to the ext4 partition and looking for the boot flag on my /dev/sda4.

Here's my partitions at this point:

----------------------------
Partition: /dev/sda1 
File System: fat32 
Label: EFI 
Flags:boot

Partition: /dev/sda2
File System: hfs+
Label: Macintosh HD 
Flags:

Partition: /dev/sda3 
File System: hfs+ 
Label: Recovery HD 
Flags:

Partition: /dev/sda4
File System: ext4 
Label: 
Flags:

Partition: /dev/sd5
File System: linux-swap 
Label:  
Flags:
----------------------------

[This page]("http://mac.linux.be/content/problems-refit-and-grub-after-installation") mentions needing the boot flag on the EXT4 partition, which mine does not have. I've tried setting this, rebooting, and resyncing via rEFIt to no avail...

Any ideas?

---

### Post by jonthenerd on 2011-10-13
Well with enough blind guessing, I got Ubuntu booting. Reading through [another forum thread]("http://ubuntuforums.org/archive/index.php/t-1572642.html") dealing with Macbook Pros got me thinking about the boot flag and what rEFIt was doing when it synchronized.

So - here's what got it booting:
1) At the point where I'm getting the Missing Operating System error after initial Ubuntu Install + sync with rEFIt
2) Boot Live CD
3) Use gParted to set boot flag on EXT4 partition
4) Reboot, do not sync with rEFIt. Instead, hold option down to get to mac partition chooser (don't know what to call it really). Select "Windows".
5) Woohoo! Got to Grub!

From there I followed some of the previous documentation I found to force vesamode, get all the way into ubuntu and download/install the nvidia drivers, and then reboot.

Now - I had rEFIt sync. What was different in its output? The little asterisk next to a partition was next to the Linux partition instead of the hfs+ partition this time around.

Confirmed that Mac OS X and Ubuntu both will load from rEFIt.

This is nuts... Can someone explain what went wrong here?

---

### Post by TerryMasters on 2011-10-13
I don't know what happened, but I've got the same problem here. I really hope your solution works for me too. Last gen Macbook Air on my end.

At first I heard there might be a bug that installed grub to the wrong partition? But if you got yours working then it's most likely something else. No idea what changed it but I'm going to give it a try now. Thanks for posting this in advance, even if it doesn't help.

Edit- It's not working for me. For the record, Lion and Windows 7 both boot fine in refit. Trying to boot the windows partition through the Bootcamp screen gives me the Missing Operating System message though. No idea what's going on or why it's behaving the way it is, but I get an "Error: Not Found returned from gptsync.efi" when I try to sync it sometimes.

> Current GPT partition table:

1 40 to 409639 - Basic Data
2 409640 to 79003391 - Mac OS X HFS+
3 79003392 to 191068479 - Basic Data
4 19106880 to 231117308 - EFI System (FAT)
5 231117309 to (end) - Linux Swap

Current MBR partition table:

1 1 to 39 - EE EFI Protective
2 40 to 409639 - 0B FAT32 (CHS)
3 409640 to 79003391 - AF Mac OS X HFS+
4* 79003391 to (end) - 07 NTFS/HPFS

Not sure if that helps, for the record the last two final builds of ubuntu installed properly in this same triple boot scenario. All 64-bit.

Edit- Good news, this trick worked for me. Hope the word gets around and it helps some other people too: [http://ubuntuforums.org/showpost.php?p=11215214&postcount=185](http://ubuntuforums.org/showpost.php?p=11215214&postcount=185). I used the deb from opensuse.

---

### Post by willnight on 2011-11-02
.
this problem may be related, or sounds similar, to mine:

(macbook pro 17" 2007, triboot; cinema display)

installing either from the desktop or live dvd produced the same result: black screen with "no operating system found" message. replicated this with many retries. took days.

what worked instead: reinstalled earlier working build then upgrade "from within."

in my case, reinstalled 10.04, then upgraded to 10.10, then to 11.10 (oneiric). at each upgrade, i stopped gdm and did update/upgrade in command line. upgrading from to oneiric took a long time (at least 2 hours maybe?).

(cinema display/nvidia conflict?) after installation and reboot, i *did not* install nvidia driver through the "install driver" icon at top because i have cinema display. installing any version (i.e. 173 or "current - recommended") seemed to flake out gdm: only ubuntu background show, but no interface whatsoever. whatever driver came with oneiric works; use "monitor (or maybe screen)" in control panel to detect and activate cinema display.

good luck. (hoping upgrading ubuntu gets easier and more integrative in future releases.)

---

### Post by Obfuscator on 2012-04-15
> **jonthenerd said:**
> Well with enough blind guessing, I got Ubuntu booting. Reading through [another forum thread]("http://ubuntuforums.org/archive/index.php/t-1572642.html") dealing with Macbook Pros got me thinking about the boot flag and what rEFIt was doing when it synchronized.

So - here's what got it booting:
1) At the point where I'm getting the Missing Operating System error after initial Ubuntu Install + sync with rEFIt
2) Boot Live CD
3) Use gParted to set boot flag on EXT4 partition
4) Reboot, do not sync with rEFIt. Instead, hold option down to get to mac partition chooser (don't know what to call it really). Select "Windows".
5) Woohoo! Got to Grub!

From there I followed some of the previous documentation I found to force vesamode, get all the way into ubuntu and download/install the nvidia drivers, and then reboot.

Now - I had rEFIt sync. What was different in its output? The little asterisk next to a partition was next to the Linux partition instead of the hfs+ partition this time around.

Confirmed that Mac OS X and Ubuntu both will load from rEFIt.

This is nuts... Can someone explain what went wrong here?

I had the same happen to me, and I also tried what TerryMasters suggested, but unfortunately I instead got "So operating system found" when rEFIt was synched. So what I did was to uninstall rEFIt completely and just use the Mac boot menu - works perfectly! Why do you need rEFIt anyway?

---

### Post by Coremiv on 2012-05-22
I'm a little late to the party, but this is the closest I've been able to come to a post with the problem I am encountering.  I keep running into the "Missing Operating System" error, but it is when I am trying to use the live CD.  I've tried a couple different version of Ubuntu, but that doesn't seem to be the problem.  I have a Macbook pro with OSX 10.6, any ideas or recommendations?

---

