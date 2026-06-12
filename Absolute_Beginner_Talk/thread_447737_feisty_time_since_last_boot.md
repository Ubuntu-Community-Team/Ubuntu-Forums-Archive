---
title: "feisty time since last boot"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by mgvbstar on 2007-05-18
Hello,

In edgy, running "uptime" would tell me the time since my last boot.  After upgrading to feisty, running "uptime" tells me how long my computer has been powered on since the last boot.  Since I use hibernate/resume a lot, I like to know how long it has been since I have actually restarted my system.  Is there any way to get the old edgy behavior back? Thanks.

---

### Post by JReagan1990 on 2007-05-18
You might want to try adding the Edgy repository back to your /ect/apt/sources.list file.  So, find out which one it is in, uninstall the package, and then install the one coming from the older repository.

---

### Post by Najand on 2007-05-18
> **JReagan1990 said:**
> You might want to try adding the Edgy repository back to your /ect/apt/sources.list file.  So, find out which one it is in, uninstall the package, and then install the one coming from the older repository.

OH! Changing sources.list  to edgy/dappr/breezy/hoary and upgrading might break your system though. Be very careful!
I haven't seen much changes in the source code for "uptime" in edgy and feisty. It just read /proc/uptime and change it to hour:minute format.

---

### Post by heimo on 2007-05-18
I read changelog for uptime between Edgy and Feisty and there is nothing that would change this behaviour. But searching google showed some discussion about how uptime should behave when in suspend - so this is more probably kernel change than userspace tool change.

---

### Post by mgvbstar on 2007-05-18
Thanks for the replies.  So if is not actually a change in uptime but rather a change in the kernel, is there any way that I can find the time since I last rebooted?

---

### Post by Najand on 2007-05-18
Does "last" command help you?

---

### Post by mgvbstar on 2007-05-18
Yes! Thanks Najand. Just what I was looking for.

---

