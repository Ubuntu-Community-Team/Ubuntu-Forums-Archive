---
title: "Live CD issues on iMac G5"
date: 2006-12-17
forum: Apple PPC Users
---

### Post by TravisG5 on 2006-12-17
This is my first attempt to use Linux, so I wanted to boot from the Live CD to see if I like Ubuntu enough to dual boot it.  

I started booting from the CD, and at the text menu I typed in "Live" like it said to.  Then I just got a grey screen with my iMac's fans going really high for a minute.  I restarted the computer and booted back into OS X at that point.  What did I do wrong?

Thanks..

---

### Post by maxamillion on 2006-12-17
You shouldn't need to type anything, it should give you a menu to select from and you might need to select the one speaking of "Safe Graphics Mode" because sometimes it fails to load modules correctly on the live cd, I assume it has something to do with not auto detecting the card correctly.

---

### Post by stream303 on 2006-12-18
Be sure you are using a version of **Edgy,** not Dapper.  Only Edgy boots the G5 iMac properly.  You will have to suffer through the screaming fans during install, but once installed you can quiet them with:

```
sudo -s
cd /lib/modules/$(uname -r)/kernel/drivers/macintosh
ls | cut -d. -f1 | xargs -n1 modprobe
lsmod | cut -d" " -f1 | grep windfarm >> /etc/modules
exit
```

Now the fans will be quiet upon reboot from here on out.

---

