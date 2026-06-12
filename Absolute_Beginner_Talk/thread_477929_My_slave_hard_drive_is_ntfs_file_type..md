---
title: "My slave hard drive is ntfs file type."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-06-18
What is the command to have Ubuntu read ntfs files?

---

### Post by st33med on 2007-06-18
It can already read ntfs files. Just have to go to Computer and click on the  **.* Volume.

however, if you want to write as well, follow [this thread]("http://ubuntuforums.org/showthread.php?t=217009&highlight=HOWTO+ntfs") to get it to write.

---

### Post by vexorian on 2007-06-18
Feisty fawn:

Ubuntu should handle ntfs partitions "out of the box"

If you are trying it from the live-cd then it is most likely not detected yet. Doing some stuff might trigger the detection, for me it was going to the partition editor.

If you already got Ubuntu installed then it could be that the ntfs partition was logical. You will need a package called "ntfs-conf"

```

sudo apt-get install ntfs-conf
```

Or should you prefer a GUI you can just look for that package in synaptic manager, after it installs you can open ntfs-conf from the menu\system write your password and it should detect your ntfs partitions.

You might enable write support, but that isn't necessary for you, I wouldn't really recommend it either, although my bad experiences with ntfs write support happened a while ago, it could be fine now.

---

