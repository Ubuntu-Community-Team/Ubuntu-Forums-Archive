---
title: "Getting rid of Grub?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by roxics on 2006-07-02
How do I get rid of grub? Completely wipe it from my system?

 I just messed up my system and I'm done with linux until I can get a dedicated hard drive for it in a week or so. I've spent over two days trying to get my 160gig drive partitioned right so I can use ubuntu on it and leave the rest of the space for windows XP and it's just not happening. It seems to be a one or the other case. 
So now that I accidently wiped out ubuntu all together on that drive I just wan to get rid of grub too so I can boot into windows again. When I get a dedicated hard drive just for ubuntu I'll come back, but for right now I'm done.

---

### Post by jazzmuzik on 2006-07-02
Do you have a dos boot disk? I've heard you can do a "fdisk /mbr" and that will wipe the boot sector.


mbr = master boot record

---

### Post by roxics on 2006-07-02
Do I still need to use a windows XP disk even if Ubuntu was not installed on the same hard drive XP was on?

Xp is on my HDD1 and Ubuntu was on my 4th hard drive.

---

### Post by bigken on 2006-07-02
boot form win xp disc when promted press R for recovery console select win partion usualy 1 then addmin password if you have 1 if not just press enter then type fixmbr then fixboot then type exit reboot you should back into windows

---

### Post by roxics on 2006-07-02
Thank you very much. Worked great. Except I did fixboot and fixmbr in reverse. Guess it doesn't matter.

---

