---
title: "HELP!!!!!!!! Login Trouble"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Dark_Man on 2008-02-07
Hello. I am running Ubuntu 7.04. I installed the KDE and during the installation I was asked what display manager I would like to use, gdm kdm. I chose kdm and now I cannot get past the login screen. Is there a way that I can correct this without a reinstall? PleasePleasePleasePleasePleasePleasePleasePleasePlease!!!
Thanks

---

### Post by taurus on 2008-02-07
What happens when you try to log in with your username and password?  Is there an error message?

Press <Ctrl><Alt>F2 and log in.  Then, you can remove kdm and reinstall gdm again.

```
sudo apt-get update
sudo apt-get remove kdm
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

---

### Post by emarkd on 2008-02-07
Try giving a bit more information.  Like, what error message you're given, or what happens when you put in your password and hit enter.

If you want to go back to Gnome, you can click on <sessions> and select it from there before logging in.

---

### Post by jan quark on 2008-02-07
try to select during the login process a failsafe session 

did you install ubuntu and then the kubuntu desktop?

or do you installed kubuntu?

do not understand really sorry

---

### Post by Dark_Man on 2008-02-07
There is no error message. When I type in my user name and password and hit enter the screen goes black and the login in screen pops back up.

---

### Post by jan quark on 2008-02-07
try to select another session

---

### Post by Dark_Man on 2008-02-07
Ok. Tried choosing different session,failsafe, gnome. That didnt work. Tried ctrl alt f2 to login and a screen full of this.

-bash: /dev/null: Permission denied

Any other suggestions?:(

---

### Post by jan quark on 2008-02-07
can you boot into the text mode with the ubuntu cd and run

this
```

ls -l /dev/null
```

You should see this if everything is correctly
set:
crw-rw-rw- 1 root root 1, 3

If you get a different set of permissions like
this maybe:
-rw-r--r-- 1 root root 1, 3

then you should (as root) delete the /dev/null with:
rm /dev/null

and recreate it (as root) again with:
mknod -m 0666 /dev/null c 1 3

---

