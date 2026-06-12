---
title: "[SOLVED] Adding gnome to server distro"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by iamstretchypanda on 2007-01-14
I recently installed ubuntu 6.10 server-i386.  Is there an easy way to adding gnome (or some sort of gui), or should i just reinstall with the desktop version?

Thanks

---

### Post by jclmusic on 2007-01-14
to install gnome, open a terminal window, type this...

```

sudo apt-get ubuntu-desktop

```

press enter and go and make a cup of tea :D

---

### Post by iamstretchypanda on 2007-01-14
Is the terminal window the main console, or do i need to open a new window?

If so, how do i open a terminal?

If else, the error message i recieved after typing the aformentioned code = Invalid operation ubuntu-desktop.

Thank you

EDIT

I did a little more research, and i think the desktop version might actually be a little bit better for me int he long run.  Thanks for the help, i'm sure i'll be back soon :p

---

### Post by jclmusic on 2007-01-14
yes i mean the main console. 

sorry, that's me being too used to the desktop version :p

---

### Post by bodhi.zazen on 2007-01-14
Small typo 

Should be:

```
sudo aptitude **install** ubuntu-desktop
```

I use aptitude rather then apt-get.

If you prefer:```
sudo apt-get **install** ubuntu-desktop
```

---

