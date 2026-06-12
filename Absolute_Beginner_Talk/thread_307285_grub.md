---
title: "grub"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by geordie chris on 2006-11-26
how do i edit grub so windows starts as default

---

### Post by bulldog on 2006-11-26
Open your menu.lst```
gksudo gedit /boot/grub/menu.lst
```
Now alter this part,and replace the zero with the number you get when you count all the entry's in your menu.lst.

Your standard ubuntu is count as zero,the safe mode is one and your mem test is two and so on till you reach the windows entry.
That number you should place at the mentioned zero.
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0 <----
```

---

### Post by Irony on 2006-11-26
Where it says;
[PHP]
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0[/PHP]

default 0 refers to the first entry (usually Ubuntu), if Windows is the 4th entry change it to 4.

Note you have to count recovery and mem-tests as boots and also confusingly the part where it says;

[PHP]# This is a divider.
title		Other operating systems:
root[/PHP]

Thus if you have only Ubuntu and Windows then change 0 to 4.

---

### Post by geordie chris on 2006-11-26
thanks think i understand

---

