---
title: "USB thumb drive compatibility question"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-04-15
What's the compatibility situation regarding USB thumb drives and Breezy? I need one. Can i just walk in a store and get one, confident it'll work? Or do i need to find out what models are available in my price range, then google etc to find out which are ok? I dont really _mind_ doing the legwork... but i need a drive pretty urgent (no cd writer, offline, just floppies) and wanna buy it asap!

---

### Post by Ramses de Norre on 2006-04-15
Almost all should work, most of them (all?) are formatted in FAT which is read- and writable by windows and linux.
So I wouldn't worry about compatibility ;)

---

### Post by mscman on 2006-04-15
The only compatibility issues I've seen with thumb drives is regarding U3 smart drives.  These drives can run programs from the drive, but that functionality is only available in Windows.  Also watch for drives that support encryption, or are password protected by default, as most of those will not work with Linux without reformatting the entire thing.  Any regular USB drives, however, should work.

---

### Post by gr0kzer0 on 2006-04-15
Thanks guys, that's just what i needed - just a bit of confirmation before i hand over my pennies. I'd hate to get something that didnt work, and i've found that asking about linux compatibility in stores usually elicits blank looks. It's like the sales assistants think i'm odd for not running windows! I'm only getting a cheap, bog-standard drive, so from what you've said, i should be safe. Cool!

---

### Post by Bloch on 2006-04-15
I have a Gateway mp3 player / memory stick. I nearly broke me head trying to get it to work. At last I found (via a note on the internet by the linux device driver writer!) that the I/O specs of the stick did not comply with the agreed international standard for these devices. The manufacturers simply tested it on windows until it worked and began to produce it.

On later versions of the 2.4 kernel (and on the present ubuntu kernel) the same device worked fine. I suppose the kernel engineers have to make allowances for devices that might not comply exactly with the specifications.

As Ramses says, there should be no problem with an ordinary device. It's a while since I heard of any incompatibilities.

---

