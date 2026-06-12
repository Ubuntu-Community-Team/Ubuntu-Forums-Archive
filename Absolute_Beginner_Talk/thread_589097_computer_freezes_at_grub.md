---
title: "computer freezes at grub"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by vertex78 on 2007-10-23
Well i upgraded to 64 ubuntu and it worked for awhile until now. Now it when it gets to the screen that says grub is loading it freezes up.  So I am stuck running on a liveCD while I try and figure it out.  I figure the best place to start would be to reinstall grub.  So here is what I did

```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,2)
grub> root (hd0,2)                   
root (hd0,2)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,2)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> 

```
So now I am gonna reboot and see if it worked...

---

### Post by vertex78 on 2007-10-23
that did the trick...

---

