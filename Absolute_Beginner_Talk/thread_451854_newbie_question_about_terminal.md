---
title: "newbie question about terminal"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by xtang on 2007-05-22
whenever you type in one word into the terminal like 'firefox', which folder does the system look at for the executable?

---

### Post by yey365 on 2007-05-22
either /bin or /usr/bin I think.

Jim

---

### Post by Nekiruhs on 2007-05-22
Its /usr/bin. Just make a symbolic link (like a shortcut in windows, only better) from the exe to the /usr/bin, and the command will be the name of the symbolic link.

---

### Post by ruy_lopez on 2007-05-22
If you type this command it will show you all the places it looks for executables:

```
echo $PATH
```

And if the executable isn't in one of those places, you can add the place to the .bash_profile file in your home folder, by adding this:

```
export PATH=$PATH:</path/to/search>
```

where </path/to/search> is the folder of the executable you want to run.

---

### Post by init1 on 2007-05-22
I think "firefox" was linked to "firefox-bin". Whenever I need to kill firefox, "firefox-bin" shows up in ps -A. 
The reason why it loads is because it is in you path. Your path usually includes /bin (basic commands), /usr/bin (almost everything else), /usr/games (games, of course), and maybe a few others. You can add other folders to your path if you need to

---

