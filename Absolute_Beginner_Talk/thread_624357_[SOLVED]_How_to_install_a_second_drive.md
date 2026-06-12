---
title: "[SOLVED] How to install a second drive"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-26
I just purchased a 320gig drive and want to "clone" my primary master, which is currently a 20 gig. What software is there for gutsy that will perform this, I guess, like Norton's Ghost?

What I'm asking is what is the easiest way to transfer the Gutsy and all my settings over to this new drive and then make it the primary master?

---

### Post by wlc3069 on 2007-11-26
here's a good way to back up your filesystem and then restore it later
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
Worked wonders for me when changing hard drives

---

### Post by Mark_in_Hollywood on 2007-11-26
I can't even begin to understand that.

You use:

tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

to do what? This, I'm guessing, compresses the entire hard drive and excludes 7 folders or directories.

Once this is done, what? If I ran 

tar xvpfz backup.tgz -C /

that would restore what had been compressed.

Can someone give me a How-To?

---

### Post by wlc3069 on 2007-11-26
here is a how-to guide on it [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) sorry i didn't include it before, its quite late

---

### Post by Mark_in_Hollywood on 2007-11-27
How did you deal with the master/slave business?

---

### Post by wlc3069 on 2007-11-27
I didn't need to. What i did was back up my system to my home server (an external hdd would work), then i put the new drive in my computer installed ubuntu again then restored the data from my server and everything was up and running like before but on my new hdd. If an external drive is out of the picture for you, then im afraid im of no further help, sorry

---

### Post by Mark_in_Hollywood on 2007-11-28
I'm marking this thread as "solved"

Thanks to the community.

---

