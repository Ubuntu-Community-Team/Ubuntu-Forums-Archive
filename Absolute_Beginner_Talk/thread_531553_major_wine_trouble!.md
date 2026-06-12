---
title: "major wine trouble!"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-08-21
Recently i tried to install a game on my computer using wine. it installed it wrong so i was told to purge the computer of wine. now when i try to download and install it on my dial-up modem, it does it in around 3 seconds. the file size for wine is around 10 MB so it can't possibly download that fast. How can i fix this issue?

---

### Post by toidi on 2007-08-21
Have you tried using the uninstaller that lets you remove windows programs that wine installed?

```
uninstaller
```

Run it in a terminal and it will let you uninstall software that has been installed with WINE.

I would try that before purging wine from your install, as it may just be an install issue.

If that fails and you want to completely remove wine then do the following command in terminal.

```
sudo apt-get remove wine --purge
```

Hope this helps..

---

### Post by axemurder785 on 2007-08-21
no it still says it downloaded and installs without downloading anything! is there another way to install it?

---

### Post by _duncan_ on 2007-08-21
the first time you installed wine, the package manager cached the downloaded files into your hard drive. For subsequent reinstallation, it's possible the package manager detected these cached files and used them nstead of downloading. That's why it's a lot faster.

---

### Post by Qrk on 2007-08-21
You may also want to delete the .wine folder in your home directory, if you haven't already.

---

