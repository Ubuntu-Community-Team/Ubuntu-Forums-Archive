---
title: "Upgrade edgy."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2007-05-15
So now that I have to reinstall Ubuntu, I'm stuck using my old 6.06 cd (too lazy). So when I open Software Updates it doesn't have the button to upgrade to 6.10 (then when that's done I need to upgrade again... to feisty). So how do I get the magical button to appear?

---

### Post by newlinux on 2007-05-15
One way:

Edit your /etc/apt/sources.list as root. Change every occurrence of dapper to edgy.Use any prefered editor. If you have a CD-ROM line in your file, then remove it.

```
sudo nano /etc/apt/sources.list
```

Now you need to update the source list using the following command
```

sudo apt-get update
```

Upgrade using the following command
```

sudo apt-get dist-upgrade

```
Double check your process was finished properly using the following commd
```

sudo apt-get -f install

sudo dpkg --configure -a

```
Now you need to Reboot your machine to take your new ubuntu 6.10 installation to effect all changes.

---

