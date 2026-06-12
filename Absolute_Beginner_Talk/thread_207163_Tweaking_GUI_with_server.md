---
title: "Tweaking GUI with server"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by uwfrog on 2006-07-01
Since as everyone said, running GUI on the server is resource consuming and not necessary, I would like to have a server with GUI installed but not automatically started on boot. I am not quite familiar with how to configure linux(start/stop a service). Could someone help me out, or better, some general tips how to deal with the services? Thanks!!!

---

### Post by sYs^ on 2006-07-01
I didn't try it, but I hope it'll help:

[https://help.ubuntu.com/community/BootServices](https://help.ubuntu.com/community/BootServices)

---

### Post by aysiu on 2006-07-01
You can easily have a GUI that doesn't autostart: ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm icewm menu
startx
```

---

### Post by uwfrog on 2006-07-01
Thanks for the reply. I will try it and post what i get.

---

