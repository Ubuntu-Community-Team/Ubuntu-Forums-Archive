---
title: "Unmount Problem"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-03-27
When I boot Linux, (6.10) all my windows drives are already mounted and show up on my desktop. I have tried sudo /etc/fstab to follow steps to unmount them, but everytine I time I try, I get command not found.
 WHat am I doing wrong? I am also trying to figure out how to get my comuter to NOT run fsck at boot. Can't figure out how to turn that off either.

---

### Post by Bias on 2007-03-27
gksudo gedit /etc/fstab

Here you will find a list of drives, you can remove the ones you don't want to see (be sure to get the right ones) Once this is saved and you reboot the drives shoul not be visible.

If you are unsure which ones to remove post the file contents here.

Nick.

---

### Post by maccawolf on 2007-03-27
I believe that was one of hte commands I tried yesterday, but I will try it again when I get home, and let you know the results.
 TX!

---

### Post by dstew on 2007-03-27
You need to edit the etc/fstab file, not run it as a command, so try the command suggested by Bias. Other text editors beside gedit can be used, such as nano and vi. And, of course you are aware that to unmount a drive, the command is **umount**, not unmount -- in case you were trying to unmount from the command line.

---

### Post by Patrick K on 2007-03-27
Do you want to unmount them or just get them off your desktop?

If you want to remove the icons from your desktop but keep the "drives" mounted, in Synaptic search for then download/install "gconf-editor" (it might already be on your system, I don't recall if it comes with Ubuntu). Once you have it, run it and go to "apps/nautilus/desktop" and uncheck "volumes_visible". This will hide the desktop icons. 

If you don't want the "drives" mounted at all, you can edit fstab (in a terminal type "gksudo gedit /ect/fstab"). Put a hash (#) mark in front of the "drives" you do not want mounted. This will keep them from mounting. Remove the hash if you want to mount them. 

As in all cases with Linux, all this can be done in a terminal. I don't know the commands so I use this method. Less chance of a typo, too.

---

### Post by maccawolf on 2007-03-27
Cool, thanks peoples. (M&F). I have lots of stuff to try when I get home....

---

### Post by maccawolf on 2007-03-27
to Patrick K,
 BOTH. I'd like to get them off my desktop AND unmount them, as long as I know how/where to mount them again when I need them.

Now that I've managed (in a round about way) to convert a Jpg for my desktop image, I don't NEED winblows stuff at this second. In the future, I'm sure I will, but right now, it's more of an annoyance than a help.

---

### Post by Patrick K on 2007-03-27
Once they are unmounted, they will disappear from the desktop.

---

### Post by maccawolf on 2007-03-27
OK, now I'm even MORE perplexed, as they ALL already have hash marks in front of them...

---

