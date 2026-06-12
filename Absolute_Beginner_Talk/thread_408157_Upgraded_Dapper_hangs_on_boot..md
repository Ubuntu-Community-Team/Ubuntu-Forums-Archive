---
title: "Upgraded Dapper hangs on boot."
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jhineman on 2007-04-13
A couple of days ago I upgraded from 6.06LTS to 6.10 without a hitch from what I could tell.  After giving the go ahead for a restart I found that I was no longer able to boot my system.  

I've tried various 'kernel' options in grub that I've read elsewhere in the forum (verbose, *removing* splash quiet, vga=791) with various kernels available on the system.  Before the upgrade the system was working fine (sans issues I had related to trying to get an smp kernel working, and some annoyances with monitors and xorg).  

When booting under the verbose setting I get a long stream of stuff that's moving faster than I can read and finally I get 'begin init-bottom' (which completes by the look of it) and then one or two more lines and then the thing hangs.

I guess I could break up my questions like this:
1.  Is there anyway to tinker more with how linux is booting than the simple options in grub (or a guide to do more complicated things in grub)?
2.  If everything is hopelessly hosed, is it possible to access volumes with a liveCD to get certain files?

---

### Post by devnulljp on 2007-04-13
best bet is going to be to boot into recovery mode and see if you can fix things there.
Answer to 2. is yes. You can boot from live cd and mount your hdd partitions and edit things there. 

When you say it hangs, what does that mean? Could it just be X that's hosed? (cntrl-alt-F1 should dump you to a terminal in that case and you can fix X relatively easily).

---

### Post by jhineman on 2007-04-13
I'm thinking getting a live cd going will be next on the list.  (we'll see if I can get fuzzy protective stuff enough out of the way to get my powerbook to eject a cd).

I've tried booting in recovery mode (in various kernels) ultimately (and similarly 'verbose') I end up in the same basic place, somewhere after "begin: init-bottom script ..." then done then stuck.  No X no nothing.  

Of other ideas I've tried lately the newest one is appending "init=/bin/bash" to the kernel line in grub to get control.  That's partially worked, it gave me a "root@(none)/#" prompt which I couldn't type at.  (more [here]("http://ubuntuforums.org/showthread.php?p=1980170"))

---

### Post by devnulljp on 2007-04-13
Take off and nuke it from space...it's the only way to be sure.
Sounds like your drive is hosed to me. Boot from the cd (can't you manually eject the cd with a paperclip?) back up your home partition. Then try to fsck the drive. 
A clean install will likely take less time than trying to figure out what's causing the error.

---

### Post by jhineman on 2007-04-17
Awesomest.computer.ever!  I must have a curse or something I can't even get the bloody liveCD ubuntu 6.10-amd64-LiveCD to boot.  To think that this computer was running pretty well only a week ago.

Is there any specific problems that anyone knows to do with ubuntu 6.10 and amd64 and or ASUS K8N-DL motherboards?

---

### Post by nudnik on 2007-04-17
> **jhineman said:**
> Awesomest.computer.ever!  I must have a curse or something I can't even get the bloody liveCD ubuntu 6.10-amd64-LiveCD to boot.  To think that this computer was running pretty well only a week ago.

Is there any specific problems that anyone knows to do with ubuntu 6.10 and amd64 and or ASUS K8N-DL motherboards?

Update the BIOS to version 1007 (or newer). That might do the trick. There have many issues with this board and Linux.

---

### Post by jhineman on 2007-04-17
Running 1007.  Will try the latest at 1010.  One of these days I will research then buy vs. my usual buy then research.

---

