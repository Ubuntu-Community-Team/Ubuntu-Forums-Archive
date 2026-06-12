---
title: "BusyBox error at loading screen"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by anitract on 2008-01-22
New Ubuntu install of amd64 version.   This is a pure Ubuntu system.  When I boot or reboot my machine the loading screen will immediately freeze. After a few seconds I get:

BusyBox v1.1.3 ...
Enter 'help' for a list of built-in commands

(initramfs) [  232.879929] ata4.00: failed to set xfermode (err_mask=0x40)
[  268.023325] ata4.00: revalidation failed (errno=-5)
[  303.166727] ata4.00: revalidation failed (errno=-5)
[  308.169741] ata4.01: failed to set xfermode (err_mask=0x40)
[  343.313128] ata4.01: failed to set xfermode (err_mask=0x40)
[  378.460517] ata4.01: failed to set xfermode (err_mask=0x40)

I have noticed that the [numbers]  and ataxxxx differ each time this occurs.  But the errors are the same.

If I ctrl-alt-delete to restart it will go back to this again.  However, ctrl-alt-delete one more time alllows me into the OS.  At that point everything works perfectly.  Can anyone give me insight or point me in the right direction to look here (error logs?)?

This looks like a potential solution...
[http://ubuntuforums.org/showthread.php?t=474693&highlight=BusyBox+v1.1.1](http://ubuntuforums.org/showthread.php?t=474693&highlight=BusyBox+v1.1.1)
...but the author of that thread does not even know why it works...

---

### Post by anitract on 2008-01-22
I forgot to add that my system doesn't always do this.

This morning when I booted it, it did.

I haven't been able to get it to do it again today since then though.

I have noticed (might be a coincidence) that its happened after software updates and a nvidia driver install.

---

### Post by anitract on 2008-01-22
Looks like a better fix is out there.  The all_generic_ide arguement seems to be the route that fixes most issues.  I have added that argument to the appropriate file.  We'll see how things go as this issue is sporadic to begin with.

---

### Post by seren6ipity on 2008-01-31
> **anitract said:**
> I forgot to add that my system doesn't always do this.

This morning when I booted it, it did.

I haven't been able to get it to do it again today since then though.

I have noticed (might be a coincidence) that its happened after software updates and a nvidia driver install.

I too got this error after changing driver to nvidia. Unable to fix it :(

---

### Post by oedha on 2008-01-31
that's not related to nvidia.......
do what anitrac said.......put "all_generic_ide" on the boot menu
it is harddisk identification problem.....

~E~

---

### Post by saberman on 2008-02-03
I am also getting the BusyBox problem.  Unfortunately, I have both IDE and SATA drives.  If I add all_generic_ide I get a load of error messages about bad commands and get dropped back into BusyBox.

Any other suggestions?

---

