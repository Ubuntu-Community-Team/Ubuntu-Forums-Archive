---
title: "[Errno 30] Read-only file system"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by drewyboy on 2008-04-08
I have had this problem trying to install, and each time it stops in roughly the same percentage during install. I have burned 3 disks which are all the live cd, downloaded it 2 times, and have burned each time at the slowest speed possible, have checked the cd's for errors and each time got 100%. I dont quite get it. I had xp and ubuntu 7.10 installed on the harddrive b4 and then something went haywire after the first time I install ubuntu, so I reformated the hardd rive and am now receiving this error everytime.

---

### Post by forrestcupp on 2008-04-08
It would help if you could tell us what the error is, or at least at what part of the installation it stops.

---

### Post by ajgreeny on 2008-04-08
Check the md5sum of the iso file before you burn it to CD just in case it was a corrupt download each time.  You can find the md5sum that it should be here [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).  I'm afraid I have no idea how you can check an md5sum in windows, but in linux it is very easy; in terminal just cd to the folder where the iso file is and then enter ```
md5sum filename.iso
```and a number will appear after a few seconds which you can compare with the number from the site referred to above.

If all that is OK and the burn is successful, have you changed any hardware since the time you got ubuntu running properly?  If so that may be the problem.

---

### Post by drewyboy on 2008-04-09
Thank you guys very much for you help. I finally realized it was that I was using a sata dvdrom to install onto an IDE HD which i guess just doesn't work, so I threw in an old ide dvdrom and no problem. Thanks for your guy's time.

---

