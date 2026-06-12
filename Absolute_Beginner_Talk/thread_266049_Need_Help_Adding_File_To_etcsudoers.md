---
title: "Need Help Adding File To /etc/sudoers"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by OffHand on 2006-09-26
Short story:
I need this file excluded from asking a password: /usr/sbin/hddtemp

I tried editting the sudoers file like this:

admin ALL=NOPASSWD: /usr/sbin/hddtemp

But that doesn't seem to work.

Long story I have a small bash script that looks like this:
```
#!/bin/bash
/usr/sbin/hddtemp /dev/sda | cut -c 27-31
```

so I can use HD temperature within conky.

---

### Post by mitch.c on 2006-09-26
> **OffHand said:**
> Short story:
I need this file excluded from asking a password: /usr/sbin/hddtemp

I tried editting the sudoers file like this:

admin ALL=NOPASSWD: /usr/sbin/hddtemp

But that doesn't seem to work.

Long story I have a small bash script that looks like this:
```
#!/bin/bash
/usr/sbin/hddtemp /dev/sda | cut -c 27-31
```

so I can use HD temperature within conky.

Based on the sudoers entry, I think your script needs to be:
```
#!/bin/bash
sudo /usr/sbin/hddtemp /dev/sda | cut -c 27-31
```

But in reality, I think you would be better off to do this:
```
sudo chmod 4755 /usr/sbin/hddtemp
```
and forget sudoers.

---

### Post by OffHand on 2006-09-27
Thnx Mitch.c, that did the trick  :)

---

