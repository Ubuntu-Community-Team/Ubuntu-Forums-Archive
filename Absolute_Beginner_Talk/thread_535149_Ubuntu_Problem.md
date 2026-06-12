---
title: "Ubuntu Problem"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by hamishnz on 2007-08-26
Ubuntu is great - I will NEVER go back to Windows.
One problem I have been having is when I try to install something,
thought the 'Add/Remove' progams or terminal (I was trying to install "beryl")
It comes up with "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." Help Please

Sould I just reinstall Ubuntu ?

Thanks

---

### Post by Dark Star on 2007-08-26
Type this ```
sudo dpkg --configure -a
```

Then do this for update 

```
sudo apt-get install -f
```

---

### Post by swoll1980 on 2007-08-26
make yourself some popcorn cause it takes awile

---

### Post by Dark Star on 2007-08-26
> **bloor75 said:**
> make yourself some popcorn cause it takes awile
WTH ? :? Btw you need not to re-install Ubuntu for that small error :p

---

### Post by Malta paul on 2007-08-26
Hi
You can use: Applications >Terminal and type in 'sudo dpkg --configure -a' this should work'
If 'add and remove' doesn't work, try System >Administration >Synaptic Package Manager >Search.
Just a note: beryl may be a bit unstable for the rest of your system your system
Have fun:)

---

### Post by Dark Star on 2007-08-26
Better install CF .. Its better and more stable than Beryl [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

