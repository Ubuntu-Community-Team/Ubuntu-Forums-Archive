---
title: "Does Deluge have a check torrent data integrity feature?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-08-06
I just downloaded a live CD using Deluge. I cannot see a check torrent data integrity feature unlike in KTorrent. I want to be sure with the torrent so I want its integrity checked.

Does Deluge have a check data integrity feature?

---

### Post by SOULRiDER on 2007-08-10
I saw someone asked this int he Deluge forums. Deluge does this automatically, so theres no need for you toc heck it manually. If you want that extra security you can compare the MD5 checksum of the file you downloaded witht he one posted on the site where you got the torrent from (if any, but most linux distros provide one)

to get the md5 sum of a file open a console and type:

md5sum <path to file>

The path can be for example "~/someFile.iso" or "someFile.iso"
Hashing may take some time though.

---

### Post by mcduck on 2007-08-10
Checking data integrity is a part of the bitttorrent protocoll, so every bittorrent client should do it automatically :)

---

