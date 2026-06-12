---
title: "How do I format a thumbdrive"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by linuxuser28 on 2006-09-11
Not sure how to format a thumbdrive or a floppy in Ubuntu.

---

### Post by bulldog on 2006-09-11
Just put it in your computer and right click and choose format.

---

### Post by Najand on 2006-09-11
Formating using:
$ fdformat <device>
is also possible

---

### Post by linuxuser28 on 2006-09-11
Actually I wont need the floppy (looks like it does not work anyway). But when I right click the thumbdrive icon there is no option listed for formating it.

---

### Post by bulldog on 2006-09-11
Go to your media folder and see if it's there.

Right click there and there should be the format option.

Just have a look and you can format it in GParted.
Your'e right there's no option to format in your media folder either.

---

### Post by Najand on 2006-09-11
You can use gparted to format a hard disk (including USB Flash memories, etc) too... You have to find your desirable device (which usually is like /dev/sd* ) on top right of the window and then right click for more options... Be careful not to format your linux file system.

---

