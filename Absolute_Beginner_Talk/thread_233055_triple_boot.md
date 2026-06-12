---
title: "triple boot?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by That Guy X on 2006-08-09
Hi , im about to install mepis so i can have a kde and a gnome desktop. Will the mepis GRUB detect ubuntu automaticly or do i have to download a special loader :confused:

---

### Post by linuksamiko on 2006-08-09
I'm not 100% sure aboute mepis but your ubuntu should be detected automatic. You can add as much Systems to your grub as you like. I used to have a triple boot with SuSE, Ubuntu and Windows (and was thinking about having even more system but I didn't had the time for taking care of one more system)

But why do you want to install a whole new system just to have another Windowmanager? Why don't you install KDE or kubuntu into your existing ubuntu installation. When ever you are prompted for your user name and your password you can choose if you like to start KDE or Gnome (or any other Desktop you like to install)

---

### Post by meng on 2006-08-09
Do you know that you can install a KDE desktop in Ubuntu, and choose between GNOME and KDE shortly after boot? If you're really keen on installing MEPIS though, then by all means create another partition and go ahead, but you'd probably be best to manually configure the existing GRUB rather than overwrite/replace with another.

---

### Post by davebgimp on 2006-08-09
**sudo apt-get install kubuntu-desktop**

---

### Post by Jagot on 2006-08-09
> **davebgimp said:**
> **sudo apt-get install kubuntu-desktop**

But use aptitude, not apt-get.  Read this to see why:

[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by cjm5229 on 2006-08-09
The Mepis grub will not recognize another linux OS when it installs. You can edit grub to make it work though. Just copy the Ubuntu Info into the Mepis grub menu. It should look something like this. 

> Other Operating Systems

title        Ubuntu, kernel 2.6.15-26-k7
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-k7
savedefault
boot

---

### Post by That Guy X on 2006-08-09
How do you get to the GRUB menu?

---

### Post by Jagot on 2006-08-09
GRUB loads when you boot.  If you mean how to you edit it . . .

```
sudo gedit /boot/grub/menu.list
```

---

