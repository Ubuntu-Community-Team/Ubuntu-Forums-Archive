---
title: "DVD rip/burning on OSX"
date: 2013-03-07
forum: Any Other OS
---

### Post by Vorian on 2013-03-07
What are some good open-source DVD ripping/burning apps for OSX?

---

### Post by BBQdave on 2013-03-07
> **Vorian said:**
> What are some good open-source DVD ripping/burning apps for OSX?

The last osX I used was 10.4. The osX disk utility, I believe was the name, did a nice job burning data and iso images. Toast was always a good third party program - though with iTunes burning ability and disk utility, not sure you need Toast.

I still have that system, eMac with Tiger - 10.4, I use it as a file server :)

---

### Post by AllRadioisDead on 2013-03-09
> **BBQdave said:**
> The last osX I used was 10.4. The osX disk utility, I believe was the name, did a nice job burning data and iso images. Toast was always a good third party program - though with iTunes burning ability and disk utility, not sure you need Toast.

I still have that system, eMac with Tiger - 10.4, I use it as a file server :)

I'm using Mountain Lion currently as my main OS, and disk utility is amazing. It should cover all your bases.

I'm not sure why you want something open source.

---

### Post by qyot27 on 2013-03-12
Ripping: vobcopy.  Otherwise, you can actually just use dd to do a straight disc copy if that's what you were really referring to.
Burning: cdrecord (cdrtools).

In both cases, Homebrew has them.  dd is part of the standard Unix userland that Darwin and OSX have by default.

cdrecord is also convenient because if you, say, create the ISO images on another computer and have to transport them over to the Mac on a Flash drive, which depending on filesystem (*cough* FAT) will split large images into multiple files, you can use a shell script to cat the pieces together again and then burn in one go.  That massively streamlines the whole process, and it's less obfuscated than Disk Utility can get at times.

---

