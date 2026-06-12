---
title: "Another Updater problem"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by DennisOS2 on 2008-02-03
So ............... how DO you spell newbie in Ubuntu :) ???

Played with Susie a couple of years ago.  Not a good experience.  Already Ubuntu has shown to be a better version for my exact same machine .......... Hats off to the team.

I went with KUBUNTU as I'm partial to KDE.  All installed well.  Have on a Dell XPS along with XP, Vista, MacOS.  Chain loading using the Vista loader to GRUB.  All working very well.  UBUNTU starts with NO error messages.

Immediately after installation I attempted an update through Adept.  All but one file (don't remember which) DL'd fine.  Adept when installing said it couldn't commit because either files were missing or the updates might break other components.  Now every time I start Adept I get this message:

[I][B]Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.[/B][/I]

So, of course, I haven't been able to really upgrade, or even enable the ATI drivers because I get the same message.

Again, the rest of the system appears to run correctly.

---

### Post by wicshadow on 2008-02-03
Try running
sudo dpkg --configure -a

that should help...

---

### Post by Majorix on 2008-02-03
[php]killall adept #try "sudo killall adept" if you get a warning about authentication[/php]

---

