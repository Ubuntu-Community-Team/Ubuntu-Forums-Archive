---
title: "&quot;sudo mount /dev/cdrom /mnt/cdrom &quot; doesn't work anymore"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-09-07
hello,
I used to be able to access my cd-rom drive (with a cd in it) by doing "sudo mount /dev/cdrom /mnt/cdrom". But then I installed ivman, because I was told it would take care of automounting the CD-Rom drive for me. But when ivman didn't work, I uninstalled ivman. I rebooted/restarted the computer, and i tried 
"sudo mount /dev/cdrom /mnt/cdrom", but it no longer works. In the terminal, after entering my password and pressing "Enter", the cursor just goes to the next line, with no printout. It just stays there forever. When I look at the CPU systems resources, it looks like the CPU is not being used.


Help.

---

### Post by erikringmar on 2006-09-19
Did you get a reply to this?  I have the same problem ...

---

### Post by hanzj on 2006-09-19
erik,
 i forget what i did to make things work. it's been quite some time since i've used my cd-rom drive. have you tried rebooting? did you install ivman? if so, try uninstalling ivman and rebooting.

---

### Post by rene86 on 2006-09-19
the directories for the drives are in /media , so:
```

sudo mount /dev/cdrom /media/cdrom

```
should work.

if you don't want to use /media/cdrom you can make a link:

```

sudo rm /mnt
sudo ln -s /media /mnt

```

Know /media and /mnt are the same.

---

