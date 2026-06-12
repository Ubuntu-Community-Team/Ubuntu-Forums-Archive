---
title: "File transfers take MORE time as they progress. ?????"
date: 2017-07-20
forum: Apple Hardware Users
---

### Post by sterator on 2017-07-20
Trying to transfer 10gb of data from HDD to my ubuntu computer, has ssd.

15 mins seems about right. 3 hrs seems extremely wrong, but after 2gb have been moved, that's how much time it says will take.

the items count has not changed; it's 31 now, and ought to be between that and 95 items, the source's items count.

-----------

What's almost more puzzling is that I transfered much larger folders of data (~70GB) which transferred in about an hour.

---

### Post by TheFu on 2017-07-21
Is this a network transfer or SATA or USB or Infiniband or some other sort of connection?  How fast is the connection?  Be careful with the units - GB or Gb are different.  MB or Mb are different.  There is an 8x difference.  Are any of the storage devices showing issues - bad cable, bad disk, bad controller?  Is the target device full? Does it have room for the new files?

When files are transferred, network and disk buffers are uses.  This buffer storage is taken from unused RAM.  You can watch it fill using the **free -hm** command. Usually, transfers happen at "read" speed until the buffers are full.  After that, transfers slow to "write" speed.  Disks usually can write faster than a 100 base-tx network, but not nearly as fast at a 1000 base-tx network.  For both network protocols, there is overhead due to the way that packets chunk up the data for transmission or if any encryption is used.

Wifi is always slower than wired, at least IME.  Newer wifi in ideal conditions might be faster than 100base-tx, but usually there are localized interference problems which make wifi slower.  Next generation wifi (after AC) might finally get faster. We shall see.  My wifi claims to be 300Mbps and I have both the wifi AP and computers setup to use only that speed.  Guess how fast real-world transfers are from 4 ft away?  75Mbps.  Wired is always faster.

None of this has answered your question, but hopefully it will provide somewhere to search for more data.

---

