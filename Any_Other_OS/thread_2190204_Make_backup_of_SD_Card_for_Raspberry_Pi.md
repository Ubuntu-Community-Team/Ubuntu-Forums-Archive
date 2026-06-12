---
title: "Make backup of SD Card for Raspberry Pi?"
date: 2013-11-26
forum: Any Other OS
---

### Post by NilPointer on 2013-11-26
Hello. I need to make a backup of 32 GB SD Card. What is the best way to do that and get a compact image? I use this SD Card for my Raspberry Pi. I need to make a full system backup to have some freedom, so that if I screw something up, I'll have an easy way to fix it.

I need to make backups on my Ubuntu Desktop. I don't think rsync will work for that purpose, since it only syncs files between 2 dirs. Also, plain dd doesn't work for me, too, because it will produce 32 GB image, while only about 5 GB is really used, so each image would waste about 25 GBs, which is unacceptable.

I'm sure there must be a way to make a full-drive compressed backup. Can anyone point it for me, though?

---

### Post by howefield on 2013-11-26
Clonezilla ?

---

### Post by NilPointer on 2013-11-26
Well, Clonezilla is LiveCD. It would be perfect if there is something that works from Ubuntu.

By the way, just confirmed that rsync doesn't work for system backup. Just tried to rsync-format-rsync, now Pi doesn't boot. Well, anyway I've planned to reinstall OS from scratch.

Looks like full imaging is only way to go.

---

### Post by mips on 2013-11-26
> **NilPointer said:**
> Well, Clonezilla is LiveCD. It would be perfect if there is something that works from Ubuntu.

By the way, just confirmed that rsync doesn't work for system backup. Just tried to rsync-format-rsync, now Pi doesn't boot. Well, anyway I've planned to reinstall OS from scratch.

Looks like full imaging is only way to go.

dd?

---

### Post by NilPointer on 2013-11-26
Hm, looks like rsync works after all... If I don't format partition, keep original volume label and restore all files onto it with rsync - system boots after all. So, I think I will stick with rsync, as it copies only files and not the free space.

---

