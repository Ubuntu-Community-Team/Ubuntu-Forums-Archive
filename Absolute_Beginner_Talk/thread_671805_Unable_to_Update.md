---
title: "Unable to Update"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2008-01-18
I am using 7.10 when I try to update there is one file for Xserver-Xorg-Core that I get this message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden

The rest of the files installed properly.  What is going on?

---

### Post by bwtranch on 2008-01-18
Do you have all your repositories enabled?

---

### Post by weaver4 on 2008-01-18
That did it, thanks!

---

### Post by PmDematagoda on 2008-01-18
You should reload your sources list. Execute:-
```
sudo apt-get update
```

That should fix your problem.

---

### Post by jahisthebalance on 2008-01-18
I had to enable the "unsupported" repository to get it to go, which is sort of wack because how did it show up in my update queue in the first place? oh well, onward and upward

---

### Post by Fanless_Puppy_Fan on 2008-01-18
I thought that update broke java. There are tons of posts on the 403 error, but I can't tell if the original reason someone shut down the update has been fixed. Anyway, I will wait for a while before updating that package.

---

### Post by michaelzap on 2008-01-19
If I were you I wouldn't reboot until there's a fix available for that update. It was blocked from the official repos because it caused a whole lot of trouble for many people (including no graphical interface at all for some). If you have to shut down before a new update is available, search the forums for fixes (there are tons of threads on this, and in particular there's a config change that you can make that seems to keep X server from crashing for now).

---

