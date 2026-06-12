---
title: "can't update to 6.10?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-02-28
So I was looking in my update manager and I saw 6.10 upgrade avialable.

I decided to update my system first, which went fine. but then after that it no loger showed an upgrade available...

I restarted my system (still clearly only version 6.06) and went back to the updage manager again.

still... no 6.10 ugrade being shown.

I refreshed it, made sure interenet is work ect.

I've had a 6.06 Xubuntu update to a Xubuntu 6.10 on this comp before. so i know it is possible.

Is there a simple comman I could do in the terminal to tell it to upgrade to 6.10?

Thanks

---

### Post by talsemgeest on 2008-02-28
Yes there is. First type: ```
sudo apt-get update
```
Then:```
sudo apt-get upgrade
```

The first is to update your sources, the second should upgrade to whatevers available.

Hope this helps :)

---

### Post by Xarok on 2008-02-28
oh wow I was shure that was gonna work... but I guess not...
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by oedha on 2008-02-28
have you check your repository ?

---

### Post by jan quark on 2008-02-28
please post the output from

```
cat /etc/apt/sources.list
```

---

### Post by Xarok on 2008-02-28
Ah this code I found works
```

sudo aptitude update
sudo aptitude dist-upgrade

```

dumb thing

---

