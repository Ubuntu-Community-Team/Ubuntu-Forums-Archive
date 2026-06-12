---
title: "Can't re-install Ubuntu"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by PurpleZoe on 2007-11-02
Peace

I had a computer glitch awhile back that cleared my hardrive apparently and made it impossible for me to reinstall Ubuntu. I tried get help after reporting the bug, but couldn't find any and decided to run the live cd until Gibbon came out.

I have the new Gibbon cd now, and it's doing the same thing.
It stops when it comes to the partition and tells me there's no root definition.
No matter what I try within my limited Noobie reasoning, it won't go past that point.

At this point I'm stuck running it live, which means I operate from the memory size of my pc.

I loathe Windows and refuse to go back to them.

I have no idea what to do however.

Can anyone help?

Thankyou for your consideration and Happy Friday.

---

### Post by rudeboyskunk on 2007-11-02
Ok, first of all, make sure your hard drive's cable connections are *securely* connected, including the power.

If it still does not work, you might want to insert a Windows boot floppy, get to the dos prompt, and just type "format c:".

---

### Post by prodigalson666 on 2007-11-02
It sounds like its waiting for you to assign the mount point for your root partition. If you are going to use your entire hard drive choose the guided partition option and will take care of all your partition problems ( root, swap and main hard drive). If this doesnt work I usually pop in xp, go through the setiup, when it asks you which drive you want to install xp, delete all your partitions and or hard drives, when thats done take out xp, reboot and you'll have a real fresh install of ubuntu. There'll be no leftover garbage from any previous o/s'.

---

### Post by prodigalson666 on 2007-11-02
Sorry I should ammend the previous, when you reboot after deleting your hard drive, reboot with ubuntu and start the reinstall over again.

---

### Post by PurpleZoe on 2007-11-02
Ah Many thanks!
The reinstall was a success after I put in a Windows OS and deleted the previous partitions.
I attempted to use the /dev/zero command to format the hd but the terminal said permission was denied... 

:) Have a good 1 ^_^ I know I will... To think I could have done this a month ago.

---

