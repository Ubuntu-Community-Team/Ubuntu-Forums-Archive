---
title: "Installing Wine..."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Justin125 on 2007-06-23
I type "sudo apt-get install wine" and get:

"Package wine is not available, but is reffered to by another package."

There's more but that's the important part.

Help?

---

### Post by wormser on 2007-06-23
Have you opened up the other repositories?  System>  Administration>  Software Sources.

The other way is to do it manually.

```
sudo nano /etc/apt/sources.list
```

Remove the # in front of the universe and multiverse repositories.

---

### Post by Enverex on 2007-06-24
>>> [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
You'll want those repos anyway. Feisty is always horribly out of date.

---

### Post by dptxp on 2007-06-24
I think it exists in add/remove.

---

