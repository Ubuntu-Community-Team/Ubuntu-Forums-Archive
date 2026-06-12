---
title: "Compiz broke my system!"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-02-10
I'm running Gusty, and I tried running a script that will patch Compiz and Nautilus so I can have different wallpapers on different sides of the cube.  Anyway, apparently the script was broken, and it broke Compiz.  Now when I run 'compiz --replace' in a terminal, it says that I need to run 'sudo apt-get install compiz-core'.  So I did, and it said that it was already installed.  Also, none of the windows I open have a menubar, and alt+F2 doesn't bring up the run dialog and I can't click the button I normally do to reboot, I have to switch to tty1.

So, does anyone have any ideas?  I'd really like to avoid reinstalling all together.

Thanks!

---

### Post by JoshuaRL on 2008-02-10
Try the following commands and see if they help.

```

sudo apt-get update
sudo apt-get upgrade

```
And then:
```

sudo apt-get -f install compiz-core

```
Or this if that doesn't work:
```

sudo apt-get install --reinstall compiz-core

```
And if you still have problems try:
```

sudo dpkg --configure -a

```
And then the same process as above.

---

### Post by Yes on 2008-02-10
Thanks, I reinstalled Compiz and now it's working.

---

### Post by JoshuaRL on 2008-02-10
Cool dude, and thanks for the thanks.  You might want to go into Thread Tools at the top and Mark As Solved.

---

