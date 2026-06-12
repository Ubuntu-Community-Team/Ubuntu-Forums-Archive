---
title: "How can I add WinXP Safe Mode to GRUB?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by celldrifter on 2007-04-01
Last night I freaked out my XP bad and can't even log in. I tried to get Ubuntu to recognize the drive by installing ntfs-config, but Windows XP didn't close properly so it won't recognize it. And I'm sucha newb I don't know how to add Windows XP to the GRUB loader. ANy ideas? Thanks in advance! (I believe XP has a problem with a software I installed last night, so i just wish to uninstall it)

---

### Post by mac.ryan on 2007-04-01
I don't know if adding a safe mode entry for windows in grub is possible at all, anyhow the "safe mode" option can be manually inserted in the boot.ini of windows (See [here]("http://www.governmentsecurity.org/archive/t9640.html") if it helps) but... can you access in any way that partition? I understood this might not be the case.

Another option I can think of is to use one of the liveCD of some GNU/Linux distro specifically designed to recover systems such for example:
[http://www.sysresccd.org/](http://www.sysresccd.org/)
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

If you are really stuck and believe is the dual boot that prevents you to get in the safe mode, you might wish to use ubuntu to restore the MBR (doing the equivalent of fixmbr.exe) so that it will not load grub anymore but windows directly. Fix your problem, reinstalling grub (see community documentation for how-to on how to reinstall grub from the live CD).

Best luck!! :)

---

### Post by nixclusive on 2007-04-01
Hello there, press F8 immediatly after you select Windows from the GRUB menu. You should get another menu. Gee.. this looks like some game cheat ;-)

---

### Post by mac.ryan on 2007-04-01
[quote=celldrifter]And I'm sucha newb...[/quote]

-->

[quote=nixclusive]Hello there, press F8 immediatly...[/quote]

THAT MUCH noob?! :-o

...not a sin, of course! I just felt silly to have posted what above! ;)

---

### Post by celldrifter on 2007-04-02
Thanks for the help guys.
BTW, holding down SHIFT or pressing F8 didn't work. That's why I came here. I guess I should have stated that in the first post. Anyways, I got a workaround to work eventually. Thanks for the help.

---

