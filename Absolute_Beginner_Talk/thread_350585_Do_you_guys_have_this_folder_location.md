---
title: "Do you guys have this folder location?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by hyby on 2007-01-31
Hello guys,

I was wondering do guys have the following folders:

/usr/src/modules/alsa-driver/debian

I am trying to recombile my ALSA drivers, however i can not get started because i need to try this command: 

cp -Rp /usr/src/modules/alsa-driver/debian alsa-driver-1.0.14rc1

However, whenever i tried this command, i get : 

cp: cannot stat `/usr/src/modules/alsa-driver/debian': No such file or directory

I was wondering what do the -Rp switches do?

Thanks for your assistance.

---

### Post by tchoklat on 2007-01-31
I only have these -

/usr/src/linux-headers-2.6.17-10
/usr/src/linux-headers-2.6.17-10-386
/usr/src/linux-headers-2.6.17-10-generic
/usr/src/rpm



tony

---

### Post by RomeReactor on 2007-01-31
Hi. the -R option is used for recursive copying of directories; the -p is used to preserve mode and ownership of whatever is being copied. I suggest you look for that folder using nautilus; open it and click the "Computer" button, then "Filesystem" then "/usr", "/src" and see whether the rest are there or not.

---

### Post by hyby on 2007-01-31
Thanks, guys.

I have looked through Natulis, but the following folders aren't there. 

I will have to do some snooping around.


Cheers

---

