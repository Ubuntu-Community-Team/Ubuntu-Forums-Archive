---
title: "update removed XP boot option."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Dave Freeman on 2007-09-03
Just an FYI.  

I run a dual boot machine with Windows XP and Ubuntu.  XP lives on hd0 and Ubuntu on hd1

Yesterday, 9/03/07, I noticed that two updates were available for Ubuntu 7.04.  I installed the updates and rebooted only to find that the XP boot option was removed from Grub.  

I was able to add the XP line to the grub menu file and everything is back to normal.  

I'm not sure if this is a bug in one of the updates but you may want to back up your grub menu file before updating.  

Has anyone else had this problem?

---

### Post by Malta paul on 2007-09-03
Yes the last update also updated grub, this is normal when a reboot is required.
The update may change your original grub settings. Mine made changes which I then changed back to may original setup. 
Yes its a good idea to make a backup for reference. 
Have fun:)

---

### Post by ggaaron on 2007-09-03
I think that this is the "feature" of ubuntu, and it proves it "easiness" - long story short, ubuntu will do everything for you, this means that config files are updated automatically and ubuntu won't ask you if you like it or not. Maybe there is a way to disable this, I don't know it. I've installed ubuntu, changed hard drives and updated grub.conf, now every time I install a new kernel my grub.conf is replaced by the one that was written during installation - this with wrong device names=/

---

### Post by louieb on 2007-09-03
There was kernel update recently. Depending on where your XP entry was/is located it is subject to getting wiped out or really messed up. Look for these lines:

```
#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
    **xp entry safe here**
### BEGIN AUTOMAGIC KERNELS LIST
   **xp entry here is going to get wiped after a kernel update**
### END DEBIAN AUTOMAGIC KERNELS LIST
**xp entry safe here too**

```

---

