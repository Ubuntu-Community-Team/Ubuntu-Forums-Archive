---
title: "Login Help"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by jfrailing on 2007-07-29
Hello,

I am using Xubuntu 7.04 Alternate i386 on a Dell Latitude CPi Pentium II with 128 MB of memory.

I changed a setting somewhere and now I am getting the following warning after I enter my name and password:

     User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved.      File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

Thank you,
Jim

---

### Post by splintercellguy on 2007-07-30
I'm assuming the file is owned by your user account. Do this:

chmod 644 ~/.dmrc

---

### Post by st33med on 2007-07-30
That little pop-up was unusually informative. Not that it's bad, but I guess this is another advantage over Windows. If there is a BSOD, all you get is a STOP code. Doesn't tell you what's wrong with a file/driver/hardware/etc. And then, sometimes you can only have that fixed by sending it to the Computer manufactures or MS because their is something wrong with a code/hard-drive/whatever. In other words, their is little you can do to fix a problem without sending it to an expert.

---

