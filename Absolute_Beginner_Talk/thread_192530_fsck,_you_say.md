---
title: "fsck, you say?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Muzzled on 2006-06-08
I am speechless. But, eh... I guess I'll have to try anyway since I started this topic...

It first started up when I tried to boot Unbuntu yesterday; I hadn't booted on it for maybe, 2 weeks. It pulled out a filesystem error telling me log in with root and then run fsck manually. I did, then I started to get prompted with lots and lots of errors on /dev/hda3 (which is my ubuntu partition), so I hit yes a bunch time... then it started to get me worried. I stopped, then rebooted on another OS to find out more that error. Didn't find much more than to just run fsck manually anyway... I ran it again with -y and it did took a while.... a real long while to "fix" my hd. I rebooted, then Unbuntu didn't want to boot, again, telling me that X was corrupted. I got a little pissy, left that there as it is then logged on Gentoo because yeah, I had things to do before all that...

So nothing that I really noticed until someone in this house had to boot on Windows today. An error showed up right before it boots, then after that it booted just fine. Then what you ask? I have a FAT32 partition which is mounted on Windows, Ubuntu and Gentoo that I use to store data that I want to access on all partitions. Funny enough, I noticed that my Music folder(which is on that partition) turned into a Music file with no extension and I have a brand new folder named FOUND.000. In this folder, I have 4057 files Named from FILE0000.CHK to FILE4057.CHK with all size being 32 mutltiples. I so eh... I figured it's my music files all cut and stored into that, so I rename one into .mp3 and it plays just fine with the right ID3 tags but it cuts near the end, of course the last bytes probably got choped into another chunk. So I've got parts of songs here and there... Everything else on that partition has remained the same, I've lost nothing else but the music.

There goes my interrogations, if anyone can help out, I'd absolutely appreciate: 
[LIST]
[*]What happened there, why did it messed up my other partition too, I mean why was it only primary detected in Ubuntu while I could boot Gentoo just fine and access that "corrupted drive"?
[*]Was it really fsck or Windows could have messed with that while booting?
[*]If it is really fsck, does it also check in fstab to check mounted drives(seems like it...)?
[*]Is there anyway to prevent it from doing that?
[/LIST]

And more importantly... 
[LIST]
[*]Is there anything I can do with theses .CHK files and get my 20 gigs of music back? I do have most of the cds in my collection, but it is still a piss off to rip em all again.
[/LIST]

I'm sorry if that's too much, but every little help would be welcome anyway.
Thank you.

---

### Post by FukitsuNaDouki on 2006-08-08
Sorry to hear your files are being screwed up and down. Yes, I also have the same unfortunate situation here.

What happened to you was (IMO) the I/O operation to your hard disk got haywired somewhere. (I'm using an external internal-HDD enclosure, so I'm thinking crosstalk problems in the USB cable). So as a result, those last bits got lost in translation, and in the process, the entire filesystem (not the hard-disk physically) eventually became "useless."

AFAIK, fsck works like chkdsk on Windows XP. As for the recovery process, well, there's not much I can say. There are 2 freeware .CHK recovery software out there (Google for it under "recover .chk files"). They accept recovery to .mp3 files (in your case). But they run under Windows, so no, I will have to find a Linux alternative.

The next thing you can do, (which is rather tedious and troublesome) is to rename the files to .mp3 first. Linux (or at least in KDE/GNOME) provides a useful preview to check on the .chk files. So you can deduce on whether the file's an mp3 or otherwise. For mp3, if they have the ID3 tags on, you can probably deduce what the mp3 file is.

There are some chance to recover some of the files, but if the file (on the preview) is unknown, chances are they are either lost causes, or Linux can't identify it, so you can start out by recovering the ones that are previewable or are identifiable by Linux.

Sorry to hear your dilemma. I am also in the process of recovering my files right now (and it's a very, very troublesome process, identifying, renaming and putting it back to proper folders). I hope my post will help you in one way or another, and some other guys will give a better solution. For now, this will suffice.

---

### Post by catfishy on 2007-04-17
Same exact problem here; a fat32 hdd that now has a Music folder that stopped being a folder.  With 300 gb of music in that folder it's pretty frustrating.  I tried having XP fix it (scan disc for errors or something like that) and got 10,000 found files in a FOUND folder (10 thousand probably being the maximum allowed).  Fortunately, a friend has my entire collection from six months ago, so I can restore after zeroing the drive, but I lost a ton of really important photos and other stuff.  The problem happened when I attached the external to a different machine running the same new Ubuntu Feisty.  This is so frustrating!  Moral:  backup.  Spend your hard-earned money on a larger drive and back it up!

when I do:
fsck -a /dev/sda

it tells me that 1 or 2 FATs it can handle, not 191, what does that mean?

---

### Post by aberry5555 on 2007-04-17
I know this is going to sound unhelpful, but your best bet is to not use FAT32. It is always generating errors and such, best to either use NTFS with the NTFS 3-g module or use ext-2 with the windows ext-2 drivers.

other than that I could only suggest trying to use a file recovery program, though since the files have been chopped and such it might not work.

---

### Post by silverglade00 on 2007-04-17
I can't help you much with recovery, but I may be able to help this not happen in the future. I found that I would get errors just like the ones you described on my FAT32 partitions on occasion. My system is a dual-boot Ubuntu  and Vista. After some frustrating trial and error, I found that the errors only happened when I hibernated Visa and then booted Ubuntu. Ubuntu won't hibernate right on my machine, so I haven't tried going the other way. Moral of the story: shut down instead of hibernating if you want to use the other OS. Hope that helped!

---

### Post by psusi on 2007-04-17
DO NOT DO NOT DO NOT hibernate one system then boot into another that mounts ( some of ) the same disks.  The new system will change the disk in ways that the hibernated system does not expect so when you resume the hibernated system it will toast the filesystem.  

As for fsck, if you told it to check /dev/sda3, then that is all it checked.  If that is not your fat32 partition, then it isn't what hosed it up.

---

### Post by szaka on 2007-04-17
> **psusi said:**
> DO NOT DO NOT DO NOT hibernate one system then boot into another that mounts ( some of ) the same disks.  The new system will change the disk in ways that the hibernated system does not expect so when you resume the hibernated system it will toast the filesystem. 
NTFS-3G detects hibernated Windows and in such cases it refuses to mount NTFS read/write, only read-only mount is allowed. Not even the 'force' option can be used to overcome this protection.

As far as I know, you're right in any other case (whatever is the OS, file system or file system driver).

---

### Post by catfishy on 2007-04-17
Oh, I've had no problems whatsoever with fat32 for two years and then WHAM! I lost the whole Media folder.  I've been able to plug it into Macs, windows and various linux machines.  I plugged it into my new feisty on another machine, I "explored" to my media folder (it was unbearably slow), I could get anywhere, and I shutdown.  Then I lost a few folders and then the parent folder.

PSUSI said:
> As for fsck, if you told it to check /dev/sda3, then that is all it checked. If that is not your fat32 partition, then it isn't what hosed it up.

umm, it can't check anything, it tells me that it can't handle 191 FATs, whatever that means.

I'm trying some of the big names in windows fat32 recovery: norton, recovermyfiles, anything and everything.  It was using Microsoft's Error-checking tool that messed everything up entirely. But I **could not find** any useful disk-checker for ubuntu. Now I have, as I said, 10,000 useless files containing the lesser-important stuff, bah!  Any help would be appreciated, but I'll keep trying to recover at least the jpg's!

**FukitsuNaDouki**, thank you for the thoughtful reply!!!  Sorry to hear about your data-loss too!

---

### Post by catfishy on 2007-04-19
So, after trying all the programs I could get my hands on, I found that Ontrack Easy Recovery Pro was the best for the windows OS.  I found many of the files from my missing media folder and transfered them to another drive.  Many other programs could only search the deleted files.  Having forethought and asking a friend to store my collection on his drive is the life-saver.  The question is still out there: why would mounting a fat32 drive  on a new feisty corrupt the drive and give it an I/O error.  The answer is sort of moot for me because I am zero'ing the drive right now.... Good luck!

---

