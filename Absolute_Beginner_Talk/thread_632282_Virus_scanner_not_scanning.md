---
title: "Virus scanner not scanning?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by SeriousName on 2007-12-05
So, I just installed the Virus Scanner (ClamAV with ClamTk), and tried to do some scans with it. It seems to ignore a lot of files because they're too big, and also seems to scan only a tiny percent of the files I want it to scan (even using a recursive directory scan). For example, I tried to scan a directory that I know to contain hundreds of files, and it scanned for a bit and then said it had only scanned 7 files.

Is there any way to make it not ignore files due to size, and is there an easy way to make sure it scans every file?

And before anyone says I don't need a virus scanner, I feel I have a legitimate reason for it: I dual boot with Windows XP and I've seen signs of viruses on it, so I want to scan that partition back in Linux where it's "safe".

---

### Post by LIEFofEeofol on 2007-12-05
i have the same problem......

---

### Post by Doomedelite on 2007-12-05
Try:
clamscan --bell -r --log=/home/insertYourUsernameHere/virus_log -i /mnt/C:/

(I got this off a website)

---

