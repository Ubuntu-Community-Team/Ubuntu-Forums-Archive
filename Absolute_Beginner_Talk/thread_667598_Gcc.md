---
title: "Gcc?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by jablair on 2008-01-14
I just stalled Ubuntu on my laptop. I was fooling around with some C code and made a simple Hello World program. After running gcc on my .c file, the a.out executable was created. However, when i run a.out, it says no command found. Any ideas?

---

### Post by SOULRiDER on 2008-01-14
To run it do
```
./a.out
```
you need the ./ to tell the terminal its in the working directory and not in /bin (if you just do a.out it looks for it in /bin)

Also, you might need to chmod it, if you get a permision error type this
```
chmod +x a.out
```

---

### Post by bodhi.zazen on 2008-01-14
yea, it is not on the default ubuntu install.

Try this :```
sudo apt-get install build-essential
```

---

