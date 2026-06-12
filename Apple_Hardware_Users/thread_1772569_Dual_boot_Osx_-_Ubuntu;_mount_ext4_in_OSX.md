---
title: "Dual boot Osx - Ubuntu; mount ext4 in OSX"
date: 2011-05-31
forum: Apple Hardware Users
---

### Post by Michel66 on 2011-05-31
Hi,

I've used the following steps to install Ubuntu on a Mac Pro (see dual boot) [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Can run Ubuntu without a glitch but cannot mount the Ubuntu partition in OSX.

Two problems:

1. well, not able to see the ubuntu partition on the desktop (not that important but)
2. trying to create a VM in Parallels using that Ubuntu installation but dont have permission to do so.

So how can I read/write on the Ubuntu partition?

Thanks

---

### Post by unknownPoster on 2011-05-31
You can't.

OSX doesn't support EXT4.

---

### Post by Michel66 on 2011-05-31
if I use ext3 then, will it do?

---

### Post by avtolle on 2011-06-01
I'd suggest setting up a partition formatted NTFS which gives r/w abilities in both. Not sure in ext3 anymore (don't use OSX at all), but at one time, could read from but not write to ext3 in OSX.

---

