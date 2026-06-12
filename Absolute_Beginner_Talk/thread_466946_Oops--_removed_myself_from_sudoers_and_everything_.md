---
title: "Oops-- removed myself from sudoers and everything else!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by lazyart on 2007-06-07
Just installed VirtualBox AMD64 (yay!).  Went to check that I was in the vboxusers group through the gui but the window would just hang with no info.  I tried to launch virtual box from the menu and it wouldn't launch, so I figured I had to manually add myself.

I had already done```
groups lazyart
``` and it didn't show me as a vboxuser.

I looked up commands and figured```
sudo usermod -Gvboxusers lazyart
``` would do the trick.  So I typed it in.  That was a mistake-- it removed me from all the groups except my own and vboxusers.  Now I can't use sudo to fix it!

I did manage to save the list of groups and will use recovery to fix it when I get home (accessing remotely at the moment).  Does anyone know what command I should have used?

Thanks.

---

### Post by taurus on 2007-06-07
If you did save a backup of /etc/group, just copy it back with (from recovery mode from GRUB menu)

```
cp /etc/group.backup /etc/group
```

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by lazyart on 2007-06-07
oops. didn't do that.  when I typed *groups lazyart* it spit out a list and I saved it... although it didnt have sudoers in it (does have adm and admin so maybe they will help out).

I see it's a matter of putting my username back in each line.  Not fun but I think it's fixable.

Looking now at the link you provided that's exactly what I have to do.  Something broken is now something learned. :)  Thanks.

---

