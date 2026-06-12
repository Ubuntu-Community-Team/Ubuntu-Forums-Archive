---
title: "what's your ntfs-3g experience?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by TomFumb on 2007-12-29
I've read that ntfs-3g has proved a reliable way of writing to ntfs, but that it should not be thought of as guaranteed to work without fault. So my question is...

Has anyone here had difficulties with ntfs-3g (e.g. corrupted files, broken index)? I'm running a dual-boot system for the first time, and I'm thinking about trying things like (by the way please feel free to point out anything really stupid in this list)...

  - having uTorrent on xp and ubuntu (wine) and downloading to the same location (ntfs partition)
  - deleting firefox bookmarks in ubuntu and replacing the file with a sym link to windows' firefox bookmarks

The uTorrent thing feels a little risky, as bittorrent is heavy on the hard drive, and if ntfs-3g has any issues I imagine they will present themselves here.

Any information that anyone can give will be greatly appreciated!

Cheers,

tom

---

### Post by taurus on 2007-12-29
Why not create a partition with ntfs filesystem and use it to share files between Ubuntu and windows.  And if you somehow trash that partition, at least it won't effect your OSes.

---

### Post by PeterJS on 2007-12-29
I've downloaded multiple torrents to an NTFS drive using ntfs-g3 and it's  never given me any trouble. I'm thinking that ntfs-g3 is as good as people say it is, that said the karma gods will look down on me and my, or your, drive is going to eat itself some time in the next half an hour just to make me look bad.

---

### Post by nick_h on 2007-12-30
ntfs-3g was an option in Feisty before becoming default in Gutsy.  I would have expected any major problems to have shown up before now.

You can share entire Firefox profiles between Windows and Ubuntu.  You may be interested in this link - [Howto: Share Thunderbird & Firefox data between Ubuntu & Windows](http://ubuntuforums.org/showthread.php?t=203524).

---

### Post by LaRoza on 2007-12-30
No problems.

I have my storage partitions as NTFS (formatted from Vista) and have no problems reading and writing to them.

I use them for storing all of my data and files, including my ISO collections, software and downloads. 

Of course, I don't know what other's have experienced.

---

### Post by KhaaL on 2007-12-30
I've had a good experience with ntfs-3g, I thought it was an annoyance having to force ntfs partitions if they had to be checked first (I know of no such tool under linux) or mounting them readonly.

There is one time I've had a NTFS partition majorly screwed up, and that was on my detachable HD. The files could be read from it, but the name of the files written to it got messed up and some files could not be written. It had the same behaviour under windows and was unrepairable, so I had to format it.

That's the only bad experience I've had with it, and I've used NTFS-3g for quite a while.

---

### Post by TomFumb on 2007-12-30
Excellent thanks a lot everyone, I'll press on with my plans, but investigate nick_h's link for firefox and thunderbird (thunderbird was going to be my next project).

---

### Post by fiddledd on 2007-12-30
I've been using ntfs-3g since Feisty without a problem (yet). I have 2 NTFS partions and an NTFS formatted hdd I use for backup. i also use 1 of the NTFS partitions for a .vdi for VirtualBox. So, for me at least, I find ntfs-3g very reliable and I trust it with my important data (hopefully not famous last words). But this post in no way endorses ntfs-3g, please don't blame me if you lose all your data :)

---

### Post by LaRoza on 2007-12-30
> **fiddledd said:**
> So, for me at least, I find ntfs-3g very reliable and I trust it with my important data (hopefully not famous last words). But this post in no way endorses ntfs-3g, please don't blame me if you lose all your data :)

Very well put :)

When Windows is involved in any way, you never know....

---

### Post by vanadium on 2007-12-30
@ KhaaL: you can install nftsprogs using Synaptic. Among the different tools, there is ntfsfix, which can correct problems with ntfs volumes. Anyway, you should use ntfs only if you also are using Windows.

---

### Post by insane_alien on 2007-12-30
one note about ntfs-3g. don't use it to access compressed volumes. it goes abit screwy in my experience.

---

### Post by LaRoza on 2007-12-30
> **insane_alien said:**
> one note about ntfs-3g. don't use it to access compressed volumes. it goes abit screwy in my experience.

Try to avoid messing with the Windows files also, although it is safe in my experience, you have the ability to delete and alter system files that should be protected.

---

