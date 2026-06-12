---
title: "USB not persistent"
date: 2012-05-15
forum: Any Other OS
---

### Post by ChameleonQS on 2012-05-15
I made a persistent USB but after I shut down and boot back to the USB it forgets all my settings or saved files. So every time I boot to the USB its like starting anew. Is it supposed to be like this? if not is there a solution?

---

### Post by nothingspecial on 2012-05-16
*Thread moved to **Other OS/Distro Talk**.*

Backtrack 5 tag

---

### Post by codemaniac on 2012-05-16
Did not you by chance forget to set size for "persistence"?

---

### Post by sudodus on 2012-05-16
- What tool did you use to create the USB boot drive?
- And as codemaniac is asking: how did you set the persistence?
- Do you have any casper-rw file or partition? Is it formatted?
- Did you add **persistent** as a boot option?

Have a look at the following thread (particularly the last post)
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

After working with that thread I have learned that it is actually easier and more stable to use a casper-rw partition instead of a file. It works well at least with *ubuntu 12.04.

---

### Post by ChameleonQS on 2012-05-16
i tried the way on the link but had no luck so from my new gained knowledge on this topic i did some googling and found this [http://www.backtrack-linux.org/wiki/index.php/Persistent_USB]("http://www.backtrack-linux.org/wiki/index.php/Persistent_USB")
it helped me
Thanks a lot for the help sudodus

---

### Post by ChameleonQS on 2012-05-17
> **sudodus said:**
> - What tool did you use to create the USB boot drive?
- And as codemaniac is asking: how did you set the persistence?
- Do you have any casper-rw file or partition? Is it formatted?
- Did you add **persistent** as a boot option?

Have a look at the following thread (particularly the last post)
[[COLOR=Red]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

After working with that thread I have learned that it is actually easier and more stable to use a casper-rw partition instead of a file. It works well at least with *ubuntu 12.04.

Well here I am again lol. The way that I did it on my last post made everything run EXTREMELY slow, so I came back and tried your way again. Works perfectly.

[Solved]

---

### Post by sudodus on 2012-05-17
> **ChameleonQS said:**
> Well here I am again lol. The way that I did it on my last post made everything run EXTREMELY slow, so I came back and tried your way again. Works perfectly.

[Solved]
I'm glad it works for you :KS

---

