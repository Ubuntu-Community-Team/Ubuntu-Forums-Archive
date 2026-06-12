---
title: "tried to switch my username and accidentally deleted myself"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by emu on 2006-07-23
hi,

I know this is a total n00b problem but I tried to change my username to something else by editing the /etc/passwd file, and now I can't login under either the old or the new name!  it seems I've just inadvertantly deleted myself.  I am currently working off of the live cd, and I just installed Ubuntu yesterday, dual-booting with winxp.

is there anything I can do to fix this?  or should I just reinstall?  any help is greatly appreciated.

thanks,
emu

---

### Post by xXx 0wn3d xXx on 2006-07-23
> **emu said:**
> hi,

I know this is a total n00b problem but I tried to change my username to something else by editing the /etc/passwd file, and now I can't login under either the old or the new name!  it seems I've just inadvertantly deleted myself.  I am currently working off of the live cd, and I just installed Ubuntu yesterday, dual-booting with winxp.

is there anything I can do to fix this?  or should I just reinstall?  any help is greatly appreciated.

thanks,
emu
Can you boot into recovery mode and then add a new user with the "adduser" command ? That should work. Or maybe you could edit the /etc/passwd file back to it's origional state.

---

### Post by aysiu on 2006-07-23
The adduser command, by the way, is ```
adduser emu
``` Then follow the prompts (creating a password, etc.). Then ```
adduser emu admin
``` That will make sure you have *sudo* privileges. Then ```
reboot
``` and go into regular (not recovery) mode.

---

### Post by emu on 2006-07-23
yay for recovery mode!  good to know about.  thanks for your help, it all seems to be working now  :D

edit: oops, one more thing:  yesterday, I could access the windows partition (the drive IBM_PRELOAD which is on the desktop) but now when I open it it says 'you do not have the permissions necessary to view the contents of "sda1".'  how do I give myself that permission?

thanks again

---

