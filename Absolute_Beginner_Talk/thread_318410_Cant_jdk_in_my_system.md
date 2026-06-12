---
title: "Cant jdk in my system"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by tin2 on 2006-12-13
Somehow multiuniverse repositeries arent being opened by adept.
I downloaded all these

 sun-java5-bin.deb
 sun-java5-jre.deb
 sun-java5-jdk .deb

What should install frist?
or did i miss something?

---

### Post by faraazs on 2006-12-14
If you already have them downloaded, then you can simply run this command to install them:```
sudo dpkg -i sun-java5-bin.deb sun-java5-jre.deb sun-java5-jdk.deb
```Make sure your terminal session is in the folder where those files are before running that command. Hope that helps.

---

