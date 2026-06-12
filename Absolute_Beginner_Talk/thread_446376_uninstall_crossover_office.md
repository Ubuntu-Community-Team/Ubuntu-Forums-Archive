---
title: "uninstall crossover office"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-05-16
I installed crossover office and it seems to have some problems. It won't update the menu and throws errors sometimes. I have the latest version and would like to install it, but if I try to go over the current one, it says that it is not compatible with the current version. I figured that the best way would be to uninstall the current one and redo with the latest, but when I try the uninstall link, it just says that the uninstall failed and quits. Is there another way I can get rid of the current installation safely so that I can try again with the latest and see if it works better? I don't have any data to worry about, just want to completely get rid of the current install and try again.

Thanks for any help you can give. So far, this forum is batting 1000 on the issues that I have had. I don't miss windows much at all. I would like to get MS office running just because I have some files that need compatibility.

I finally got it to reinstall and got it working. My preference would be not to have any MS at all, but, unfortunately, I need Excel for a couple of things.

---

### Post by taurus on 2007-05-16
How did you install the old version of CrossOver?  If you installed it as a .deb, then you can uninstall it with dpkg.

```
sudo dpkg -r filename
```

---

### Post by dondad on 2007-05-16
I used the shell script that was listed as a universal installer on the codeweavers website. That was probably my mistake, but I don't know how to kill it. If I can get rid of the current, I have the deb file to reinstall.

---

### Post by taurus on 2007-05-17
May have to remove it by hand if there is no uninstall script to go with it.

```
locate crossover
```

---

### Post by dondad on 2007-05-17
Thanks. How would I go about doing that? I used the command and it found a lot of stuff, but I am not sure what to do with the output, or how do do a manual uninstall.

---

