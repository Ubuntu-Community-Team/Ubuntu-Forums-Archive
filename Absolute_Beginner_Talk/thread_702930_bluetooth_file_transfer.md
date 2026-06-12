---
title: "bluetooth file transfer"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by da Wookiee on 2008-02-20
Operating systems involved.  Ubuntu Gutsy Gibbon 7.10 and Windows Vista Home Premium

I have bluetooth adapters installed on both machines, and the gnome-obex-server is up and running, but I can't seem to figure out how to send files through the pipe.  

the pc's are paired, btw.  

Which steps am I missing?

---

### Post by talsemgeest on 2008-02-21
Try installing bluez-utils ```
sudo apt-get install bluez-utils
```

---

### Post by da Wookiee on 2008-02-21
Bluez utils was installed.  What I realized was that I had not turned on the file transfer service on the Vista Machine.  Also looking closer on the gnome menu I finally noticed the send to option.

Thanks for your reply.


Now how do I mark a thread solved?

---

### Post by talsemgeest on 2008-02-21
It should be under the thread tools menu at the top of the thread. Glad you got it working!

---

