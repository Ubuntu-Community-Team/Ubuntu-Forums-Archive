---
title: "usb cd drive detected but not working"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by dronug on 2005-11-04
i have a hp usb cd burner that im trying to use with ubuntu.  it shows up in my computer with file system and everything, but when i put a cd in and try to open it says unable to mount the selected volume

also when i copy files to a floppy on ubuntu pc and try to view them on a xp pc thay dont show up, and the disk has full memory 1.3 mb.
but if i copy files from xp in view them on ubuntu works fine.

---

### Post by speckman on 2006-02-11
hey, me and a friend are having a similar problem with our usb-cd burners, but i got an answer for your floppy question:

wait a while.?

i copied files in the command line, to /media/floppy0.  i watch the green light and listen for the sound of the floppy drive.  it won't start copying files until 10-20 (?) seconds after the command.  if you "ls /media/floppy0" before then, it'll show them as being there, but i guess the task is just sitting in a queue.

this is incredibly stupid, in my opinion.  i mean counter-intuitive.  it's like the floppy copy command has the lowest priority in the universe, when in reality, it's the highest priority for a user.

good luck with the usb cd drive.

---

### Post by bartbes on 2006-02-11
Well actually I had that first as well (but it wasn't with an usb cd burner) try to download/update pmount, this makes that you don't have to be root to mount something, that got my automount working!

---

