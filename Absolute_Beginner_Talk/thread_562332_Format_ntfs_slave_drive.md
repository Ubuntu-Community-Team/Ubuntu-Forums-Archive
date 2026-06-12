---
title: "Format ntfs slave drive"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-09-28
I want to format my slave drive, ntfs, I want read and write priveleges, however, gParted will not let me delete the drive, I cannot enable any functions through the menus or by right clicking, any ideas? I'm using 7.04 ubuntu, amd proc. Thanks Mark.

---

### Post by mandrill on 2007-09-28
I just did this - with help - format as fat32 - see [http://ubuntuforums.org/showthread.php?t=560865](http://ubuntuforums.org/showthread.php?t=560865), and good luck!
linux cannot write to ntfs....

---

### Post by prodigalson666 on 2007-09-28
Thanks for the reply however as I stated gparted will not let me alter the drive, it just provides info about the drive, hence my problem.

---

### Post by mandrill on 2007-09-28
What I did, after fumbling around for 1/2 hour, was just tell it to format the drive as fat32, and, it did the rest - no hassle...

---

### Post by prodigalson666 on 2007-09-28
The only buttons it is allowing me to access is information and unmount. Right clicking does give me a menu obviously, but I cant select any of the options, Scrolling along the menu tabs only allows a few buttons that I can select, so I am going to assume I have to unmount the drive first? Because there is obsolutely no other buttons that I can select, I can see the a;; the options through the drop boxes but I cant select them, except for the two options I have already stated. Thanks for your help so far! Mark

---

### Post by mandrill on 2007-09-28
just curious, and very simple, but I would have overlooked it if it wasn't pointed out to me, did you make sure to select the correct drive in the top right-hand corner? I do not think you want to unmount, as that would prevent the task at hand?

I just opened gparted to remember what i did, - just highlight the partition, right click, choose fat32, and away you go - it automatically reserves space for the system files, etc...actually pretty slick - although if you have a lock symbol next to the drive name, you may in fact have to unmount - as I said, I just did it - for the first time - 2 days ago....

---

### Post by prodigalson666 on 2007-09-28
Tried that still no options, the only thing I can do is unmount and try to load again. I'm wondering, when I wanted to delete my slave drive or a partition in windows I would pop in the cd go through the start up motions, without actually installing windows and delete the partion or hd that way, couldnt I just do the same thing with the ubuntu dvd?

---

### Post by mandrill on 2007-09-28
The drive will not unmount? gotta admit, I'm no expert, but....sounds strange. Are you able to access the drive? does it have to be manually mounted each boot?
 
There's always the hand-grenade approach -  download UBCD, the "ultimate boot cd" as iso, burn it, boot with it, format it. Assuming you have, as I do, another pc......

---

### Post by prodigalson666 on 2007-09-28
Im in the process of burning off all the stuff I want from the drive right now so I cant unmount yet to see what will happen. I will get back to you though if youll be around.Thanks

---

### Post by mandrill on 2007-09-28
will be around - have fun - it took me awhile to figure everything out - but now my 300gb slave automounts in my home folder, as "media" on sdb1 - very sweet

---

### Post by prodigalson666 on 2007-09-28
Same here, my slave is a 300gb, and I never had a problem finding or using it, its always there under local media, I just need to eliminate the ntfs so I can use it in linux, I'll let you know after I finally get everything burnt off. Thanks

---

### Post by prodigalson666 on 2007-09-28
Ok, I unmounted and now I have a plethra of choices, what should I format it to?

---

### Post by mandrill on 2007-09-28
after some poking around, found out there is a gparted disk - possibly google - claims don't have to mount/unmount anything...check it out, I may do the same for future....

---

### Post by prodigalson666 on 2007-09-29
Thanks for all your help, it worked!

---

