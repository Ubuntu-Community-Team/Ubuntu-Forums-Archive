---
title: "need some help with grub"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by at0mic on 2006-11-19
hi, trying to config grub for vista and am curious if my grub menu is right...

/dev/hdb1 is where windows is. on the one and only partition.

menu.lst readout for gruB. Is everything correct?

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Vista
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by at0mic on 2006-11-19
i think it should be hd1 instead of hd2 because they count 0. brb

---

### Post by at0mic on 2006-11-19
sayz bootmgr is missing. doh

---

### Post by at0mic on 2006-11-19
looks like ill have to recovery repair vista

---

### Post by bulldog on 2006-11-19
It seems to be that GRUB and Vista don't work well.
Although I've read about people who did it without a prob.

Just search these forums about it,it should be stated somewhere.

---

### Post by b_martinez on 2006-11-19
> **at0mic said:**
> hi, trying to config grub for vista and am curious if my grub menu is right...

/dev/hdb1 is where windows is. on the one and only partition.

menu.lst readout for gruB. Is everything correct?

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Vista
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


How many hard drives do you have and what type. You posted that Windowns is on hdb1 (/dev/sda1) so it probably should read

title		Vista
rootnoverify    (hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

hth
Bill

---

