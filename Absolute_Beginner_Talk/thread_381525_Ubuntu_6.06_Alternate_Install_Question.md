---
title: "Ubuntu 6.06 Alternate Install Question"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Chris_F on 2007-03-11
I just installed Ubuntu 6.06 alternate on a P3 HP laptop. First I cannot login using my username pw, but can logon using OEM, and my password. So now im in a dos type text based area, and I have no idea what to do from here, any help would be great. Thanks

---

### Post by taurus on 2007-03-11
You need to run this command to create an actual account for you to use from now on.

```
sudo oem-config-prepare
```

---

### Post by Chris_F on 2007-03-11
Then what?

---

### Post by taurus on 2007-03-11
:confused: 

Not sure exactly what you mean!  Then reboot and log in with your new username and password.

---

### Post by Chris_F on 2007-03-11
How do I get to the GUI?

---

### Post by taurus on 2007-03-11
Did you reboot and log in with your new username?  What is the error message when you run this command at the prompt?

```
startx
```
If you get something like "command not found", then you need to install Gnome on your machine.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by Chris_F on 2007-03-11
Where do I get gnome? Their website does not have a direct download link. If there is a guide that will go through all of this, id be more than happy to use it. 

Thanks

---

### Post by partsdale on 2007-03-11
Chris, I believe the lines of code in the post #6 are the commands to get gnome.

---

### Post by Ocxic on 2007-03-11
a tip fpr next install dopn't use OEM mode

---

