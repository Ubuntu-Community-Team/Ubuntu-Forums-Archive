---
title: "How do you shut-down the computer?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Linux4HumanBeings on 2006-08-22
There is no shut-down button, on the top right corner the only options are switch user log off and hibernate. Is there a way to shut of the computer not manually?

---

### Post by Jagot on 2006-08-22
From Terminal:

```
sudo shutdown -h now
```

---

### Post by bodhi.zazen on 2006-08-22
To reboot:

```
sudo shutdown -r now
```

or 

```
sudo reboot
```

---

### Post by TFX360 on 2006-08-22
Dear Linux4HumanBeings,


There should be one, at least you could add it by right clicking the taskbar and add to panel.

You can also use 

For shutdown:
```

sudo init 0
```

For reboot:

```
sudo init 6
```


Kind regards,


TFX

---

### Post by LeighT on 2006-08-22
Click on System and select quit a dialoge box should appear giving you a choice of log out, lock screen, switch user, Hibernate, reboot or shutdown.
If the shutdown or reboot options are not there you can use the above command lines or just control-alt-delete to reboot and control-alt-backspace to restart Xserver.
It is better to use the command line if the shutdown GUI is not present.

---

