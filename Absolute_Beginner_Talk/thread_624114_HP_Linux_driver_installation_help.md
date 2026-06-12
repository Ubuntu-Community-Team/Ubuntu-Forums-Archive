---
title: "HP Linux driver installation help"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-11-26
I have bought a hp deskjet f4180 and need a driver for it in order for it to work.  I am trying to download the hp driver for linux from this site, [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html).

i downloaded the setup file and etc.  
i typed in :sh hplip-2.7.10.run : into my terminal and the terminal says sh: Can't open hplip-2.7.10.run

any ideas to why this is happening and how i could fix this? thanks.

---

### Post by 11hjpphty76lkjj on 2007-11-26
```
sh hplip-2.7.10.run
```

Should work work, you may want to try deleting the .run and downloading it again. 

Also if you continue to have problems you can run

```
chmod 777 hplip-2.7.10.run
```

then 

```
sh hplip-2.7.10.run
```

But you shouldn't have to..

A

---

