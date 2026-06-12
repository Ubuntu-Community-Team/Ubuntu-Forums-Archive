---
title: "gui on server"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by alexroot on 2006-12-15
Hi,
I installed the server distribution and i am really missing a gui given the fact that i'm pretty new to this. I read on these forums that it's fairly easy to install a gui once you have installed ubuntu server. Can anyone point out how to do this? Thanks in advance,
Alex

---

### Post by Famicommie on 2006-12-15
```
sudo apt-get install ubuntu-desktop
```

---

### Post by alexroot on 2006-12-15
great, thanks

---

### Post by hyper_ch on 2006-12-15
Or if you prefer KDE:

```

sudo aptitude install kubuntu-desktop

```

or if you prefer Xfce:

```

sudo aptitude install xubuntu-desktop

```

I read several times that for install the desktop it's better to use aptitude instead of apt-get... so you may alter the code give by Fammicommie to:

```

sudo aptitude install ubuntu-desktop

```

---

