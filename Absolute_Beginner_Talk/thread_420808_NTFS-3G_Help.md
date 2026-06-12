---
title: "NTFS-3G Help"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2007-04-23
i tried installing "ntfs-config" so i can write to my windows partition through apt-get, and it didnt work....

then i tried in aptitude, now i get this though after running "sudo aptitude install ntfs-config"

The following actions will resolve these dependencies:

Install the following packages:
libfuse2 [2.4.2-0ubuntu3 (dapper)]

Keep the following packages at their current version:
fuse-utils [Not Installed]
libntfs-3g0 [Not Installed]
ntfs-3g [Not Installed]
ntfs-config [Not Installed]

Score is -4

Accept this solution? [Y/n/q/?]



any ideas? Thanks for the help!

---

### Post by jfinkels on 2007-04-24
> **RMorris78 said:**
> i tried installing "ntfs-config" so i can write to my windows partition through apt-get, and it didnt work....

then i tried in aptitude, now i get this though after running "sudo aptitude install ntfs-config"

The following actions will resolve these dependencies:

Install the following packages:
libfuse2 [2.4.2-0ubuntu3 (dapper)]

Keep the following packages at their current version:
fuse-utils [Not Installed]
libntfs-3g0 [Not Installed]
ntfs-3g [Not Installed]
ntfs-config [Not Installed]

Score is -4

Accept this solution? [Y/n/q/?]



any ideas? Thanks for the help!

run this:
```

sudo aptitude install libfuse2 fuse-utils libntfs-3g0 ntfs-3g ntfs-config

```
That should satisfy the dependencies...see if it works.

---

### Post by RMorris78 on 2007-04-24
The following actions will resolve these dependencies:

Install the following packages:
libfuse2 [2.4.2-0ubuntu3 (dapper)]

Keep the following packages at their current version:
fuse-utils [Not Installed]
libntfs-3g0 [Not Installed]
ntfs-3g [Not Installed]
ntfs-config [Not Installed]

Score is -244



thats what is output.... this makes no sense to me whatsoever! thanks though

---

### Post by jfinkels on 2007-04-24
Try to install ntfs-config using Synaptic. It should show you the dependencies that need to be installed in addition to the ntfs-config package. If that doesn't work, come back here.

---

