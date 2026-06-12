---
title: "my missing file system space"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by ashley1987 on 2008-04-16
being completely new to linux, can someone help me? I have installed ubuntu gutsy and im doing some housekeeping.

i have about a 20gb partition, filesystem type ntfs, i have just deleted about half of my media files (mostly wma some m4p, mp3, etc) and now it reads 3675 files totalling 10.6gb. Yet it also says 19.8gb used, 600mb free. There is nothing in trash and no other visible files or folders on the partition outside of this 10.6gb media folder. What is eating the extra space and how can i free it?

Thanks in advance

---

### Post by st33med on 2008-04-16
Hrmmm... I am confused. Are you saying that you deleted stuff inside a Windows XP partition from Ubuntu?

---

### Post by Oldsoldier2003 on 2008-04-16
> **ashley1987 said:**
> being completely new to linux, can someone help me? I have installed ubuntu gutsy and im doing some housekeeping.

i have about a 20gb partition, filesystem type ntfs, i have just deleted about half of my media files (mostly wma some m4p, mp3, etc) and now it reads 3675 files totalling 10.6gb. Yet it also says 19.8gb used, 600mb free. There is nothing in trash and no other visible files or folders on the partition outside of this 10.6gb media folder. What is eating the extra space and how can i free it?

Thanks in advance

look for a hidden folder on the ntfs partition. In nautilus press ctrl+H. you could have a hidden .Trashxxx folder on the partition

---

### Post by ashley1987 on 2008-04-16
thanks people, it was in a hidden folder on the partition. shift-delete ...huzzah! me feeling slightly silly :)

---

### Post by quill7111 on 2008-04-26
Wow, thanks. That was a much easier answer than I expected.

---

