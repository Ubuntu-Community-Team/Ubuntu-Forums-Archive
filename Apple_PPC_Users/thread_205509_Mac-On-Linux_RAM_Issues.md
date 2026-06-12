---
title: "Mac-On-Linux RAM Issues"
date: 2006-06-28
forum: Apple PPC Users
---

### Post by ismhackett on 2006-06-28
No matter what I set the RAM setting to in the "/etc/mol/molrc.osx" file, I always get this:

[COLOR="DarkOrange"]>> MacOS X Boot Loader 0.9.70
>> Candidate boot volume: /mol-blk@0/disk@0:0
>> /mol-blk@0/disk@0:0,\mach_kernel (4338660 bytes)
>> Old mkext timestamp (or safe-boot)
>> Loading from /mol-blk@0/disk@0:0,\System\Library\
>> --> Boot loader failure: Out of memory
cleaning up...
Terminating threads...
DONE[/COLOR]

It worked once using 512 as my RAM setting. I installed the MOL drivers on the OS X side, and then it asked me to Restart OS X. I hit Restart, and haven't gotten it to boot back up. I've used 256, 512, and 1024 as my settings. I have 1.5GB of RAM on this Powerbook, so you know.

What am I doing wrong/.

---

### Post by onehotcutey on 2006-06-28
I had the exact same problem and couldn't figure it out.  Eventually I uninstalled MOL, rebooted, installed MOL from the repositories again, set the memory to 512 and all worked fine and has ever since.

I am working on TiBook 1ghz with 1 gig of ram.

Sorry I couldn't be of more help.  I also looked at the MOL mailing list, but they had nothing.

---

