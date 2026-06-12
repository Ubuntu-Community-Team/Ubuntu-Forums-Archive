---
title: "Syncronize data from usb drive to Hard disk"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-03-06
Hi,

   Is there a GUI version of data sync from USB drive to hard disk (preferably automatic) whenever there is a change between the two folders (USB vs HD).

   If not, is there a command-line version that is easy to execute?

Thanks

---

### Post by kolinab on 2007-03-07
There is a progam many use for similar purposes that is probably what you are looking for. It's called rsync and there is a GUI frontend for it. There's just heaps of options you can set on it as far as how the details of the backing up works. I use it to back up things regularly. One word of caution, be CAREFUL about setting things up to synchronise - i.e. delete files from one when they dissapear from the other. If you're not really careful about what direction this happens in you could be headed for trouble.

Look for Grsync in the repos.

K

---

### Post by in_flu_ence on 2007-03-07
Thanks for that.

---

