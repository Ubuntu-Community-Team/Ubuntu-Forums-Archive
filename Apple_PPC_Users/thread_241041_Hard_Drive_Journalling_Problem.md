---
title: "Hard Drive Journalling Problem"
date: 2006-08-21
forum: Apple PPC Users
---

### Post by TDave on 2006-08-21
Anyone and Everyone... :-)

Presently forced to write this post from my small OS X Partition as Kubuntu did something very rare to me and just crashed...

Upon rebooting, the boot process begins before getting and error coming up saying something along the lines of Error strating HD Journalling and sticking at that point.

Booting into OS X and trying to mount the drive manually using ExtFS manager gives the error that there may be something wrong with the partition.

No idea how this happened, at the time I was running a few applications (amarok was playing a short playlist, KAudioCreator was ripping a CD and Konqueror was FTP-ing another box on the network), something the system does regularly. Firefox was also browsing accessing the server on the other box.
The notebook is a PowerBook G4 with 80gb drive and 512 RAM, 1.25GHz CPU. Running fairly hot, but no more so than when running OS X - it's (if you haven't guessed), an ext3 partition that's been affected.

It's late so I'm going to go sleep before attempting anything more tonight, but any and all suggestions by the morning would be greatly appreciated - I'm pretty well screwed if I can't get any form of access back into my Unix partition!

Many thanks

---

### Post by TDave on 2006-08-22
Just a quick addition with the errors ExtFSManager gives me:

Command: Mount
Device: disk0s3
Message: The filesystem may need repair. Please use Disk Utility to check the filesystem.
Error: 0x1FFFFFFF

Will edit later to include the boot up error.

Cheers

---

### Post by TDave on 2006-08-23
Well, problem solved, albeit not perfectly...

As I sort of began to fear after my bout of denial wore off, the Hard Drive was fu@!ed, as it later managed to slow down and die on me whilst trying to fix the problem is in OS X...

So, now to crack open the box and see how difficult Apple have made it to change a hard drive in one of them...

---

