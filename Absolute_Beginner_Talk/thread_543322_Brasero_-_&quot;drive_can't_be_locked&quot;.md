---
title: "Brasero - &quot;drive can't be locked&quot;   ??"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by j_dog on 2007-09-05
I've been trying to copy a CD  and I keep getting this error.  What am I doing wrong ?

---

### Post by jombeewoof on 2007-09-05
try using sudo 
if that doesn't work unmount the drive

---

### Post by disraeli on 2007-09-30
I have the same problem too. The bug was filed by someone on launchpad but they closed it as it doesn't seem a Brasero problem. I'm gonna try something and will post the result asap.

EDIT: I rebooted and everything went fine. Guess the problem must be related to the fact I used the drive for listening to some audio cd, and Sound Juicer didn't release a lock or such. Anyway after writing was finished, integrity check failed because Brasero couldn't mount the drive. I unmounted the drive from a terminal, mounted it again to see if everything was ok, and unmounetd it again. Then I told Brasero to perform the integrity check again and it worked.

---

