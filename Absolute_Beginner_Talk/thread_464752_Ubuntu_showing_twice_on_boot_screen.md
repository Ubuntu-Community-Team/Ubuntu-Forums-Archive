---
title: "Ubuntu showing twice on boot screen"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by GlennM111 on 2007-06-05
Hi guys,

I updated ubuntu last night through the notifier and this morning the boot screen is showing double entries of ubuntu, its "safe" mode and ubuntu + memtest is there anyway of removing the double entry as im aware you could do this by modifying the boot.ini in windows.

Thanks in advance

---

### Post by Inxsible on 2007-06-05
thats because you updated with the latest kernels 2.6.20-16.

I would advise against un-installing the older kernels since, many ppl have ahd problems with the -16 kernel and it would be a good idea to keep your older (-15) around, just in case -16 gives you problems too.

There are ways to change the default ubuntu kernel and also ways to delete it from the menu or completely un-install the older kernels. But you should do this only if you are sure that the new ones work for you.

All in all, rule of thumb is to keep atleast one older( and stable) kernel around

---

### Post by daschmidty on 2007-06-05
Is it a case of one safe mode+one "ubuntu" or two sets?
If it is two sets this is because your latest upgrade has installed an updated kernel image which created a new boot entry for itself. It is possible to limit the number of entries..but I wouldn't recommend limiting it to one, for safety reasons. Most new kernel images run into trouble with some hardware/software setups on release before everything can be adequately tested and bugs worked out. So if you set GRUB to only show your newest kernel, you may someday upgrade and be left with an unbootable system. I would recommend leaving two kernel images in the boot list for stability concerns. At any rate here's how to change it:

open the file /usr/sbin/update-grub (as root) in an editor. about 320 lines or so down you will find some options pertaining to the default menu.

One of them is:
# should grub create the alternative boot options in the menu
        alternative="true"
if you set this to "false" the safe modes will be removed from the list (not a good idea)

and the other is# controls howmany kernels are listed in the config file,
# this does not include the alternative kernels
        howmany="2"
where howmany is the number of kernels(2 sets of ubuntu 2.6.20-xx-generic+recovery mode)

to apply the changes open a terminal and run
```
sudo /usr/sbin/update-grub
```

---

### Post by GlennM111 on 2007-06-05
Appreciate the help guys

---

