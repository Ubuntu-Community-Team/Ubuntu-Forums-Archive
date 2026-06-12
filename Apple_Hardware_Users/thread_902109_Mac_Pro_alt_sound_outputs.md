---
title: "Mac Pro alt sound outputs?"
date: 2008-08-27
forum: Apple Hardware Users
---

### Post by cwestpha on 2008-08-27
I have a early 08 Mac Pro and have the Intel HDA audio working properly using the internal speaker (have to change 2ch to 6ch as clicking the speaker button does zip). However I am unable to get it to export the sound stream over the line out port to my powered speakers. Anyone know how to do this? I have tried playing with it for hours and searching all over the internet.

---

### Post by joe.inom on 2008-08-27
It might be the problem with your line jack cause i have also faced the same problem.You see , i waste $5 each month to change the line jack and the jumpr for my laptop.

---

### Post by cyberdork33 on 2008-08-27
you have to get a newer version of ALSA. 

[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

---

### Post by cwestpha on 2008-09-09
hmm... if only it was so easy...

```
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/home/cwestpha/Desktop/alsa-utils-1.0.18rc3/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cwestpha/Desktop/alsa-utils-1.0.18rc3/alsactl'
make: *** [all-recursive] Error 1

```

---

### Post by cyberdork33 on 2008-09-09
Looks like the 'xmlto' command is needed. Need to find the package that it is a part of and install it, then try again.

---

### Post by cwestpha on 2008-09-12
odd I did a fresh install of Ubuntu 8.04.1 on my mac pro (normal no swap, normal GRUB, used gpartd to set partition as boot) and booted to it using the bootcamp selector (not rEFIt) and now the sound works perfectly out of the box. o.O

---

### Post by cyberdork33 on 2008-09-12
> **cwestpha said:**
> odd I did a fresh install of Ubuntu 8.04.1 on my mac pro (normal no swap, normal GRUB, used gpartd to set partition as boot) and booted to it using the bootcamp selector (not rEFIt) and now the sound works perfectly out of the box. o.O
Well, IDK glad you got it working.

---

