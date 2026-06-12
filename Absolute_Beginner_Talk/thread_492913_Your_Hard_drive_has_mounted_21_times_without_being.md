---
title: "Your Hard drive has mounted 21 times without being checked. What's that about?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by jamesey on 2007-07-05
I've booted Ubuntu a lot of times with no issues. Today, when the status bar (right before the login screen) was scrolling, it stalled at about 33%. After waiting about 3 minutes, I hit reset on my box and feared the worst.

On the next boot,  I was at the startup status bar, when I was switched to a text interface. The text interface said, "your hard drive (sda1) has mounted 21 times without being checked." Then it was checked, as a a status indicator counted from 1% to 100%. I went and took a 10 minute shower in the interim, and came back at 98%. It hit 100% and everything booted normally. 

What's that about?

---

### Post by megamania on 2007-07-05
> **jamesey said:**
> 
What's that about?
it's an automatic check of your file-sytem which verifies the integrity of the file structure.

There are ways to change the frequency of such action - just search the forums if you want to get into that.

---

### Post by rodo-&gt;dave on 2007-07-05
tune2fs will allow you to change the fsck check options

[http://ubuntuforums.org/showthread.php?t=464364&highlight=tune2fs](http://ubuntuforums.org/showthread.php?t=464364&highlight=tune2fs)

---

### Post by NewJack on 2007-07-05
I'm not sure myself, but I found that after I have logged in as Root alot (like doing numerous separate installs in Synaptic or changing a bunch of system settings) this seems to happen.  Although it never took 10 minutes for me.  That might be due to your computers specs.  I don't think it is anything to worry about, more a check and balance system.

---

### Post by Cypher on 2007-07-05
The filesystem isn't thoroughly checked every time it is mounted. If you're using EXT3, just the journal is checked and if things check out, the mount and usage continues. However, during the initial filesystem creation time, a "mount count" was set to basically force a thorough check after that many mounts were encountered.

In most cases, that number is usually in the 20-40 range and is a good thing to happen. Do not stretch this out much longer than what is already there for your own good. On larger parittions the check can take a little time, but it's better to spend the time doing the check as opposed to losing data.

Turning the PC off without properly shutting-down will also trigger a quick (but not fully thorough) check on the filesystems to ensure that nothing broke..

---

### Post by Kosimo on 2007-07-05
The nice thing about this is when Ubuntu is installed for the first time, 
updated and then restarted.....  The message is something like..

Your hard drive has mounted 238917831723 times without been checked.. Check forced ;)

What a long time!!  lol


Did somebody else had this problem?  It always happens to me

---

### Post by Cypher on 2007-07-05
The only time you will get that sort of a ludacrious number is if during the EXT3 filesystem creation, the date on the system is wrong. In MOST cases, the default date will go to Jan 1, 1970 and that's what will be stored on the filesystem. Then when you reboot, the date might get properly set through the RTC or NTP or something and you suddenly jump to 2007 and that results in that wonky number..

If, during installation, Ubuntu figures out the right date/time then you will not have this issue..

---

### Post by rodo-&gt;dave on 2007-07-05
> **Kosimo said:**
> ...

Your hard drive has mounted 238917831723 times without been checked.. Check forced ;)

What a long time!!  lol


LOL! Yea, you probably don't want to set the number of boots quite that hi :D

---

### Post by Raineer on 2007-07-05
> Today, when the status bar (right before the login screen) was scrolling, it stalled at about 33%. After waiting about 3 minutes, I hit reset on my box and feared the worst.

Just so you know, the file check was what it was doing the first time when you pressed the reset button.  Just something to keep in the back of your mind if a boot seems to hang for no reason on a normally working machine.  I imagine your threshold is set for every 20 boots.

---

