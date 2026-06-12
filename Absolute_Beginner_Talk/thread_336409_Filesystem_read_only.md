---
title: "Filesystem read only?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by pan69 on 2007-01-11
Hi,

I found this page ([http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)) that explains how to make a couple of improvements to speed up your Ubuntu system. I think, I want that so I followed the steps presented on this page. Now, of course, my system will not boot any more. ](*,) 

If I now boot up in recovery mode to undo the changes I made I cannot write the files to disk anymore. I get a message saying that my "Filesystem is read-only".

Does anyone has an idea of how I can get into my system again to change back the files I changed?

Thanks!

---

### Post by ajgreeny on 2007-01-11
In what way will it now not boot and where does it stop?

To go back to where you were you will need root access, which is probably best obtained using a live CD rather than recovery mode, though I'm sure it will be possible to get root access in that too.

Once you are root, undo the changes you made, or rename the files you made and reinstate the backups (you did make sure you had backups, I hope) and with luck you'll be back where you were before.

---

### Post by pan69 on 2007-01-11
In recovery-mode the system allows me to sudo and edit the files. Only when I write the modified file back to disk it comes up with a message saying the Filesystem is read-only.

I did make backups of my config files etc. but I can't write to disk so I can't put the backup files back.

>> In what way will it now not boot and where does it stop?

At the moment I'm not near my machine but I believe it comes up with a message saying something about x.org failing to start. :-k

---

### Post by pan69 on 2007-01-12
This is the message the systems comes up with:

"Could not start the X server (your graphical environment) due to some internal error."

I guess this is because some process wants to write to disk but can't (X server in this case).

---

### Post by pan69 on 2007-01-12
I fixed the problem. I booted from a Ubuntu Live CD then I mounted my harddrive, gave a "*sudo passwd root*" and edited my "*/etc/fstab*" to undo my changes. Pfffff. I guess I was lucky this time. Next time I will try these so called optimizations out inside a VMWare instance first.

Thanks for your help!

---

### Post by Psquared on 2007-01-16
> **pan69 said:**
> I fixed the problem. I booted from a Ubuntu Live CD then I mounted my harddrive, gave a "*sudo passwd root*" and edited my "*/etc/fstab*" to undo my changes. Pfffff. I guess I was lucky this time. Next time I will try these so called optimizations out inside a VMWare instance first.

Thanks for your help!

How did you do that? I need to make a change in my inittab file and need to mount hda1 (which I have done) from a Live CD. I can access the file, but because I am not root I can't save the change (to runlevel 4 - long story) and thus boot back into my regular system. So, how do you gain root access to a mounted partition using a live CD?

---

