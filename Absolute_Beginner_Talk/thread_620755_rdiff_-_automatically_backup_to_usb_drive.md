---
title: "rdiff - automatically backup to usb drive"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by rygar on 2007-11-23
i would like to sync data on my hard drive to my usb flash drive.
it appears rdiff is a good solution for this, though i haven't tried it yet.

my question is, how can i get it so that every time i insert the drive on this computer, it will automatically sync?

---

### Post by bluepowder7 on 2007-11-23
bump, because i'd like to know as well.

---

### Post by banewman on 2007-11-23
Personally I'd use rsync
Open a terminal and type -
man rsync
That will give the manual for the program. It's an interesting way to backup. I'm going to explore this further. :)

---

### Post by banewman on 2007-11-23
I new I'd seen a how to on this before - 
[http://mylinuxnotes.wordpress.com/2007/09/19/howto-backup-to-a-usb-drive-and-sync-two-computers-w-rsync/](http://mylinuxnotes.wordpress.com/2007/09/19/howto-backup-to-a-usb-drive-and-sync-two-computers-w-rsync/)
Hope it helps. :)

---

### Post by rygar on 2007-11-23
well, i'd like to stick with rdiff if possible.

it's mostly documents, and web sites i am working on.  rdiff is useful in that it only copies the differences between files, and will allow me to revert to a previous stage if necessary.

regardless, i'm not sure how "man rsync" or the above link help me accomplish what i'm trying to do, but maybe i'm missing something...

to clarify, i don't want to have to go to the console and type a command every time i insert my usb drive, i'd like it to sync automatically.

---

