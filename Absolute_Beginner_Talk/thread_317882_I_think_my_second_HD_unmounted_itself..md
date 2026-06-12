---
title: "I think my second HD unmounted itself."
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-12-13
hey people . . .A while ago, I mounted my second hard drive successfully . . .but for some reason it's not showing up anymore . . .is there a way to check if it's still mounted, and is it possible that it unmounted by itself for any reason at all? If it's actually gone, how do I remount it? Thanks.

---

### Post by ]Nbx*cmD[ on 2006-12-13
to check mounted devices just type mount in the console :)

---

### Post by ]Nbx*cmD[ on 2006-12-13
Oh, to re-mount it, just type

```
 sudo mount /dev/hdaXY /media/hdaXY 
```

Where X is the IDE port letter (a,b,c...) and Y is the partition number (1,2,3...)

---

### Post by CheshireMac on 2006-12-13
Hmmm . . .It's showing up . . .I routed it to a file called 'storage', and in console, it shows up as /dev/hda1 on /storage type ext3 (rw). It's the correct drive, and obviously it's routed to the correct folder. My concern was that initially, the second drive showed up in "Computer" as a physical entity, although I couldn't open the actual drive. I had to go to "Storage" for that . . .but now, the drive itself doesn't show up on "Computer", and it made me worry . . .but now that it shows up in mount, does that mean it's still there, and still active?

---

### Post by Scorpuk on 2006-12-13
Did the drive dissapear after a reboot or something?

Also have you edited the fstab file to include the second drive?

when I added my second sata drive I needed to add the following line to my fstab file so that it would be mounted every time the computer booted up:

```
/dev/sdb1    /media/drive2   ext3    defaults,errors=remount-ro 0       1
```

sdb1 being the second drive and /media/drive2 the mounting point.

---

### Post by mcduck on 2006-12-13
If 'mount' shows it, then it's mounted ;)

If you want mounted drives to show on desktop and in 'Computer' you should mount them under /media directory (like /media/storage)

---

### Post by CheshireMac on 2006-12-13
> **Scorpuk said:**
> Did the drive dissapear after a reboot or something?

Also have you edited the fstab file to include the second drive?

when I added my second sata drive I needed to add the following line to my fstab file so that it would be mounted every time the computer booted up:

```
/dev/sdb1    /media/drive2   ext3    defaults,errors=remount-ro 0       1
```

sdb1 being the second drive and /media/drive2 the mounting point.

Yeah. I edited fstab . . .I think you may be right about the reboot. Would it do that? Disappear after a reboot and still be present, functionally?
Thanks for all the help, by the way. I appreciate it, and it's a great learning experience in this community. :)

---

### Post by Scorpuk on 2006-12-13
hmmm if you added the drive into fstab it shouldnt dissapear.

Only if you hadn't would it dissapear on reboot.


can you show us what your fstab file has in it?

If you are still having probs that is. ;)

---

