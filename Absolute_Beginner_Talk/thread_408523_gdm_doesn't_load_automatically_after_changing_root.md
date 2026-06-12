---
title: "gdm doesn't load automatically after changing root and user passwords"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by miyln on 2007-04-13
Hi, 

Bear with me, I'm completely new to Ubuntu. I had to change my password last night; ever since then, Ubuntu won't get past the startup screen. It barely begins loading. However, I'm still able to load gdm through recovery mode.  

I changed my password using this tutorial:
   1. At system boot, when Grub menu appears, select Recovery. Eventually, a root (#) command line appears.
   2. Use “cd /etc” and “tail passwd” to see the last part of the password file. You’ll see your login name.
   3. Use “passwd login name” and it will prompt you for a new password.
   4. Press Ctrl-D and the X window will begin and you’ll be able to login.

I ended up changing both the "UNIX password" and my user password to the same phrase. I'm not sure if this is what's preventing gdm from loading; I also uninstalled beryl (through the package manager) before rebooting to change my password. How can I get gdm to load without going through recovery mode? I'd like root to not have a password, like how it is by default - how can I change this back?
Any help is greatly appreciated!

---

### Post by xopher on 2007-04-13
> I'd like root to not have a password, like how it is by default - how can I change this back?

```
sudo passwd -d root
```

---

