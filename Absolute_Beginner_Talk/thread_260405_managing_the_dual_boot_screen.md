---
title: "managing the dual boot screen"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-09-18
Ok this title wasn't great =P 
U know when u're dual booting, it's suppose to display your different OS. the thing is, i already made a lot of updates and now i have like 8 different linux kernels and it kinda looks bad :rolleyes: Apart from that, how can i change the default OS ?

---

### Post by Najand on 2006-09-18
Go and edit /boot/grub/menu.lst
and go to the bottom of the file...
Then comment the sections you do 
NOT need any more (the part that
starts with "title" and the name of
unneccessory kernel to the next one)
with # sign. You will not see any more
of them in your grub boot menu.

[COLOR="Red"]NOTE:[/COLOR] Don't comment your the recovery
boot section of your latest kernel or
yoou would be in a trouble when something
goes wrong.

---

### Post by seshomaru samma on 2006-09-18
in /boot/grub/menu.lst you will see a line like this:
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```
this means that the default OS is the first option on your boot menu
If you change the number to 1 then the second option on the boot menu becomes the default OS , if you change the number to 2 the 3rd option becomes default  and so on....

---

