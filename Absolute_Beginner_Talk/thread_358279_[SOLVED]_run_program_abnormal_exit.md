---
title: "[SOLVED] run_program abnormal exit"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by freddybob on 2007-02-10
This is really not my day. :( 

After fixing the nvidia driver problem from the kernel update, I realised that I no longer had any sound.

I tried lots of the suggestions in the Comprehensive Sound Problem Solutions ([http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)) and somewhere in there I broke something.

I think it was after I modified:

> sudo nano /etc/modules

Anyway, the problem now is that Ubuntu won't boot.  It just says:

> devd-event[2926]: run_program 'sbin/modprobe' abnormal exit

At that point the system hangs.  I cannot get to a command prompt (even in recovery mode) so how do I undo whatever it was I did?

In recovery mode it hangs at the message:

> NET: Registered protocol family 17

---

### Post by risbac on 2007-02-10
Wow :) that's a serious one!

Did you try a liveCD, then modify the modules file again? That's what I would try. Or access to the file from Windows using an EXT2 driver.

---

### Post by freddybob on 2007-02-10
Fixed it using a LiveCD.

It was the /etc/modules file that I had modified - I removed the line that I had added.

---

