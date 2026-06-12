---
title: "chkdsk ntfs from linux?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-09
hi i have no cd burner or windows cd.

i get error..

ntfsresize v1.13.1 (libntfs 9:0:0)
[COLOR="Red"]ERROR: Volume is scheduled for check.
Run chkdsk /f and please try again, or see option -f.[/COLOR]

how can i do chkdsk from Ubuntu?

i tried:

root@Darkstar:/# fsck -f /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1

how can i fix this?

Many thanks...

---

### Post by jspangler on 2007-08-09
To the best of my knowledge, your ntfs partition will always be marked with a force check unless you run chkdsk in windows (or possibly just attach to a computer with windows and boot reboot twice. I had this problem to. You can check for errors, but if you want to see your data you are going to have to force the mount, with the "force" option. I did this for a while but it made me scared. I wouldn't do it if you absolutely can't lose the data.

---

### Post by splintercellguy on 2007-08-09
I think the OP is trying to resize his NTFS partition. I suggest obtaining an XP LiveCD (legality questionable) from a torrent and then invoking chkdsk.

---

### Post by Cypher on 2007-08-09
You are not going to be able to run a chkdsk from Linux on your NTFS partition. That's probably not a good idea anyway. Your best bet is to somehow get a XP CD so that you can get intot he Recovery Console and run the command..

---

### Post by Hopeless on 2007-08-10
ntfsresize --no-action -s 5870M /dev/hda1

how can i add a -force command on this?

because i used gparted after and stuffed it...it reset the Current volume size...all the info is there...just wondering what would happen if i did it again...

---

### Post by Hopeless on 2007-08-10
ntfsresize --no-action --force -s 5870M /dev/hda1

cool.... im learning linux!!!!

---

