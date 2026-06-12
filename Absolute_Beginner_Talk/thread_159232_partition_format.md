---
title: "partition format"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by insane_alien on 2006-04-12
What is the preffered format for ubuntu to be installed on. /ext3 or FAT32? i thought i had installed ubuntu on a FAT32 partition but after installation it appears that its installed itself in a /ext3 partition that i didn't create. i'm going to format and try again but i want to know if i should make the partition a /ext3 format this time.

---

### Post by Perfect Storm on 2006-04-12
Use ext3 it's superior to fat32.

---

### Post by WoodyMahan on 2006-04-12
Ubuntu will create an ext3 partition automatically (it installs the OS on this format).  If you want Fat32 for file sharing with a windows install you can partition the HD during install and leave the majority of workspace on the HD partitioned to Fat32.  Ubuntu writes and reads from that format without a problem, but I haven't installed it and run the OS from a Fat32 drive.  Read the prompts carefully on the install, the partition management is pretty exhaustive.

---

### Post by insane_alien on 2006-04-12
Right so majority of the space should be given over to /ext3 and a small chunk to fileshare with windows. gotcha.

---

