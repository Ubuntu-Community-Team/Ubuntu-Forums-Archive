---
title: "please, i desperately need help with GRUB"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-04-11
I installed Ubuntu, but the slider confused me, during the install, so I only gave my XP machine 15gb and i wanted that to be Ubuntu, so I went into windows and I just deleted the partitions and added them back to windows, well, when I restarted, GRUB says there is an error and I need help please, even a link to somewhere that can help..

---

### Post by ljpm on 2007-04-11
Boot your machine with XP CD and remove GRUB from MBR with fixmbr from the CD.

---

### Post by nintennuendo on 2007-04-11
I have to go to work, in like 4 minutes, but I boot using my XP cd, go to the desktop and use the fixmbr?  or is that on the cd, or what?  I would really not like to have to reload windows again on this computer, as it would be the fourth time so far this year.

---

### Post by justleen on 2007-04-11
> **ljpm said:**
> Boot your machine with XP CD and remove GRUB from MBR with fixmbr from the CD.

choose Repair during the XP setup, once done loading you get a DOS like screen, and enter fixmbr..


alternativly, reinstall Ubuntu :) (im guessing you deleted those partitions)

---

### Post by seshomaru samma on 2007-04-11
boot from the windows cd\
choose 'rescue mode
in rescue mode put the command ```
fixmbr
```

---

### Post by antoz on 2007-04-11
You obviously got rid of grub by deleting the ubuntu partitions and need to fixmbr as was said in the other posts
Check out the link below it gives a lot of good advice about this.

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

PS: You may want to create your partitions manually next time that way you have more control, I know the same thing happenned to me the first time i tried to install, but somehow I had a funny gut feeling and aborted the install, I then resized my Window partition with Gparted on the live CD

---

### Post by nintennuendo on 2007-04-11
I do not get any recovery console option on my CDs, my laptop and OS came from eMachines and it has some pc angel recover junk.  is there any way I can use a floppy disk to get into dos?

---

### Post by confused57 on 2007-04-11
> **nintennuendo said:**
> I do not get any recovery console option on my CDs, my laptop and OS came from eMachines and it has some pc angel recover junk.  is there any way I can use a floppy disk to get into dos?
Yes, you can make a Win98SE oem boot floppy:

[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method)

---

