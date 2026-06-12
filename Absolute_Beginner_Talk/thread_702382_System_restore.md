---
title: "System restore"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-20
Is there System restore option in Ubuntu?

---

### Post by lswest on 2008-02-20
what exactly do you understand under "system restore"?  setting the system back to how it was at a certain date?  If so, i don't know of any programs that can do that, apart from making your own tar archive of the root filesystem and untarring them back into the proper paths.  If you mean a recovery console, the tty sessions are usually accessible on the normal boot (even if the Xserver fails) or otherwise can be reached through the failsafe mode (in the GRUB menu)  where you can undo anything you did that may have crashed your system.

---

### Post by philinux on 2008-02-20
> **adi_das said:**
> Is there System restore option in Ubuntu?

Not yet but there are simple things you can do. I've got my home folder on its own partition. Reinstalling the system is then very easy.

You can make a live cd of your current set up and burn to disk.

[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)
[http://www.linux-tutorial.info/modules.php?name=News&file=article&sid=5695](http://www.linux-tutorial.info/modules.php?name=News&file=article&sid=5695)

There is also grsync and sbackup in the repos.

---

### Post by oedha on 2008-02-20
> **adi_das said:**
> Is there System restore option in Ubuntu?
like windows ?
i am not really think so......since we still can do "something" if we crashed
and also there is recovery mode ( i dont know exactly what is this...:) )

---

