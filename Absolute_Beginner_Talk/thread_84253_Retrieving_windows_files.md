---
title: "Retrieving windows files?"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by Ski1215 on 2005-10-30
I installed linux the other day, and the only process I wasn't very surea bout was creating/ and erasing partions of my HD. I'm wondering if there is a way that I can retrieve files from windows? I have some school documents that are really important, like papers that I have to update on a weekly basis. Is it possible to get them via linux? If not, when I reinstall windows will I start from ground zero again with none of my files?

---

### Post by matthewv on 2005-10-30
If you left your windows partition in place, it can be read from (but not written to) by linux. Can you see your windows partition from linux???

---

### Post by Kapre on 2005-10-30
[QUOTE=Ski1215]I installed linux the other day, and the only process I wasn't very surea bout was creating/ and erasing partions of my HD. I'm wondering if there is a way that I can retrieve files from windows? [/quote]

If you did not delete your windows partition (meaning you did not choose "erase entire disk and install ubuntu" in the installation process), YES you can still get your files from your windows partition.

>  I have some school documents that are really important, like papers that I have to update on a weekly basis. Is it possible to get them via linux? If not, when I reinstall windows will I start from ground zero again with none of my files?

As what Mattewvy stated above, you can still get it. If the M$ was set on FAT32, you can Write on it and Get files from it. You just have to mount it by using [THIS]("http://www.ubuntuguide.org/#mountunmountfat") from the guide. If it was set on NTFS, you cannot Write on it but you can still Get files from it by again mounting it and using the guide above.

K :smile:

---

