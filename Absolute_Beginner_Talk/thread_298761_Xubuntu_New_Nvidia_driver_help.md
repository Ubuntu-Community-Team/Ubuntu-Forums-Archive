---
title: "Xubuntu New Nvidia driver help"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by tjotser on 2006-11-13
Hi, i'm on **Xubuntu** edgy, and i have a problem with the new nvidia drivers..
NVIDIA-Linux-x86-1.0-9629-pkg1.run

so i pushed ctrl-alt-F1 and logged in the terminal
started the Nvidia installer with "sudo sh NV<tab><tab<" and away it goes
Then i get the error saying that there is still an X-server running.

So how do i stop that x server to install the newest drivers ?? thanks:-k

---

### Post by joshsherman on 2006-11-13
You need to stop your login manager... under Ubuntu it's gdm, so you run:

sudo /etc/init.d/gdm stop

Then when you're done, you run:

sudo /etc/init.d/gdm start

Not sure what gui login manager Xubuntu uses, so update the process accordingly.

-j

---

### Post by pdub on 2006-11-13
You can stop X like this:

```
sudo /etc/init.d/gdm stop 
```

---

### Post by tjotser on 2006-11-13
i thank you both.. after some stumbling with the already installed drivers and such , i was greeted with a fancy new splashscreen from nvidia, i'm off to see if there's any improvent in Unreal 99... THANK YOU !!!:D

---

