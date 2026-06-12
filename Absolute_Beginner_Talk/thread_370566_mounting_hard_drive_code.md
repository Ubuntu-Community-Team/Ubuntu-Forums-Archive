---
title: "mounting hard drive code"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by johnlh on 2007-02-25
I did get ubuntu to automount my window hard drive partitions.  My question is:
what is the 'nls=utf8' statement in the following:

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

I could not mount successfully with that in there.  Instead I omitted that as I found in the guide: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html) ,  and it worked.

/dev/hda1 /windows ntfs umask=0222 0 0

I should have taken note what error message I received. Sorry about that. 
John:)

---

### Post by muguwmp67 on 2007-02-25
I think nfs=utf8 has something to do with converting filenames.  Maybe the utf8 setting wasn't correct for your system.

---

### Post by johnlh on 2007-02-26
Thank you Mug.   I think I caught a break w/ all my hardware b/c things have gone smoother than I expected.  (knock on wood).

---

