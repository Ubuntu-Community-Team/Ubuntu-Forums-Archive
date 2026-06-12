---
title: "stuck in grub--ubuntu no start"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-01-07
I have been looking for an answer for a while but no luck so far.

ubuntu does not start after seeing the grub menu. It gives error at the start up, i CANNOT GET INTO THE login screen, I can see ubuntu/ubuntu safe mode start up:

init:rcS process ( 1988 ) terminate with status 2
init: rc2 ( 1994 ) process terminate with status 2.

Would you please show how I can recover? I run "safe mode" and get into su. But after that what do I do? Would you please inform step by step, or direct me to stg detailed link, I am new to linux.

Thanks in advance,
findik

---

### Post by Ramses de Norre on 2007-01-07
You can get in recovery mode?
Try:```
mv /etc/rc2.d/ /etc/rc2.d.old
cp -aR /etc/rc3.d/ /etc/rc2.d/
init 6
```

It's a guess but it might solve your problem.. If not you can always reverse the changes with ```
mv /etc/rc2.d.old/ /etc/rc2.d/
```

---

### Post by findik1 on 2007-01-07
thanks for the reply!
yes I can get in recovery mode:
root@(none) I typed your commands but it said it could not find that directory or file.
I checked there is /etc directory, but maybe not rc2/rc3 under it.

(when it was working previously my username was: matlabuser , root@(none) is a problem?

any suggestions?

---

### Post by houstonbofh on 2007-01-07
Looks like you lost some stuff.  Did you loose a hard drive, or partition?

---

### Post by findik1 on 2007-01-07
I looked with live cd gnome partition maganer, gparted that all partition is there. I guess I deleted some files only

---

