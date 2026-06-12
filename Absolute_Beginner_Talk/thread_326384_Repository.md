---
title: "Repository"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2006-12-27
:rolleyes: How do you enable a restricted repository in /etc/apt/sources.list?

(probably a stupid question to which I do not know the answer to!)

Thanks, Loyaleagle

---

### Post by taurus on 2006-12-27
By removing the # sign in front of all the lines with universe & multiverse at the end (with deb at the beginning)...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by loyaleagle on 2006-12-27
Thanks.....

---

