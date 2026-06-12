---
title: "Question about navigating the terminal"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by flehnerz on 2007-12-21
Question:
How come I can navigate to the correct folder(ex: alsa-utils_1.0.15) by doing this
```

root@frank-laptop:cd /usr/src/alsa/alsa-utils*

```

but not this

```

root@frank-laptop:/usr/src/alsa# cd /alsa/alsa-utils*
bash: cd: /alsa/alsa-utils*: No such file or directory

```

or this

```
root@frank-laptop:/usr/src/alsa# cd /alsa-utils-1.0.15
bash: cd: /alsa-utils-1.0.15: No such file or directory
```

This is really pissing me off why the latter two wouldn't and never work. I am using Ubuntu 7.10 with what I believe is the latest kernel.

---

### Post by taurus on 2007-12-21
```
cd alsa-utils-1.0.15
```
or
```
cd /usr/src/alsa/alsa-utils_1.0.15
```
Not sure why you are pissed because the shell did what you told it to to.  You wanted to move to the / directory and then to alsa-utils_1.0.15 but there was no such directory because you have the extra / in front of the name!

---

### Post by flehnerz on 2007-12-21
Something ridiculously simple...haha
THANK YOU SO MUCH

---

### Post by blueridgedog on 2007-12-21
In your second example:

```
root@frank-laptop:/usr/src/alsa# cd /alsa/alsa-utils*
bash: cd: /alsa/alsa-utils*: No such file or directory
```

You are starting your cd argument at the root, with /, but you are not giving it a root path.  You type cd /alsa/alsa-utils*, but it should cd /usr/src/alsa/alsa-utils* if using a root path or simply cd ./alsa-utils* if using the local directory (dot slash).

---

