---
title: "Ubuntu 6.1 cant view GIF animation"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mocqueanh on 2007-10-28
I'm using Ubuntu 6.1, today, when i try viewing an GIF image, i can see it on Ubuntu, but i cant see the animation of the image.


And one more question of newbie: Sorry, few months ago, i have to come back to Windows because of my work. So i forgot many commands in Linux. Now i want to write to NTFS file system in my Windows partition, but by default, Ubuntu only read, cannot write.
How to do ? I want Ubuntu auto mount Windows partitions at startup.

---

### Post by Delkster on 2007-10-28
> **mocqueanh said:**
> Now i want to write to NTFS file system in my Windows partition, but by default, Ubuntu only read, cannot write.
How to do ? I want Ubuntu auto mount Windows partitions at startup.

There's a least some improvement in NTFS write support in the latest 7.10 release that came out about a week ago. You can probably get NTFS write support working also in 6.10 somehow through FUSE but upgrading to 7.04 and then to 7.10 might be a good idea if you really need NTFS write support.

I don't know if the partitions are auto-mounted read-write, though.

---

### Post by argie on 2007-10-28
> **mocqueanh said:**
> I'm using Ubuntu 6.1, today, when i try viewing an GIF image, i can see it on Ubuntu, but i cant see the animation of the image.
...

Try opening it in Firefox. If the default image viewer opens it, it will not animate. To make Firefox the default for .gif files, right click on one of the files, open the Properties window and then go to the 'Open with' tab. Then select Firefox by making sure that its radio button is the only one selected. Then close that dialog. All should be well now.

---

