---
title: "Crash???"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by FriscoZR on 2007-07-11
Hi all,
Not sure what's happened here and what I should do about it - Please advise...

This is what is on the screen:

   /dev/dsa1: UNEXPECTIED INCONSISTENCY; RUN fsck MANUALLY.
               (i.e., without -a or -p options)
   fsck died with exit status 4
   
       An automatic file system check (fsck) of the root filesystem failed.
   A manual fsck must be performed, then the system restarted.
   The fsck should be performed in maintenance mode with the 
   root filesystem mounted in read-only mode.
    * The root filesystem is cuuently mounted in read-only mode.
   A maintenance shell will now be started.
   Afer performing system maintenance, press CONTROL-D
   to terminated the mainenance shell and restart the system.
   bash: no job control in this shell
   bash: groups: command not found
   bash: lesspipe: command not found
   bash: The: command not found
   The program 'apt-get' is currently not installed. You can install it by typing:
   apt-get install apt
   bash: apt-get: command not found
   bash: dircolors: command not found
   bash: The: command not found
   The program 'apt-get' is currently not installed. You can install it by typing:
   apt-get install apt
   bash: spt-get: command not found
   root@cfp-server:~# _

That's it...  What does all this mean? What should this nube do?
Thx,
Matt

---

### Post by Inxsible on 2007-07-11
Pop in your LiveCD. Then boot thru the liveCD and Go to Applications --> Accessories -- > Terminal
 
type in ```
fsck /dev/sda1
``` That should hopefully fix it !

---

### Post by FriscoZR on 2007-07-11
Thanks for the quick repsonse. I'll give that a shot and report back later.

---

