---
title: "All of a sudden, no audio output"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-08-31
All of a sudden, no audio output.  XMMS complains "Couldn't open audio ... check that your sound card is properly configured" but I haven't changed anything before and as far as I can tell, the correct audio plugin (ALSA) is selected.  Totem hangs on start, presumably because of the same problem.
I have already rebooted, nothing.
The last thing I did prior to the problem was running an apt-get upgrade.  The latest kernel was installed, I can only suppose it has something to do with that.
I'm running Xubuntu 7.04.  Please help!

---

### Post by alienexplorers on 2007-09-01
Try booting from the previous kernel and see if sound works.  If it does then it has to be a problem with the new kernel update.

---

### Post by Koiti on 2007-09-01
And I guess you're not the only one: -> [http://ubuntuforums.org/showthread.php?t=540072&highlight=kernel+update+sound](http://ubuntuforums.org/showthread.php?t=540072&highlight=kernel+update+sound)

I had the same issues,and  also noticed a white border around my panels (using compiz-fusion). Both carried to the old kernel and had to restore the system from an old backup I had somewhere in here. Even booting in the old kernel via GRUB didn't worked for me.

Now I have some files from the new kernel laying around here, but have NO IDEA in how to delete them/prevent a new upgrade/erase it from GRUB.

Let's keep reading...

---

### Post by Blofeld on 2007-09-01
Dang!!!
But many thanks, Koiti and Alien. :popcorn:
Just before I installed the update I actually thought that it would be wiser not to give the updates a bit of time to let them mature ... how prophetic of me.

---

### Post by Blofeld on 2007-09-05
To anyone who is facing the same problem:  it is caused by some incompatibility between the ALSA driver and the latest kernel, version 2.6.20-16.
It can at least temporarily be amended by telling GRUB (the boot manager) to boot the older kernel, version 2.6.20-15, in the menu that comes up when you're booting.
It is also possible to revert to the older kernel but that is a dangerous "open heart" procedure which I'd advise anyone who isn't proficient in this to avoid.

---

