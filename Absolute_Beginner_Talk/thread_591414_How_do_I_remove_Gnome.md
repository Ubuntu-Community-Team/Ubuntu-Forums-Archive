---
title: "How do I remove Gnome?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by BCPower on 2007-10-25
My server is currently running Gnome but I want to get rid of it because I want to install Zimbra.  How do I get rid of Gnome?  Also, how can I simply exit Nautilus all together and get back to the CLI?

---

### Post by aysiu on 2007-10-25
I don't know what Zimbra is, but why do you have to uninstall Gnome in order to install Zimbra?

If you want to exit Gnome completely to get back to CLI, press Control-Alt-F1, log in, then type ```
sudo /etc/init.d/gdm stop
```

---

### Post by BCPower on 2007-10-25
Thanks.  Is there a way to keep Nautilus.Gnome from loading after every reboot?

---

### Post by aysiu on 2007-10-25
> **BCPower said:**
> Thanks.  Is there a way to keep Nautilus.Gnome from loading after every reboot?
Sure. ```
sudo /etc/init.d/gdm stop
sudo apt-get remove gdm
```

---

