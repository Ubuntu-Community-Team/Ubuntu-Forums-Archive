---
title: "You do not have permissions to write to this folder."
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2007-10-22
I just reinstalled Fiesty on my laptop. But when I try to copy my backup files from my dvd by coping and pasting I get You do not have permissions to write to this folder. And I am only coping this all to my desktop??

---

### Post by cfaulkner on 2007-10-22
try doing it in console
and


sudo it

---

### Post by Malice007 on 2007-10-22
I cant even download anything from get deb it will not let me save anything

---

### Post by shad0w_walker on 2007-10-22
It sounds like you have somehow ended up with your home folder set to root ownership. Try running this command and post the output.

```
ls -l
```

---

### Post by cfaulkner on 2007-10-22
drop into console

type:

sudo su -

and

chown -R username:username /home/username

substitute yer username for above.. :)

---

### Post by Malice007 on 2007-10-22
malice@malice-laptop:~$ ls -l
total 4
drwxr-xr-x 2 root   root   4096 2007-10-21 20:34 Desktop
lrwxrwxrwx 1 malice malice   26 2007-10-21 20:34 Examples -> /usr/share/example-content
malice@malice-laptop:~$

---

### Post by cfaulkner on 2007-10-22
yup


sudo chown -R malice:malice /home/malice

---

### Post by shad0w_walker on 2007-10-22
You managed to end up with the desktop folder as root. Run this and it should fix it up

```
sudo chown -R malice:malice ~/Desktop
```

---

### Post by Malice007 on 2007-10-22
drop into console

type:

sudo su -

and

chown -R username:username /home/username

substitute yer username for above.. 





That fixed it... but how the heck did that happen?

---

### Post by cfaulkner on 2007-10-22
<shrug>  Gremlin perhaps?  Is gizmo running around there?  Did you feed it after midnight?  Did you put water on it?  lol

good deal

---

### Post by sageb1 on 2007-10-22
you might have installed as su from the /home folder?

---

