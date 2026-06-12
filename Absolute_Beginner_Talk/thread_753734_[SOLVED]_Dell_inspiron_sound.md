---
title: "[SOLVED] Dell inspiron sound??"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-04-13
Hello all
Looks like I have been posting sound problems for different models (all those I converted from Vista to Gutsy!!). I got all resolved except for 2, and one of them being a Dell Inspiron 1520 (specs: Core2 Duo T7500, 2GB RAM, nVidia 8600 M GT, 250GB HDD). It says that "No Audio device found" when I click on the Volume control icon. ALSA and OSS don't seem to work. Any ideas? :D

---

### Post by ibutho on 2008-04-13
Can you post back the output of 
```
sudo lspci | egrep -i "audio | multimedia"
```

---

### Post by sayakb on 2008-04-13
Thank you for replying. But I seem to have solved it. I installed &quot;linux-restricted-modules&quot; thru apt and got it working.:)

 EDIT: Sorry, I actually installed "linux-backports-modules".. that worked for me.

---

