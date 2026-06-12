---
title: "usb hd unclean --&gt; failed to determine mount point"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by larrybrazos on 2007-03-21
i was following the tutorial to enable read/write to my usb hd formatted as ntfs and i hit the power button like a dummy and now it is unclean and fails to determine mount point.

i plugged it in to my windows laptop and it has no problems, did a check disk and properly shut it down, but when i plug it back in to linux it is still unclean.

last time this happened, i had no data on it so i just reformatted, no big deal.

now i have data, how can i clean the drive and preserve the data?

---

### Post by i.am.canadian on 2007-03-21
Hi there.

Easiest thing to do would be to copy all your data to your windows machine, wipe the drive in linux, and then copy the data back to the drive if you want it on your linux system.

However, if that is unsatisfactory, you should mount the drive and run fsck on it from the terminal.  I had a scare where my laptop wouldn't boot because of some corrupted files and I had to sit through a manual fsck to get it running again, but it did.  Be warned it could take a while depending on how big your disk is, and as far as I remember, it requires your attention as you need to say yes or no (just say yes).

Anyway, that's my two cents, hopefully someone else may prove more helpful.  Cheers.

---

### Post by larrybrazos on 2007-03-21
thanks for the advice, but i can't mount the drive to run fsck on it.  i have added like 130g in the last couple of days and that would be a hugh pain to pull everything off, reformat, and move everything back over.  and what happens if this sucker is full (500g) and my friggin cat jumps up and hits the power button for revenge because i hadn't given him enough treats one night?!!? then what?  anyone else know a way to repair without reformatting.

i have tried ntfsfix, but that doesn't work either.

---

### Post by larrybrazos on 2007-03-21
ummmmmmmmmmm . . .

not sure what happened, haven't been messin with it for a couple hours now, and whatda know, it is mounted and has read/write.

guess a reboot or just igving it some time, not sure

---

