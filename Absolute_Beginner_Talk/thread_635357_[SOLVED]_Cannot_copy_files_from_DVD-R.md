---
title: "[SOLVED] Cannot copy files from DVD-R"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Tabenx on 2007-12-08
I recently performed a backup of some files to dvd because i had to reinstall ubuntu because of an issue. The only problem is that after i reinstalled the os and everything, all the files on the dvd are read only. I thought i could get around this by going root on nautilus and then going to the dvd but that didn't work. Any ideas?

---

### Post by nsilva on 2007-12-08
Did you try the command line? Assuming your dvd is mounted under /media/cdrom

Go to the folder you want to download your files at, lets assume tmp

```

cd /media/cdrom
cp * /tmp

```

make sure your dvd is mounted, when you are inside /media/cdrom, try using ls to make sure you can see files.

---

### Post by lintoon on 2007-12-08
You cannot edit the files on the DVD-R.  You have to copy the files from the DVD-R onto your hard drive before you can edit them.

---

