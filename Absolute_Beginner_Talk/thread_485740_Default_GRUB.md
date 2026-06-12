---
title: "Default GRUB?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-27
as some of you may alrrady knopw, i have had some real trouble with my grub menu.

it akll works! 

but when i load windows, that becomes default and loads automatically!
so i have to live cd and  change the flag to my ubuntu whuich is Boot flag

is there a way to "lock" grub? to stop windows' queerness from  auto loading? :D:popcorn:

---

### Post by Seisen on 2007-06-27
Can you post your grub menu?

```
gedit /boot/grub/menu.lst
```

---

### Post by ruza on 2007-06-27
Try editing your /boot/grub/menu.lst(i thunk that path is correct)
put ubuntu section before win

---

### Post by skymera on 2007-06-27
it is before windows!!!
when i boot ubuntu grub appears next boot.

but if i boot windows...
it stay default

---

### Post by Seisen on 2007-06-27
Open up your grub menu and look for a the line that says 

```
default 0
``` it might be a different number and make sure that it says 0 and it should automatically start Ubuntu at boot up instead of Windows.

---

### Post by skymera on 2007-06-27
all i want is a grub menu that i can choose.

this seems to be hardwer than i thought.

---

### Post by Seisen on 2007-06-27
So it doesn't even give you time to choose which OS?

Find this line and change it to 10

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		3**

```

---

