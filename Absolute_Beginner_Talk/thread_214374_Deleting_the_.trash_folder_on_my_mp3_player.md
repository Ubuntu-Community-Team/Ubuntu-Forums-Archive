---
title: "Deleting the .trash folder on my mp3 player"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by suver.17 on 2006-07-12
Ok, i'm sorry I keep posting.  Anyways, I can view the .trash folder that was put on my iRiver mp3 player.  When I go to delete the folder, it tells me for every single file in the .trash that it is a read-only file, and wont let me delete it.  Why is this happening? How do I fis it?  I never had this problem before I updated to Dapper Drake.

Thanks again,
Jared

---

### Post by richbarna on 2006-07-12
> **suver.17 said:**
> Ok, i'm sorry I keep posting.  Anyways, I can view the .trash folder that was put on my iRiver mp3 player.  When I go to delete the folder, it tells me for every single file in the .trash that it is a read-only file, and wont let me delete it.  Why is this happening? How do I fis it?  I never had this problem before I updated to Dapper Drake.

Thanks again,
Jared

Are you dual-booting with windows? If so, put it in a windows pc, choose show hidden files and delete it.
There may also be a small switch on the mp3 player case that locks or unlocks the drive.

---

### Post by The Noble on 2006-07-12
Same thing happens on my usb flash. The way to get around it is by navigating to the drive through the terminal, and trying

```

sudo rm -r .trash

```

That will delete it. The reason it won't delete is permissions. Also under properties of the folder, look under permissions. If you can modify it to be written and read by everyone, you can remove it through nautilus.

---

### Post by Endow on 2006-07-12
This happens to me too...but why?Why is a .trash folder even created?

---

### Post by richbarna on 2006-07-12
> **Endow said:**
> This happens to me too...but why?Why is a .trash folder even created?

I had the same with my memory stick for my digital camera. It seems that when you delete the photos from linux, it just creates a trash folder on the same drive. Whereas windows moves the files to the trash can on the C drive.
As I said before, I just delete everything from windows instead of Linux.

---

