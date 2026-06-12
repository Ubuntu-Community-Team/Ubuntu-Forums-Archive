---
title: "install and partition questions ?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by New2Linux0319 on 2008-03-30
hi,
couple quesitons here please:   

(using Ubuntu 7:10 and a couple of "beginning ubuntu" guide books)

1) last night i booted from the live cd in order to remove all my Linux partitions ( i wanted to remove linux and then reinstall from a clean fresh drive with only windows xp and free space just like the first time)

this morning when i turned on computer it would not boot:  error 22  grub something...
i thought that after removing the linux stuff, it would just go back to automatically booting into windows xp like before...

this issue is not addressed in either of my linux books.
comments?

2) now i am installing linux Ubuntu 7:10 again and have partition questions.  i wanted to install like this:
ntsfs (windows xp)  60GB
/                             7GB
/home                     5GB
swap                      3GB
free space               7GB  

could you explain difference between  "primary" and "logical" partitions?

thanks

---

### Post by ASchweitzer on 2008-03-30
To address the GRUB error 22:
GRUB is your bootloader (the text-based OS selection screen that pops up on boot after you install ubuntu) It is installed on the Linux partition by default, so when you erased the Linux partition you erased your bootloader (hence the error). To fix this boot from your windows CD and go into the repair console, select your windows install and type:
```
fixmbr
```
This will fix your Master Boot Record and reinstall the windows bootloader.

---

### Post by Moop on 2008-03-30
A logical partition is contained within an extended partition. A primary partition isn't. You can only have four primary partitions but you can have as many logical partitions as you want. Ubuntu and XP both work fine on logical or primary partitions.

---

