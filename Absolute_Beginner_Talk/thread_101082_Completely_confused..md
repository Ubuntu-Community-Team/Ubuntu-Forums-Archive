---
title: "Completely confused."
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by Protoman on 2005-12-09
Well I got my CD's today and tried installing with them.  5 CDs were failing just doing the normal install.  Since I didn't feel like trying the 5 more left, I just went ahead and did a mininum/server install.  Thought it would be hard but not confusing and with Google as my friend I thought I could do it.  Wrong.  I'm trying to get fluxbox, ndiswrapper, and firefox on it.  I've been trying instructions that the Internet says yet I can't do a damned thing.  I haven't been able to get anything installed and I'm starting to get a bit irked.   Can anyone help me at least get these installed?

---

### Post by sami83 on 2005-12-09
[QUOTE=Protoman]Well I got my CD's today and tried installing with them.  5 CDs were failing just doing the normal install.  Since I didn't feel like trying the 5 more left, I just went ahead and did a mininum/server install.  Thought it would be hard but not confusing and with Google as my friend I thought I could do it.  Wrong.  I'm trying to get fluxbox, ndiswrapper, and firefox on it.  I've been trying instructions that the Internet says yet I can't do a damned thing.  I haven't been able to get anything installed and I'm starting to get a bit irked.   Can anyone help me at least get these installed?[/QUOTE]

Edit you're apt sources list:

```
sudo nano /etc/apt/sources.list
```

You need to uncomment the universe repos.

Then do:
```
sudo apt-get update
```

Then you will be able to install the packages you need with apt

---

### Post by aysiu on 2005-12-09
Log in and type this ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` Remove the # signs from the beginning of any line that looks like a web address. Then save (Control-X), confirm (y), and exit (Enter). ```
sudo apt-get update
sudo apt-get install fluxbox firefox ndiswrapper-utils ndisgtk ndiswrapper-source
```

---

