---
title: "t61 nvidia suspend solved- sort of"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by sc30317 on 2007-12-07
I have found a script that works great to make my laptop suspend!

```
#!/bin/sh

# if launched through a lid event and lid is open, do nothing
echo "$1" | grep "button/lid" && grep -q open /proc/acpi/button/lid/LID/state && exit 0

# remove USB 1.1 driver
rmmod uhci_hcd
rmmod ehci_hcd

# sync filesystem and clock
sync
/sbin/hwclock --systohc

# switch to console
FGCONSOLE=`fgconsole`
chvt 6

# go to sleep
sleep 5 && echo -n "mem" > /sys/power/state

# readjust the clock (it might be off a bit after suspend)
/sbin/hwclock --adjust
/sbin/hwclock --hctosys

# reload USB 1.1 driver
modprobe uhci_hcd
modprobe ehci_hcd

# turn on the backlight and switch back to X
chvt $FGCONSOLE

```

However, I have to type sudo sh script sh to make it work.  How can I map this so that when I push FN + F4 ( the default suspend buttons) this script will work?

---

### Post by sc30317 on 2007-12-07
bump

---

### Post by sc30317 on 2007-12-09
anyone?

---

### Post by Virnik on 2008-02-07
hi there, it is little late, but u can use this:
[http://www.linux.com/articles/54610](http://www.linux.com/articles/54610)

I have used your script...and it is really nice, that it works.

---

