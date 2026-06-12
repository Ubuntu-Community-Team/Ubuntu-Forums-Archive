---
title: "repair netatalk cnid database"
date: 2011-02-08
forum: Apple Hardware Users
---

### Post by hgu on 2011-02-08
I have set  up a ubuntu 10.04 LTS machine to be used as a time machine backup solution. It worked well for quite some time, but recently I had other problems that completely filled up the root partition with log files and that screwed up many parts of the system. I'm guessing that is the cause of that one of my time machine backup partitions have issues now (I have two partitions for two different computers only one of them have issues). When the mac (OS X 10.6.5) try to connect it manage to mount the appletalk volume on the ubuntu machine but not the time machine sparse volume on it. It just tries and the finder uses like >100%  without managing to open it. The sparse bundle icon flickers, between generic icon to sparse bundle icon. Creating files on the appletalk volume from the mac works without problems (just for testing).

Anyway I'm guessing that it could be due to that the cnid database is corrupted. Anyone know how to repair or recreate it on an Ubuntu 10.04 machine using netatalk 2.0.5? The cnid database is according to file a ".AppleDB/cnid2.db: Berkeley DB (Btree, version 9, native byte-order)" file.

Also other tips of what might be wrong is appreciated.

/Harald

---

