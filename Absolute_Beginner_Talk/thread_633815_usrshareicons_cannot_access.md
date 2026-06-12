---
title: "/usr/share/icons/ cannot access"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by uberlube on 2007-12-06
Ok so I have downloaded the Glossy-glass icons and it says to add the icons to the /usr/share/icons/ folder but i dont have permission to write to there. Is there a way around this?

---

### Post by PeterJS on 2007-12-07
That's actually a security feature for you protection. On windows (I assume you're a new convert) users are used to running as an admin account that will let them do anything at anytime with out asking questions. This is an incredibly bad idea, if you run malicious software, or you're system is attacked, once the attacker gets in that's it there are no more security measures.

On Ubuntu even with an admin account, you still have to verify with your password before writing to any system file, like say /usr/share/icons/. There is an application, sudo (Super User do), that will allow you preform commands with elevated privileges.  There's also a graphical version called gksudo that does the same thing.

Try pressing alt+f2 to get the run dialog and enter:
```

gksudo nautilus

```to open a file browser with elevated privileges.
Here's the documentation on sudo and admin privilages, it's worth reading as it's something you're going to want to understand when making system changes.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by crimesaucer on 2007-12-07
> **uberlube said:**
> Ok so I have downloaded the Glossy-glass icons and it says to add the icons to the /usr/share/icons/ folder but i dont have permission to write to there. Is there a way around this?

Assuming that you have unpacked the .tar and now have a folder named "Glossy-glass" that you want to upload to /usr/share/icons, all you have to do is use your terminal and the sudo (root privileges) command:

```
sudo mv Glossy-glass /usr/share/icons
```

or copy it to the /usr/share/icons

```
sudo cp -r Glossy-glass /usr/share/icons
```

---

### Post by uberlube on 2007-12-07
Worked like a charm, thanks for the tidbit, im sure ill be using it again soon!

---

