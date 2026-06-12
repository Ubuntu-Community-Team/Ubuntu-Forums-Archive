---
title: "Very simple question.."
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Crymsyn on 2006-12-05
Hello all. I am very new to Linux, and I started off using FC5. I decided to switch over to Ubuntu.. what I cannot figure out, is how to configure my boot loader to start up at a command prompt, i.e. without the GUI, while maintaining network capabilities.

I heard a couple different attempts to solve my problem, none of which worked.. first was to edit /etc/inittab, which is not there. Second was to go into GRUB editor on boot, and add the init=3 argument to the kernal line.. didn't work.

I've searched for this, and have not been able to find anything, other than how to remove gdm from the system (which I do not want to do..). Anyone have any suggestions?

---

### Post by rabid emu on 2006-12-05
I've wanted to know how to do that as well.  All the research I did indicated, however, that Ubuntu made runlevel 3 (multi-user non-graphical mode, the one you want) point to runlevel 5 (graphical).  The only default way to boot up non-graphically is runlevel 2, which is single-user non-graphical i.e. root only, i.e. recovery mode in the grub menu.  I'm sure it's possible to reconstruct runlevel 3, but I have no idea how and it's probably complicated.

---

### Post by Crymsyn on 2006-12-05
So, I cannot boot to command prompt, without shutting down network support (since runlevel 2 is single user mode, instead of multi..) ?

---

### Post by mahy on 2006-12-05
just put number "3" (without the quotes) at the end of the proper line in menu.lst. That worked for me.

---

### Post by bodhi.zazen on 2006-12-05
I suggest you disable start scripts rather then deleting them.

Since Linux is case sensitive this is easy:

To disable:
```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
```

To Enable:```
sudo mv /etc/rc2.d/s13gdm /etc/rc2.d/S13gdm
```

This way I do not need to remember

    * What start scripts I disabled
    * Start order of said scripts
    * Where was that link to ?.

After booting to cli:

    * To start gdm: sudo gdm
    * You know startx

---

### Post by steve.horsley on 2006-12-05
Ubuntu boots into runlevel 2 by default. All runlevels (2, 3, 4, 5) are configured to start gdm (the GUI). 

I suggest you use this command: 
**sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm**
This changes the symlink name from upper to lower case 'S', and thus stops it from being run as boot time. Rename it back to upper case S to re-enable gdm.

Bodhi has beaten me to it again!

---

### Post by bodhi.zazen on 2006-12-05
> **steve.horsley said:**
> Bodhi has beaten me to it again!

I hate it when that happens :p

---

