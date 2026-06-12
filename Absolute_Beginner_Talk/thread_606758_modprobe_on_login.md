---
title: "modprobe on login"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Dark Seraphim on 2007-11-08
I was wondering would gnome session be able to modprobe on login. like the way it launches gnome-power-management. i would really like it to work on login instead of boot.

---

### Post by kd7swh on 2007-11-12
you can write a shell script.

```
gedit modprobe.sh
```

type your modprobe commands -> save script

then make it executable:

```
sudo chmod +x modprobe.sh
```


then you can add it to the session startup in:

System -> Preferences -> Sessions -> Startup Programs

---

