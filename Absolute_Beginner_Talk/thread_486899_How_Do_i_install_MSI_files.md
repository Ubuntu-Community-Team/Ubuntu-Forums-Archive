---
title: "How Do i install MSI files"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by TehCJ on 2007-06-28
How do i Install MSI Files?
  


Because i need to RUn SteamInstaller.msi

---

### Post by speaker219 on 2007-06-28
MSI's are windows installer files, not for ubuntu, but if you have wine, you can cd to the directory the msi is in, and then run
```
sudo wine SteamInstaller.msi
```
Edit, the above code might not work, see the below link
[http://ubuntuforums.org/showthread.php?t=483222](http://ubuntuforums.org/showthread.php?t=483222)

---

### Post by Rocket2DMn on 2007-06-28
Wine is working on including built in support for msi files, but I'm not sure if it's complete yet.
I think the command is something like
```
wine msiexec /i SteamInstall.msi
```

---

