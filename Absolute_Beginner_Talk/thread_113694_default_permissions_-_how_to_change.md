---
title: "default permissions - how to change?"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2006-01-06
every file created in my hdd in ubuntu gets executable permissions for everyone, which is a pretty stupid security hole... Maybe that was me who tweaked it somehow? Is there a way to change the default permissions for any newly created files? specifically, I want new files to have rw-r--r-- ...

Is the command supposed to be ```
umask 133
``` or ```
sudo umask 133
``` or both? and, am I correct with the numbers? Don't want to break the system...

---

### Post by darth_vector on 2006-01-06
the default umask is in /etc/profile and is usually 022. for what you want i think it should be 144.

someone please correct me if im wrong... havent done this much

---

### Post by towsonu2003 on 2006-01-07
[QUOTE=darth_vector]the default umask is in /etc/profile and is usually 022[/QUOTE]
mine is 077 (hmmm) but if I give command umask, it returns 0022. which is confusing to me :)
[QUOTE=darth_vector]
someone please correct me if im wrong... havent done this much[/quote] hmm then let me wait for a confirmation, especially about the correct number... thanks for the post, I appreciate it.

---

### Post by racecat on 2006-01-07
It seems kind of odd - there is no man page for umask. Looked it up in an old Unix in a nutshell. Umask numbers are the opposite of chmod as they are a mask - i.e. permissions to be turned off. Here's a breakdown:

umask number /          file permission /             directory permission
0 /                              rw- /                             rwx
1 /                              rw- /                             rw-
2 /                              r--  /                             r-x
3 /                              r--  /                             r--
4 /                              -w- /                             -wx
5 /                              -w- /                             -w-
6 /                              ---  /                             --x
7 /                              ---  /                             ---

Looks like 022 and 133 are the same in relation to files.

Hope this helps,
Bill

---

### Post by towsonu2003 on 2006-01-07
edited: 077 seems ok in /etc/profile then... maybe it's bc I am copying files from FAT32? well, never mind, consider this solved.

thanks for the help :)

---

