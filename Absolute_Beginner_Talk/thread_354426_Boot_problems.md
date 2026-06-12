---
title: "Boot problems"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by ubunick on 2007-02-05
For SOME reason, on both Dapper and Edgy, I'll install them and then reboot and voila.. they stall at the loading screen or afterwards show a blank screen.  It's odd tho, I'm running openSuSe and it doesn't have issues booting -- so what could be the problem? It's perplexing. Your thoughts?

---

### Post by shareMenaPeace on 2007-02-06
When you boot can you choose recovery mode and than do you get any error messages?

If so post them here please.

---

### Post by rccharles on 2007-02-06
> **ubunick said:**
> For SOME reason, on both Dapper and Edgy, I'll install them and then reboot and voila.. they stall at the loading screen or afterwards show a blank screen.  It's odd tho, I'm running openSuSe and it doesn't have issues booting -- so what could be the problem? It's perplexing. Your thoughts?

You can turn on a 'verbose' mode when booting up.  I have changed my boot to work this way.

Press the esc key just after you power on the machine.  

Press e to edit.  It should be the first line on the list of partitions/files to boot.

Cursor down to the kernel line.

Press e to edit.

delete the 
  quite splash
options.

This will give you more messages on boot.

Press the return key

Press the b key to boot.


if you like these changes you will have to edit:
/boot/grub/menu.lst
..............

I am thinking that you X11 profile could be incorrect.  What you may need to do is to copy a working profile from a working system.  How far the boot messages get will better tell of this situation.

The file is:

/etc/X11/xorg.prof

Robert

---

### Post by Mba7eth on 2007-02-06
reboot and wait tell the screen get blank . get into any tty consel (Ctrl+Alt+F1 .i.e). 
Know your hardware specifications. then 
```
$ sudo dpgk-reconfigure xserver-xorg
```
to reconfigure ur xserver. 

If didn't work, just tell us ur box specifications, and model of peices ?

---

### Post by Mba7eth on 2007-02-06
Ohh forget to tell . once you are done from reconfiguring ur xserver. type  :
```
$startx
```
to test ur xserver configurations.

---

### Post by lnxnubie on 2007-02-06
i had simillar problems but i found out that it was filesystems problem. i had choosen xfs and grub was having some problem with it

---

### Post by ubunick on 2007-02-06
It's not an x problem.

---

