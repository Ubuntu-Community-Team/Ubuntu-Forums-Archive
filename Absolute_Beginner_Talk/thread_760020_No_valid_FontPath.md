---
title: "No valid FontPath"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by vba_djs on 2008-04-19
I installed Ubuntu 7.10 server on a new box.

Because I occasionally want to go into the desktop, I installed xserver-xorg.

When I run startx, I get the following error message:

Fatal server error:
No valid FontPath could be found.
X10: fatal io error 104 (Connection reset by peer) on X server.

Do I have to install anything else?

Thanks,

---

### Post by joshrobinson on 2008-04-19
have you tried
```
sudo apt-get install ubuntu-desktop
```

---

### Post by vba_djs on 2008-04-19
Thank you very much.

That did the trick.

---

