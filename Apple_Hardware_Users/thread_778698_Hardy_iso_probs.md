---
title: "Hardy iso probs"
date: 2008-05-02
forum: Apple Hardware Users
---

### Post by Doctor J. on 2008-05-02
Is there a known issue with ubuntu-8.04-desktop-powerpc.iso?  I downloaded it twice, on two different Macs [one by Torrent, one directly].  In both cases, after the download completes i get this when i attempt to mount the disk image: "The disk image you are opening may be damaged and could damage your system."  I am using Disk Utility 10.5.6 on Tiger.

Edit: to be perfectly clear, i also downloaded and burnt the amd64 iso on my Mac - no scary warnings there.

---

### Post by avtolle on 2008-05-02
> **Doctor J. said:**
> Is there a known issue with ubuntu-8.04-desktop-powerpc.iso?  I downloaded it twice, on two different Macs [one by Torrent, one directly].  In both cases, after the download completes i get this when i attempt to mount the disk image: "The disk image you are opening may be damaged and could damage your system."  I am using Disk Utility 10.5.6 on Tiger.

Edit: to be perfectly clear, i also downloaded and burnt the amd64 iso on my Mac - no scary warnings there.
First thought: corrupted iso d/l. Did you check the md5sum of the iso after d/l and before burning? Second thought: bad burn. Did you burn at lowest speed (4x, e.g.)? I have a feeling you've checked this, and the above thoughts are offered for any lurkers. Third thought: did you burn to a CD-R or a CD-RW? My onboard CD-ROM won't read RWs, it seems (G4 Cube, fyi), and I need to use high quality CD-R media for an iso burn. Fourth thought, after the burn, did you check the md5sum of the disk?

---

### Post by Doctor J on 2008-05-05
> **avtolle said:**
> First thought: corrupted iso d/l.

I had that notion as well.  That's why did the d/l again, from a different source, on a different computer - same result.

> **avtolle said:**
> Second thought: bad burn.

I never got to burning.  The problem surfaced when mounting the .iso preparatory to loading it into Disk Utility.  At this point, i suspect there is something particular about that specific iso that OSX doesn't like.  I will copy it over to my Feisty partition and try the burn from there.

---

### Post by stream303 on 2008-05-05
It has been awhile since I burned from Tiger, but all I ever did was to just open disk utility, drag the downloaded iso to the left-hand pane, highlight it, and then click burn - using a low speed.

I don't recall having to mount it though.  Getting tired so I could be totally wrong here... :)

---

### Post by Doctor J. on 2008-05-11
I'm so used to using Toast that i forgot about that - Toast expects to work with mounted images, and Tiger's DiskImageMounter definitely didn't like that image [It was just fine with the image for 
AMD64.].  It seemed to burn okeh, though, so i'll give it a try next weekend.  Thanks!

---

### Post by cyberdork33 on 2008-05-11
> **Doctor J. said:**
> I'm so used to using Toast that i forgot about that - Toast expects to work with mounted images, and Tiger's DiskImageMounter definitely didn't like that image [It was just fine with the image for 
AMD64.].  It seemed to burn okeh, though, so i'll give it a try next weekend.  Thanks!
i use toast all the time without mounting the image...

---

