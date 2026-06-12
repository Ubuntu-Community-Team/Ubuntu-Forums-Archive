---
title: "SWAT &amp; root"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by dsewell on 2007-07-26
Hi,

I am lost (again).

I have installed SWAT, but I can't log-on as root as per the instructions as I don't have root enabled.  (I understand that this is the norm for Ubuntu?)

So, although SWAT seems to be working, all I can do is log-on with my use account which is pretty useless as I can't see or change any of the Samba config data.

Does anybody know how I get the full functionality of SWAT without enabling root?

Seems that this thread is for the same issue:  [http://ubuntuforums.org/showthread.php?t=351592](http://ubuntuforums.org/showthread.php?t=351592)

Or, do I need to enable root?  (If so, how?)

Cheers again.

---

### Post by Steve1961 on 2007-07-26
Just type:

sudo passwd root

and then logon as root into SWAT with the password you were asked to input after the command

---

### Post by p_quarles on 2007-07-26
There's no need to set a password for root, and doing so just gives you another thing to remember. To get into a root shell, type:
```
sudo bash
```

---

### Post by dsewell on 2007-07-27
Thank you guys.

---

### Post by drspastic on 2007-09-07
There is another way, 

open a root terminal and type

$ firefox [http://localhost:901](http://localhost:901) $

---

