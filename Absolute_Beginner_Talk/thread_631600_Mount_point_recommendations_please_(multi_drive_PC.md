---
title: "Mount point recommendations please (multi drive PC)"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Guy7 on 2007-12-04
Hi all, first post here I think =:^0

I'm just about to wipe an old Win PC and install Ubuntu.  The idea is to set it up as a file server to be accessible from my existing Win PCs (sorry, can't get away from it that easily).

The old PC has three hard disks in it which in the past I've used for os, apps and data.  They're 20, 80 and 320Gb respectively (the 320 is two SATA disks in hardware RAID 1 - the mobo has a RAID controller on it).  Would they be hda, hdb and hdc in Ubuntu speak?

I'll be wiping them all completely and plan, subject to recommendations, to create a single partition on each, no, strike that, I'll have to put the swap partition somewhere, hda or hdb I presume, but otherwise just whole disk partitions.

I'd appreciate guidance on what I should mount where please.  / on hda seems a good starting point to me. /home on hdc perhaps?  Is it worth keeping hdb (the 80) in there?

Reading up on the other mount points tends to result in me going "uh huh" but to be honest I don't understand enough about Linux yet to make a judgement call where they should go.

I'll then want to set up somewhere to store individuals' data (/home seems a sensible choice but I'm no expert that's why I'm here) *and* somewhere for common data.  I'll no doubt be back again to sort access rights so Win users can read / write etc (but have had some success in testing).

Recommendations as to the most sensible way forward mount point / partition wise would be much appreciated.

Thanks everso
Guy

---

### Post by Paqman on 2007-12-04
I'd definitively put the swap and root on the 20GB.

Your Raid array seems the logical place for shared data, you could map it as a network drive on Windows and have it mount with a drive letter. There's plenty of good guides out there for setting up Samba.

If you're just using it as a file server, your /home shouldn't need to be that big, since it'll only contain config files for whatever software you install. I'd be inclined to put that onto the 20Gb drive, too.

Which leaves the 80GB one unused. Storage for non-critical data maybe? Or buy a caddy and use it as portable storage?

---

### Post by bodhi.zazen on 2007-12-04
Well, I would start with this thread : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

You might also want to look at LVM.

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

LVM appears to be supported on the alternate install disk, although I am not sure how robust ....

---

### Post by Guy7 on 2007-12-04
Ta muchly for the quick responses.

Pacman - spooky, a caddy is where the 80Gb drive came from originally!  :)

bodhi.zazen - I've had a quick look at that thread.  It feels a bit over my head at the mo' but it's late so probably best looked at on a clear head.  You have taught me that /home isn't for user data though, I thought it was.  I noticed the ref to /data too.  Interesting.

Thanks guys, the sense of foreboding is diminishing (especially as the missus will kill me if she can't get to her files)  ;)

Guy

---

### Post by Paqman on 2007-12-04
> **Guy7 said:**
> the missus will kill me if she can't get to her files


Been there! ;)

Samba can be a bit fiddly to set up. Allow yourself enough time to follow through a HowTo and any potential troubleshooting before presenting the finished article to your audience.

---

### Post by bodhi.zazen on 2007-12-04
> **Guy7 said:**
> Ta muchly for the quick responses.

Pacman - spooky, a caddy is where the 80Gb drive came from originally!  :)

bodhi.zazen - I've had a quick look at that thread.  It feels a bit over my head at the mo' but it's late so probably best looked at on a clear head.  You have taught me that /home isn't for user data though, I thought it was.  I noticed the ref to /data too.  Interesting.

Thanks guys, the sense of foreboding is diminishing (especially as the missus will kill me if she can't get to her files)  ;)

Guy

Yea, it takes a while to take it all in ...

/home is where most people keep user data, but I like to suggest a /data partition. You can always link to /data in /home :

```
ln -s /mnt/data/music /home/Guy7/music
```

---

