---
title: "how can i delete a kernel"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by airzer0 on 2006-06-13
currently i have 4 kernels and xp to chose from, so how can i get rid of the other 2 so i just have breezy dapper and xp. i installed the others so i could just check them out in case you wonder

---

### Post by Ctrl+Alt+Del on 2006-06-13
edit your /boot/grub/menu.lst and remove the entries you don't want, additonally you can delete the kernel image in /boot and the corresponding modules in /lib/modules, should be pretty selfexplanatory.

---

### Post by cbudden on 2006-06-13
Search in synaptic for linux-image and remove the ones you are NOT using (to find out the running kernel type uname -r in the terminal (Applications -> Accessories -> Terminal )) Be careful not to remove the kernel you are running, otherwise bad things will happen :P.

---

### Post by airzer0 on 2006-06-13
lol

---

### Post by airzer0 on 2006-06-13
i man. installed 2.6.16 it did not show up on synaptic, so how can i del that one

---

### Post by halfvolle melk on 2006-06-13
Don't remove them. They don't take up a lot of space and you might need them if you ever bork your system. (Guessing here)One is a memtest, one is failsafe mode, one is the default that got installed and the last one is a newer verion you installed. There's no harm in leaving it like that.

---

### Post by airzer0 on 2006-06-13
yea boy (edit your /boot/grub/menu.lst and remove the entries you don't want, additonally you can delete the kernel image in /boot and the corresponding modules in /lib/modules, should be pretty selfexplanatory.) compelety self explanatory love the quick answer thanks

---

