---
title: "trouble installing plasmoids (kde 4.0.4)"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by jbrown96 on 2008-03-06
I decided to switch to KDE4 now that 4.0.2 has com out, but I'm having a very difficult time with plasmoids. I can't figure out how to install them. I assumed it would be a pretty easy untar, cd, make, make install; however, that doesn't work either. 

I saw this guide, but it doesn't work either, and I have no idea what the cmake command is supposed to do.
```
How to install a Plasmoid

 
tar -xvf plasmoid.tar.gz 
cd plasmoid 
mkdir build 
cd build 
cmake -DCMAKE_INSTALL_PREFIX=/usr/lib/kde4/ 
make 
sudo make install OR su -c "make install" 
Have fun! :-)
```

Could someone help me find a way to install them.?
Also has anyone seen a konsole plasmoid? I would really like to have a terminal embbed in my desktop.

Thanks for the help.

---

