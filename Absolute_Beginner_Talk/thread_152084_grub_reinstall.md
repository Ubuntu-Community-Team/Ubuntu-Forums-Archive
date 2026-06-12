---
title: "grub reinstall"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by champ_rock on 2006-03-29
don't know if this is the right section or not.. but anyways...
regarding this post..
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

i tried the live cd method as I thought that i will be able to manage......

but when i load the live cd everything goes fine...
i enter the grub command
grub terminal opens up.....

then when i press root (hd0,2) and press enter then it says that the selected disk does not exist???????
i have treid to change it to hd1,hd2,hd3 etc. and ,0,1,2,3,4,5,6, etc. but it shoes the same error .......

also, i tried that maybe the partition was not mounted therefore, i mounted the partition in a folder on the desktop...

any suggestions or solutions where i am going wrong?????????

---

### Post by cronholio on 2006-03-29
Are you sure it's (hd0,2)? How are your partitions set up? You can boot the live cd, run fdisk and press p to see the partition table.

By the way, for installing grub the partition doesn't need to be mounted.

---

### Post by champ_rock on 2006-03-29
i checked using paragon partition manager in windows only.. .it syas that my linux partition is hd0,2 or hda3

i have got only one disk (therefore it is hd0 surely)

1. hd0,0- windows2000
2. hdo,1 windows xp 
3. hd0,2 linux

thwen i have 2 extended partitions - swap and one fat

---

### Post by cronholio on 2006-03-29
You might want to try:

```
sudo grub-install --recheck /dev/hda
```

---

### Post by champ_rock on 2006-03-29
thanks man for your help....

i decided to take some risk and went for the first method i.e. to use the install cd... and it went on well..

i am currently using linux only.... thanks man for ur help anyways

---

