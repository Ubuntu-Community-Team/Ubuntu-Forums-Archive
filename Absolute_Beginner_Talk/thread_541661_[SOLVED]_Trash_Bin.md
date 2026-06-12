---
title: "[SOLVED] Trash Bin"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-09-03
How can you empty your trash bin through the terminal out of curiosity? Can you even do it?

---

### Post by Lord Illidan on 2007-09-03
Sure you can:
Your trash in ~/.Trash

The ~ stands for your home directory when you are in a terminal.

So basically, all you have to do is :

```
cd ~/.Trash
rm -R *
```

Be careful with the last command, as the deletion is usually irreperable (unless you use some pretty advanced software - can be quite a hassle).

In KDE, the trash is located elsewhere, forgot where it is atm.

---

### Post by ingvildr on 2007-09-03
All the recycle bin is a folder so you could do something like this,

```
$ rm -rf $HOME/.Trash/*
```

---

### Post by CapitanYochua on 2007-09-03
thanks

---

### Post by Lord Illidan on 2007-09-03
And as I said before, please don't underestimate the rm command...many people have wiped out their systems with it.

---

### Post by laur on 2007-09-10
I'm able to add that in KDE (kubuntu 7.04) this is a little different. The ~/.Trash directory does not exists, but in ~/.local/share/Trash the trash can be found. 

I'm not sure if it is safe to delete the two directories files and info, but I believe that it is safe to delete the contents of the two directories.

Laur

---

