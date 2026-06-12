---
title: "help please!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by kfir on 2007-12-06
> kfir@kfir-laptop:~/3ddesktop-0.2.9$ make
make  all-am
make[1]: Entering directory `/home/kfir/3ddesktop-0.2.9'
g++ -Wall -O3 -DQT_CLEAN_NAMESPACE -DSHAREDIR=\"/usr/local/share/3ddesktop\" -DSYSCONFDIR=\"/usr/local/etc\"   -g -O2    -o 3ddeskd -L/usr/lib -lImlib2 -lfreetype -lz -L/usr/X11R6/lib -lX11 -lXext -ldl -lm  -lSM -lICE -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi  -lm  3ddeskd.o xutil.o arrange.o util.o win.o camera.o config.o  -lm -lXxf86vm -lXext   -lSM -lICE -lSM -lICE 
/usr/bin/ld: cannot find -lXmu
collect2: ld returned 1 exit status
make[1]: *** [3ddeskd] Error 1
make[1]: Leaving directory `/home/kfir/3ddesktop-0.2.9'
make: *** [all] Error 2

what is this -lxmu and i can i get him??

thanx

---

### Post by shadow-of-sin on 2007-12-06
lXmu is libxmu, you can install it by typing this in the terminal:
```
sudo apt-get install libxmu-dev
```

---

### Post by kfir on 2007-12-06
thanks alot!!!

---

