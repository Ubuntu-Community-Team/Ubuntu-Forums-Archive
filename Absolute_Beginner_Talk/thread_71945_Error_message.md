---
title: "Error message"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by bugsout on 2005-10-04
I just reinstalled Hoary.
 If I type "sudo /etc/hdparm.conf" in a terminal to change my DMA settings I get."command not found" .  I had used the very same command before and had no problem. Any idea's ?

---

### Post by SilentCacophony on 2005-10-04
you forgot the editor:

sudo **nano** /etc/hdparm.conf

---

### Post by Mustard on 2005-10-04
or 

```
sudo gedit /etc/hdparm.conf
```

if you are using gnome and want a graphical interface.

---

### Post by bugsout on 2005-10-04
Thanks, nano did not work for me ,but then I remembered gedit had to go in the command line, like you posted and worked fine.

Thanks again.............

---

