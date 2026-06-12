---
title: "[SOLVED] user name lost"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by MIPIO on 2008-02-23
installed ubuntu in new computer. cannot get back in because of username not recorded

---

### Post by taurus on 2008-02-23
Boot into recovery mode from GRUB menu and look it up with this command.

```
ls -la /home
```
And if you don't remember your password, then you can change it as

```
passwd john
```
_assuming_ john is your login name.

---

### Post by MIPIO on 2008-03-04
from the GRUB:  prompt I entered  “ ls - la / home “ as I was instructed 
What I got back was “ Error 27: Unrecognized command
                                          grub> E

---

### Post by JoshuaRL on 2008-03-04
No, you need to boot into the Ubuntu Recovery Mode from the Grub menu.  Then you can do that command.

---

### Post by Joeb454 on 2008-03-04
No he means when you see the GRUB menu appear (where there are 2 or 3 versions of Ubuntu listed) you need to choose the one that says recovery mode :)

---

### Post by aysiu on 2008-03-04
This is recovery mode (highlighted in green)

---

### Post by MIPIO on 2008-03-04
when you say choose, is that the edit (e) mode ?
If I choose the edie (e) 
I get 3 more selections   root, kernal and initrd 
do I edit (e)one of these ? withe the command:  ls - la /home ?

---

### Post by JoshuaRL on 2008-03-04
> **aysiu said:**
> This is recovery mode (highlighted in green)

Good one aysiu, that's really great.  How did you get that?

> **MIPIO said:**
> when you say choose, is that the edit (e) mode ?
If I choose the edie (e) 
I get 3 more selections   root, kernal and initrd 
do I edit (e)one of these ? withe the command:  ls - la /home ?

MIPIO, you want to press up or down arrow keys until they highlight that Recovery Mode.  Then press enter.  A lot of stuff will load and will finally drop you into the CLI as root.  Something like:
```

root@yourcomputer:~$

```

Then you try those commands.

---

### Post by aysiu on 2008-03-04
> **JoshuaRL said:**
> Good one aysiu, that's really great.  How did you get that? VirtualBox

---

### Post by kool_kat_os on 2008-03-04
> **aysiu said:**
> VirtualBox

im getting that for sure:)

---

### Post by JoshuaRL on 2008-03-04
> **aysiu said:**
> VirtualBox

I thought so, but I wasn't sure.  Thanks.

---

### Post by MIPIO on 2008-03-04
> **JoshuaRL said:**
> Good one aysiu, that's really great.  How did you get that?



MIPIO, you want to press up or down arrow keys until they highlight that Recovery Mode.  Then press enter.  A lot of stuff will load and will finally drop you into the CLI as root.  Something like:
```

root@yourcomputer:~$

```

Then you try those commands.


Thanks Thanks Thanks  I got it now!

---

