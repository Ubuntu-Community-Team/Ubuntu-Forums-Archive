---
title: "Fiesty fails to boot"
date: 2007-02-17
forum: Apple PPC Users
---

### Post by Seth Quarrier on 2007-02-17
I just upgraded to Fiesty, which was probably a bad idea as I have continuously upgraded my system from at least Dapper. Now when I boot, the splash screen appears and advances once. After that the computer hangs. Has anyone experienced this or does anyone know how to disable the boot screen in order to see what is going on. 

Thanks

---

### Post by grazie on 2007-02-17
You don't say which version of the release you got, but I've been trying quite a few recently - some booted, some didn't. If you've just been upgrading from the repos it not easy to know exactly what you've got. Also, there's been quite a lot of problems with the kernel packages recently, so that most likely is the problem.

To see the boot messages you can take out "quiet splash" from /etc/yaboot.conf  entry (I'm assuming New World) or more simply hit alt+F1 on booting.

---

### Post by Seth Quarrier on 2007-02-17
For anyone experiencing the same problems, the issue that I had was a kernel panic when loading usplash. I used chown to remove usplash and the issue went away. The kernel was paging an address it couldn't read. You will know if you have this issue as the boot screen will hang for several minutes and then fall into a kernel dump which will have in it the text 'Task usplash-write'.

---

