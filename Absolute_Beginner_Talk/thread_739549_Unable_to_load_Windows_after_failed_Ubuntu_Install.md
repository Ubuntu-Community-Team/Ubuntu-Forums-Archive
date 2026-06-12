---
title: "Unable to load Windows after failed Ubuntu Installation"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by dapps2k on 2008-03-29
While partitioning my other drive, an error popped up during the partition and caused the installer to quit.  Then Linux locked up and I was forced to restart my computer.

However, now it won't load Windows up anymore.  I really hope the error didn't erase everything I had in my first drive, but is there any way for me to salvage Windows or stuff I have from my first drive?

---

### Post by LeoSolaris on 2008-03-29
try [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

or [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

If they can't it might not be do-able

---

### Post by Moop on 2008-03-29
If you weren't partitioning the windows hdd then everything should still be there. If you have a XP cd to boot from you can run fixmbr to restore your XP master boot record. You could also use a super grub cd to boot XP. 

If you can boot from a live cd you will be able to use the partition editor to look at your hdd's and partitions to see what's going on. It's also possible that you could just finish installing Ubuntu and it will go as planned and you will be able to boot XP or Ubuntu. Really can't say without seeing how your partitions are set up.

---

### Post by Phoenixzeus on 2008-03-29
Your best shot is to boot into your Windows XP Cd, and press R at the first screen, at the MSDOS based prompt. You should type:
Fixmbr (and follow the prompts)
if that doesnt work try:
fixboot (again follow the prompts)
and if that still doesn't fix it you might (but shouldn't have to) try a bootcfg.
Hope one of these get you up and running.
Failing all of this you could try an inplace upgrade, which is installing windows back over the top of itself and keeping all your data and programs.

---

### Post by LeoSolaris on 2008-03-30
> **Phoenixzeus said:**
> .
Failing all of this you could try an inplace upgrade, which is installing windows back over the top of itself and keeping all your data and programs.

I have used Windows since DOS and thats a new one to me...   wow   ya do learn new things every day. I will have to look that up.

Thanks,
Leo

---

### Post by InlawBiker on 2008-03-30
> **LeoSolaris said:**
> I have used Windows since DOS and thats a new one to me...   wow   ya do learn new things every day. I will have to look that up.

Thanks,
Leo

Every time I've done an in-place upgrade - re-installing the OS on an active install - it has ended in disaster.  It's like you end up with a brain-damaged OS.  It's much cleaner just to salvage your data and re-install everything fresh.

---

