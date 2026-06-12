---
title: "Need help to reinstall"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-19
I tried to fix a wifi problem and ended up destroying my ubuntu partition.  All I get is the command line and a message that ubuntu doesn't come with warranties. :(   Look here for details:
[http://ubuntuforums.org/showthread.php?p=4549428#post4549428](http://ubuntuforums.org/showthread.php?p=4549428#post4549428) 

Anyway, I posted earlier about a similar thing but am still unsure as to how to use the live CD to reinstall ubuntu on my linux partition without messing up my windows partition.  The installation in the live CD has no reinstall option.  Can someone please tell me what to select?  When I click manual, I am still unsure as what to do.  Please help.  I want to restore ubuntu, and then try to fix my wifi problem without doing this again.

---

### Post by Suparious on 2008-03-19
you could always reinstall. You will have to partition manually (basically just assign mount points for each partition and choose "do not format') and choose 'No' when the installer asks you to install GRUB to the "MBR".

if you can sudo on the commandline, you most likely wouldn't need to reinstall.

---

### Post by hikujk123 on 2008-03-19
> **Suparious said:**
>  if you can sudo on the commandline, you most likely wouldn't need to reinstall.  I can sudo on the command line, but wouldn't know what I was doing.  I think it may just be easier to reinstall.

---

### Post by kryth on 2008-03-19
You can always use the LiveCD
Then use Gparted on the LiveCD
to delete your old ext3 and swap partitions
then re-install like normal using the guided partitioner

---

### Post by hikujk123 on 2008-03-19
> **kryth said:**
> You can always use the LiveCD
Then use Gparted on the LiveCD
to delete your old ext3 and swap partitions
then re-install like normal using the guided partitioner

If I did what you said, would I also reinstall grub?

---

### Post by kryth on 2008-03-19
I believe so.
But I'm not sure what your really looking into doing.
If all you want to do it install grub you can do that from LiveCD or
google SuperGrub. I'd have to look up the commands to do it from the liveCD

---

### Post by kryth on 2008-03-19
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
can fix grub problems
if that's your real problem

I'm guessing 'startx' doesn't start xwindows .....the gui.

---

### Post by mikewhatever on 2008-03-19
Deleting root is completely unnecessary, because it gets formatted during the installation anyway. All you need to do is correctly specify the right partitions as root and swap by assigning to the the corresponding mount points, / and swap. Grub would be reinstalled in the process too and should pick up the Windows installation.

---

### Post by handydan918 on 2008-03-19
Ya know, it sorta sounds like you have a console login thing going on there. If you get a black screen with white text and a login prompt, just login and try ```
sudo dpkg-reconfigure xserver-xorg
```

Faster than reinstalling...

---

### Post by hikujk123 on 2008-03-20
I tried handy dan's command, but it wanted me to reconfigure everything manually.  For someone new to linux and taking into account ubuntu easy-to-use guided install, it was much easier to reinstall.  Let's get back to the wireless issue if it doesn't for some unknown reason work out of the box this time (ubuntu is installing right now).

---

### Post by hikujk123 on 2008-03-20
This was said by mcduck in another post:
"'gksudo' does the same thing 'sudo' does, but is made for use with graphical programs. (you should _never_use 'sudo with GUI apps, while it works for some cases in others it might mess the ownerships of setting files in your hoem directory, making you unable to log in any more)."

Is that what happened?

---

### Post by hikujk123 on 2008-03-20
bump

---

