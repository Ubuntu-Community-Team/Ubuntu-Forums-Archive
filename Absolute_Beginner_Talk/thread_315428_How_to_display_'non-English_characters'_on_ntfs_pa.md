---
title: "How to display 'non-English characters' on ntfs partitions correctly?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by mahy on 2006-12-09
Hello,

what do i have to add to /etc/fstab to display characters with diacritics (Central European) in filenames correctly on ntfs partitions? Adding utf8 doesn't help, likely because windows doesn't use Unicode. The encoding used in windows is called windows-1250, but i'm not sure if that'll help. Any ideas?

---

### Post by mahy on 2006-12-09
alrite, after a long and tedious trial-and-error approach, i found out that nls=utf8 does the trick...

---

### Post by btdown on 2006-12-15
Hi,

I'm having the same issues with not being able to copy some Czech MP3s to my US Ubuntu NTFS mp3 partition. 

I tried the nsl=utf8 in the /etc/fstab, but it doesnt seem to work. Am I doing this right?

```
/dev/hdd1       /media/music    ntfs-3g auto,gid=1002,umask=0002,nls=utf8       0       0

```

---

