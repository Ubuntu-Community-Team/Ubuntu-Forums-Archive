---
title: "restricted drivers console won't open"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-23
Hi, when I go to open restricted drivers it gives error

need to install linux-restricted-modules-2.6.22-14 server

I tried searching synaptic. (no luck)

Tried ```
 sudo apt-get install linux-restricted-modules-2.6.22-14 server 
```

Tried it with - between "14" and "server" too but I get "E: Couldn't find package linux-restricted-modules-2.6.22-14-server" both ways.

I'm running server AMD64 with desktop and gnome installed. I allready installed nvidia-glx and my video seems to be fine, so do I even need to install the restricted driver? If yes, then where can I find the restricted modules package?

---

### Post by iansane on 2008-03-23
according to a bug report, apparently the package does not exist so I can remove the server kernel and not have a server any more or after spending all day trying to make this work, I can install Hardy which claims to have fixed the bug. Boy I'm glad this is a learning process and not a mission critical thing for me. Shouldn't the bug be fixed in the current distro instead of waiting for a new distro? Oh well, I'm glad Ubuntu has come so far so I won't complain.

---

### Post by iansane on 2008-03-23
They fixed it alright. removed the restricted driver console all together.

---

