---
title: "Overwriting Hard Disk with 0s!"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Adjutant on 2006-12-25
Hi guys. Haven't been here in a long time. Anyways, I been interested in deleting my hard disk really good since I'll be selling it off and I just want to make sure nothing is recoverable in the future, like personal info, etc.

I came across a solution that sounded fairly easy and basically involved linux and overwriting the whole hard disk with 0s.

Someone gave this short line of info as to "how it's done."

```
# dd if=/dev/zero of=/dev/hda bs=1048576
```

I'm an absolute beginner, I can't tell what this line means. But the real problem is, how do I execute this task? I know I'd need to boot up a Live CD first, but something tells me copy+pasting that line wouldn't work quite perfectly. I know I'd need to change some stuff first to match my PC in particular but don't know what.

---

### Post by JamesWP on 2006-12-25
Load up a live CD, throw open a terminal, choose the HDD you wish to Low Level Format (list of HDDs can be seen by running '_sudo sfdisk -l_'), once your drive name is determined, simply run ```
sudo dd if=/dev/zero of=/dev/hda bs=1M
```

replacing '/dev/hda' with the drive you wish to format.

---

