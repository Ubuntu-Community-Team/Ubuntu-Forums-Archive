---
title: "Very looong boot"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by wiktor91 on 2008-02-02
When i turn on computer i have to wait at least 3 minutes after GRUB loader to boot... 
I had Ubuntu earlier and it took a few second to boot but now when i installed 7.10 it takes at least 3 minutes to boot. 

Can i do something to solve this?

---

### Post by cubeist on 2008-02-02
when grub comes up, press esc and then select the linux boot path and press "e" and on that line remove the word splash.  Don't worry, this is not a permanent change.  Once you remove that go back to the menu and use "b" to boot.  Without splash you will be able to see each step of the boot process and see what step is taking so long.  Once you know that, post back.

---

### Post by dstew on 2008-02-02
Another thing to try is install the bootchart program. It creates a graphical picture of the boot process, and you can often see where it gets stuck. The program puts the picture in the /var/log/bootchart directory.

---

