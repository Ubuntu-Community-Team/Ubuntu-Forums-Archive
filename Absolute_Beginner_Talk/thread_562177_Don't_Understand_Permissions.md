---
title: "Don't Understand Permissions"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by TonkaTruck18 on 2007-09-28
Hi I am a newb on Ubuntu and I have not been able to get espsxe to work and have given up and am now trying to remove the folder. The folder is located in my USR file and whenever i try to delete it I can't because it says that I don't have permissions and I don't know how to delete it in terminal, if anyone could help it would be greatly appreciated!!

---

### Post by Perfect Storm on 2007-09-28
```
cd <distination>
sudo rm -rf <file>
```

Just be careful when using rm command if you do it wrongly, you can break your system badly.

---

### Post by TonkaTruck18 on 2007-09-28
hey thanks for the help but I still can't delete it because it says no such file or directory, is there a way I could get rid of permissions so i can just delete it through the GUI?

---

### Post by Marc Hoffman on 2007-09-28
you can run 

sudo nautilus 

this will allow you to have root permissions while browsing- again be careful and close when you have finished.

---

### Post by TonkaTruck18 on 2007-09-28
ah awesome thanks so much exactly what i needed!!

---

### Post by Perfect Storm on 2007-09-28
> **TonkaTruck18 said:**
> hey thanks for the help but I still can't delete it because it says no such file or directory, is there a way I could get rid of permissions so i can just delete it through the GUI?

You don't want to mess with the permission system (only if you absolutly know what you're doing, even that it still not recommendable to mess with it). It keeps your system secure and prevent you to do "stupid" things to kill the system.

---

### Post by TonkaTruck18 on 2007-09-28
alright i def wont mess with them thanks again for the help:)

---

