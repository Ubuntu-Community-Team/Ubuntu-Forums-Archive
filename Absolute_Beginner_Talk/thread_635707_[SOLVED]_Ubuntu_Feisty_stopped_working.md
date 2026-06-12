---
title: "[SOLVED] Ubuntu Feisty stopped working"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2007-12-09
Hello,

So, for several months I have been running Feisty and XP in a dual boot situation. My system has two gigs of memory, two hard drives, and an AMD 64 bit processor. Today, Feisty stopped working. I came in to find that it had shut itself down, and that it was showing me the following error message:

fsck died with exit status 4

* An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.

bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program apt-get is not currently installed. You can install it by typing: apt-get install apt
root@username:


Obviously, I can't use apt-get to install apt. So, I exited this screen, restarted the computer, and each time I did so it returned to the above screen. In XP, I can still see all of the data that resides on the Ubuntu hard drive, so it doesn't appear to have lost anything, at least from the /home partition.

Anyone have any ideas as to what might have happened here, or what I need to do next? Fortunately, I can still see the data as I said, so I guess I could back up the home partition and reinstall Ubuntu if necessary. Other solutions?

Thanks so much for any thoughts.
Jonathan

---

### Post by Natr0n on 2007-12-09
> **flamingsole said:**
> 
* An automatic file system check (fsck) of the root filesystem failed. **A manual fsck must be performed, then the system restarted**. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

Start up your computer again and when that screen comes up type```
fsck
```which will start a **f**ile**s**ystem **c**hec**k**. I don't know if your computer will be able to recover but that's the next step you need to take.

---

### Post by flamingsole on 2007-12-09
Perfect. I ran fsck twice, and everything was perfect. One of the messages it gave me was about the Trash folder. Now in retrospect I remember trying to remove a file from the Windows (NTFS) drive through Feisty, which logically could have caused an issue. Thanks so much for your help.

Jonathan

---

### Post by Natr0n on 2007-12-09
No problem. Just glad you were able to get up and running again. :)

---

