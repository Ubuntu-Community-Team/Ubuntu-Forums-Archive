---
title: "Problem with permissions"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by gingerrich on 2007-06-29
I am trying to edit the grub file menu.lst to remove the splash screen but everytime I try it says that I do not have permission. 
I have tried to log in as Root and Ubuntu will not let me. The folder and files for grub say that the owner is Root and I am now completely lost as to how I can do something as theoretically simple as edit a lst file.

Please help before I revert to a bog standard version of Linux and relearn the hard way.

---

### Post by S29K on 2007-06-29
Ubuntu does not allow you to log in as root but instead allows you to execute a command as root using sudo.

```
sudo gedit /boot/grub/menu.lst 
```

Password is your user password.  This should work for you.

---

### Post by Tsen on 2007-06-29
Go to a command prompt and type
```
sudo gedit /boot/grub/menu.lst
```
Ubuntu doesn't use a root account, instead it uses sudo.  Whenever you need root access, just add "sudo" to the front of your command.

EDIT: S29K beat me to it. :P

---

### Post by skrimpy on 2007-06-29
you should type in

```
 sudo gedit menu.lst 
```

if you're running gnome.  sudo whatever KDE's text editing program is if you're using KDE.

sudo = super user do, and it will prompt you for your user password.  Then you can edit menu.lst with root user privileges ^.^  Root is not assigned by default in Ubuntu.

Does that help?

---

### Post by gingerrich on 2007-06-29
Thanks!
Was getting confused as the last time I used any Linux was back in 2000 and was SUSE 6 or something.

---

### Post by bodhi.zazen on 2007-06-29
for graphical programs (gedit) your should user gksudo rather then sudo

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by davidjmayo on 2007-06-30
just in case anyone needs to know in Kubuntu or KDE use

```
kdesu kate <filename>
```


(kate is the default text editor)

 you can  use kdesu for konqueror etc ```
kdesu konqueror
```

---

### Post by Tsen on 2007-06-30
You don't need to use gksudo for gedit.

EDIT:
Okay, read that link, I understand where you're coming from now.  In this case, I don't think it will cause any problems (it never has for me), but I never knew it could cause issues to use sudo instead of gksudo before...

---

### Post by bodhi.zazen on 2007-06-30
> **Tsen said:**
> You don't need to use gksudo for gedit.

EDIT:
Okay, read that link, I understand where you're coming from now.  In this case, I don't think it will cause any problems (it never has for me), but I never knew it could cause issues to use sudo instead of gksudo before...

LOL

---

