---
title: "are the packages installed with apt-get stored somewhere??"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Delp on 2005-11-16
My problem is that i want to install the modem (eagle-usb modem) on a friend's computer, but i cannot install the packages offline. So, i thought about installing them on my computer, copy the packages and install them manually on his computer.

By the way, if somebody has a smoother method, i would be happy to know it.

So.. That's my question, i've sought for the answer, but i didn't find it.

Thanks a lot.

---

### Post by oskude on 2005-11-16
to find things
```
locate *.deb
```
or without updatedb
```
sudo find / -iname *.deb
```
i found them in
```
/var/cache/apt/archives/
```

---

### Post by darknuala on 2005-11-16
/var/cache/apt/archives/

That is where all of mine go to as well.

---

### Post by BIGtrouble77 on 2005-11-16
I noticed these files when I did my last backup.  What's the downside to deleting them?  Seems like an enormous waste of space...  I have over 2gb of them.

-BT

---

### Post by simplyw00x on 2005-11-16
> I noticed these files when I did my last backup. What's the downside to deleting them? Seems like an enormous waste of space... I have over 2gb of them.

-BT
If you ever have to reinstall them, it'll redownload them all instead of just getting the locally stored ones. You can safely delete all of those, but expect a long download if you reinstall anything large.

---

