---
title: "portable hardrive question"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-03
okay i have a western digtal portable hardrive that has tons of stuff saved onto it. It works perfectly fine with the stock cord with my laptop. on my desktop which is windows for gaming i try to run it but it makes a clicking noise on when i run it on windows. could the hardrive be set to a partiton that windows cant read

---

### Post by natehall on 2007-12-03
My experiance with clicking hardrives is they are about to fail. I'd back up any data I wanted to save  if it happened to me.

---

### Post by fedex1993 on 2007-12-03
no it is not clicking on linux at all. like it complete silent and i can save and back up to it and everything. but when i plug it in on windows it clicks i dont know why either

---

### Post by benerivo on 2007-12-03
Can you actually use it in windows even though it clicks - or does it not register as a useable drive? Try going in to linux, connecting the drive, and then```
blkid
```in a terminal. The last entry on each line is the filesystem type. If it anything other than fat or ntfs then it is not compatible with windows. If it is ext2/3 then you can install a driver in windows that will let you read/write to it.

---

### Post by Hospadar on 2007-12-03
what is it formatted as? right click it under linux and check the filesystem, if it's ext3, you might want to try either, reformatting it to ntfs and then use ntfs-3g under linux to read and write to it, or, install ext drivers in windows

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Note that if you go the latter route, the drive will only mount in windows if you've properly unmounted it in linux by a) only removing it after a clean linux shutdown or b) right-clicking in linux and selecting "unmount"

---

### Post by fedex1993 on 2007-12-03
na its failed it will connect but once i try to save stuff to it shuts down auto maically so yeah i will probley need to buy a new one or just use my ipod :)

---

