---
title: "Ubuntu 7.10 Removal"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by bryansworld on 2008-01-17
I have purchased a laptop for work and decided that I want it with both windows and Ubuntu. I have another computer running both ubuntu and windows. So how do i remove ubuntu 7.10???

---

### Post by Dynaflow on 2008-01-17
What version of Windows are you using?  Is it Vista?

---

### Post by bryansworld on 2008-01-17
nope,
Windows XP SP2

---

### Post by Dynaflow on 2008-01-17
Bizarrely enough, I know how to do it with Vista, but I don't remember off the top of my head how to do it with XP (the last time I had to do an uninstall with that OS was a couple of years ago, and it was with a distro that used LILO, not GRUB).

You'll have to do these things:

*Restore the Windows master boot record (which GRUB will have replaced on your laptop).

*Delete the Ubuntu and swap partitions on the hard drive.

*Re-expand the Windows partition.

Give me a minute to research how to do that specifically for XP (unless someone else wants to chime in).  In the meantime, was the laptop giving you problems or something like that?  They tend to be a bit harder to Ubuntuize than desktops, but they can end up performing remarkably well when done right.

---

### Post by thelatinist on 2008-01-17
If you boot into recovery console on your WinXP install CD, you can just run fixmbr to restore ntloader.

---

### Post by Dynaflow on 2008-01-17
Beat me by a minute.  Yes, if you have the recovery CD, that's what you'd do.  If you don't, [SuperGRUB]("http://supergrub.forjamari.linex.org/") is apparently capable of restoring your MBR as well.

Download and burn a copy of the GParted liveCD from [http://sourceforge.net/project/showfiles.php?group_id=115843]("http://sourceforge.net/project/showfiles.php?group_id=115843").  Boot from that, and it will give you the tools to delete your Ubuntu and swap partitions and re-expand your Windows one.

---

### Post by Attila2452 on 2008-01-19
that didn't work for me, i had XP, but then i put ubuntu on it, and it screwed up, so i put ubuntu on it again, and now, i have XP, an ubuntu version that dosen't work and another version of ubuntu, what do i do, i want tot get rid of the 2 ubuntu's and get a COMPLETLY NEW UBUNTU!!!!! PLEASE HELP!!!

---

### Post by Dynaflow on 2008-01-20
> **Attila2452 said:**
> that didn't work for me, i had XP, but then i put ubuntu on it, and it screwed up, so i put ubuntu on it again, and now, i have XP, an ubuntu version that dosen't work and another version of ubuntu, what do i do, i want tot get rid of the 2 ubuntu's and get a COMPLETLY NEW UBUNTU!!!!! PLEASE HELP!!!

XP works, right?  What partition is it on?  If everything else is fine with your system, you can just install Ubuntu from the CD, have the installer delete the current Ubuntu partitions (not the Windows one, though) and reinstall Ubunt over the reformatted, former Ubuntu partitions.

---

