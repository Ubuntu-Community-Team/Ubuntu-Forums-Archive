---
title: "btsco problem"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-24
.
   
im following an instrucion from a thread to install bluetooth 

*1. Load Kernel Module for btsco: "sudo modprobe btsco", checking "dmesg" if it runs. To load it permanently add it to /etc/modules, just write "btsco" at the end of the File*

but when i do it.. i get this message

[INDENT]sudo modprobe btsco
Password:
FATAL: Module btsco not found.
   [/INDENT]

what should i do ?

---

### Post by HunkieChan on 2007-03-24
can anyone please help me /

---

### Post by invalid on 2007-03-24
Where is the thread you are following? Have you installed the module yet?

---

### Post by HunkieChan on 2007-03-24
> **invalid said:**
> Where is the thread you are following? Have you installed the module yet?

[http://ubuntuforums.org/showthread.php?t=75978](http://ubuntuforums.org/showthread.php?t=75978)

this is the thread ^... i think i did, how do i reassure ?

---

### Post by HunkieChan on 2007-03-24
#

Check /etc/bluetooth/hcid.conf:

    *

      security should be user.
    *

      pairing should be multi.
    *

      pin_helper should be /usr/bin/bluez-pin.


it also asks me to this ^.. but i cant never find "pin_helper" in that file.. whats the problem ?

---

