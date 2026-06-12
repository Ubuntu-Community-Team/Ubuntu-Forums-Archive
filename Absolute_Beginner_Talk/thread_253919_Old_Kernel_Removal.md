---
title: "Old Kernel Removal"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-09-09
I have two old kernals on my PC that I want to get rid of, to free up some HDD space.

One is the i386 Kernal, that was loaded from the Live CD.

Another is the i386 updated Kernal, that was automatically downloded when the new system rang home.

I have since dowloaded the i686 Kernal, which has been operating without flaw for a week now.

How do I remove these Kernels and remove the entries in the Grub loader? 

Regards,
Roger 8)

---

### Post by bulldog on 2006-09-09
Synaptic can do this for you.
Look for the kernels you want to delete and do so [uninstall]

Then open your menu.lst with gedit with root permisssions [gksudo] and delete the entry's you don't want anymore.

Watch carefully what you are going to uninstall and every thing must be fine.

Simple as that.

---

### Post by mgor on 2006-09-09
```
sudo dpkg --list | grep linux-image-2.6
```
to list the installed kernels and you can go and do a,
```
sudo apt-get remove linux-image-<version>
```
for those who DON'T match the output of,
```
uname -r
```
apt-get should update grub, but to be sure you can run,
```
sudo update-grub
```

---

### Post by mgor on 2006-09-09
> **bulldog said:**
> ...
Then open gedit with root permisssions [gksudo] and delete the entry's you don't want anymore. 
...

You don't want to remove kernel entries in /boot/grub/menu.lst manually, update-grub will take care of this for you.

---

### Post by ramjet_1953 on 2006-09-09
Thanks, Guys!
Piece of cake!
My grub loader looks much cleaner now, too.

Regards,
Roger :D

---

