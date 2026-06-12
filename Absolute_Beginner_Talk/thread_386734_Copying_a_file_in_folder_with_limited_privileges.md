---
title: "Copying a file in folder with limited privileges"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by xuser1 on 2007-03-17
Hello all,
I was trying to install the last rel. of Java JRE in a folder with root privileges (that I created via the console) on Xubuntu Edgy. Being a newbie I haven't been able to copy the .bin file I downloaded in a temp folder from Java site to the above folder in order to execute it from within and allow self-extraction: does anybody know what's the procedure for copying files to folders with root privileges ? (The procedure explained on [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)  didn't work because at point .4 the .bin file wasn't found in its originary location, so I suppose it must be put in the destination folder).
Thanks in advance.

---

### Post by taurus on 2007-03-17
When you want to move or copy something outside your $HOME directory, you need to use the sudo command.

```
sudo cp **filename** **destination**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

