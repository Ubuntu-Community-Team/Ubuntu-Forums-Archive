---
title: "gotta trouble with locale/compiz , after upgrade to gusty"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by iblicf on 2007-07-22
i have upgrade to gusty by change the sources.lst file, and do apt-get update/distupgrade,, then ... gotta some trouble with LOCALE and my Compiz fussion ,
first ....,, my manpage(english) seems been unreadble messages ( mess abslutly ),,,i have trying to "export LC_ALL=C", and it works,,but the chinese folder mess again ... :)
> weiyh@MyPC:~$ man man 2>man
weiyh@MyPC:~$ cat man
/usr/share/man/zh_CN/man1/man.1:24: warning: can't find special character `u2542'
/usr/share/man/zh_CN/man1/man.1:30: warning: can't find special character `u2540'
/usr/share/man/zh_CN/man1/man.1:42: warning: can't find special character `u0446'
/usr/share/man/zh_CN/man1/man.1:56: warning: can't find special character `u2103'
/usr/share/man/zh_CN/man1/man.1:60: warning: can't find special character `u2516'
/usr/share/man/zh_CN/man1/man.1:148: warning: can't find special character `u2033'
/usr/share/man/zh_CN/man1/man.1:171: warning: can't find special character `u2032'
/usr/share/man/zh_CN/man1/man.1:171: warning: can't find special character `u2545'
/usr/share/man/zh_CN/man1/man.1:179: warning: can't find special character `u0101'
/usr/share/man/zh_CN/man1/man.1:238: warning: can't find special character `u0412'   
...
weiyh@MyPC:~$ locale
LANG=zh_CN.UTF-8
LANGUAGE=zh_CN.UTF-8
LC_CTYPE="zh_CN.UTF-8"
LC_NUMERIC="zh_CN.UTF-8"
LC_TIME="zh_CN.UTF-8"
LC_COLLATE="zh_CN.UTF-8"
LC_MONETARY="zh_CN.UTF-8"
LC_MESSAGES="zh_CN.UTF-8"
LC_PAPER="zh_CN.UTF-8"
LC_NAME="zh_CN.UTF-8"
LC_ADDRESS="zh_CN.UTF-8"
LC_TELEPHONE="zh_CN.UTF-8"
LC_MEASUREMENT="zh_CN.UTF-8"
LC_IDENTIFICATION="zh_CN.UTF-8"
LC_ALL="zh_CN.UTF-8"


and compiz doesn't work anymore! 
> weiyh@MyPC:~$ compiz --replace
Checking for Xgl: not present.
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Converting gconf plugin list: ''
Checking for nVidia: present.
Checking for Xgl: not present.

***MEMORY-WARNING***: gtk-window-decorator[10013]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

plz help ! im from china( mainland by the way ,sorry for the poor english )

---

### Post by starcraft.man on 2007-07-22
Can I ask why you upgraded to an alpha software? I know people have said it's mostly stable (least from what I seen/heard) but that doesn't mean everyone will have it so good. 

I can't help on the locale problem, perhaps something got corrupted/messed up on the upgrade?

As for Compiz, reinstall your graphics driver over the existing one, then reinstall compiz fusion. I imagine it should work after that, when you change kernels substantially (you went to 2.6.22, I believe that's the gutsy one) you have to reinstall drivers that don't come with the new kernel.

If the problem persists and no one else has superior help (and this fails) I'd simply downgrade to Feisty and in future it's best not to upgrade your main OS to a testing software.

---

### Post by iblicf on 2007-07-23
thx for reply ...:) ,,why upgrate....? eh.. maybe "have a taste of what is just in season".
i have reinstalled the nvidia-glx and remove/reinstall the compiz completly ,,it' still don't work.....i'll report the bug.

but the man page ...it's rather oddness...even alpha edition,, can't imagination

---

### Post by crimesaucer on 2007-07-23
Have you searched through the Gusty development thread for similar problems: [http://ubuntuforums.org/forumdisplay.php?f=238](http://ubuntuforums.org/forumdisplay.php?f=238)

---

### Post by iblicf on 2007-07-23
hah... i have fixed the problem , just now... since i remembered that ..i have installed the Cman(chinese manpage edition  ) ever ,,:) ,,i  try to mv the cman folder( /usr/share/man/zh_CN ) to another place ,  OK!!! ,,,both man and cman 

thanks crimesaucer...i'll concern that thread....
thanks starcraft ,,,i love the game also,,,,and WOW,and TFT
good luck !

---

### Post by Benbow on 2007-07-23
What do you thin of Gutsy so far?

---

### Post by FleetAdmiral74 on 2007-07-23
> **Benbow said:**
> What do you thin of Gutsy so far?

lol it messed up is comp, probably does not think super highly of it :)

---

