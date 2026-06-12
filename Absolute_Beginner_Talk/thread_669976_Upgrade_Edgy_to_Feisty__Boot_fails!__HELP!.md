---
title: "Upgrade Edgy to Feisty:  Boot fails!  HELP!"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by mamdali on 2008-01-16
I just upgraded Edgy to Feisty (using apt not distro CD).

After re-booting I am getting:

Busybox v1.1.3 (Debian.....) Built in shell ash
enter help for list ...etc etc
/bin/sh: can't access tty; job control turned off
(initramfs)

I've looked all over seen similar problems but NOWHERE a nowhere a nice clean answer I can undertsnad as a newbie.

THANKS!

---

### Post by PapaNerd on 2008-01-17
You didn't list your hardware platform, but this is a known problem with a Mac PPC.  The workaround can be found at [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues).  You basically need to exit the BusyBox utility, let it boot, then do a one line mod to a file to prevent the problem on subsequent boots.

---

### Post by mamdali on 2008-01-17
Apologies.  this is a DElll 386 machine with WIndoes ME.

BTW, I had Breezy installed.  Went to Edgy and Dapper successfully.  All worked well.  upgrade to Feisty results in what I described.

(BTW, this is dual boot with Windows ME.  GRUB shows all the updated boots (Breezy, Dapper, Edgy, etc).  But they don't work at all or correctly anylonger either.)

Does the fix you indicated still apply?

Thanks!

---

### Post by PapaNerd on 2008-01-18
I don't know if the advice applies to that machine configuration as well, but the symptoms are nearly identical.  It shouldn't hurt to try since the file update you make could be backed out if it didn't work.

---

### Post by mamdali on 2008-01-18
i don't understand.  The instructions clearly state to add 'powerpc' somewhere (mine is a Dell 386 based machine). 

Plus what is 'yaboot'?

I really need basic instructions in 'English'

Thanks!

---

### Post by mamdali on 2008-01-18
plus modprobe ide-core returns "module not found"

---

