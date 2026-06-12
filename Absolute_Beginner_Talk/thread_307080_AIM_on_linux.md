---
title: "AIM on linux"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by misfitpierce on 2006-11-26
Ok im somewhat new to linux now. Surprisingly i've got it pretty much down installing stuff through konsole and all. Thing is though I cant get AIM to install whatsoever on my laptop. Everytime I try to alien the RPM or use the DEB it wont install right or run. Can someone please in words describe exactly how to install AIM if youve done so. 

 When I tried running it said something bout shared directory and cannot run. So please help its the only app giving me headaches!

---

### Post by kelbizzle on 2006-11-26
I don't know what you have against Gaim. But if you think linux owns windows. Then you should at least try it out if you havn't. I hate the new aim and I'm all about plugins. 

Try:
```
sudo apt-get install gaim
```

---

### Post by sardion on 2006-11-26
I would strongly suggest you try gaim as mentioned above.
Gaim is in my opinion a much better option and is certainly much more in the spirit of ubuntu than using aim.  But of course, it's all about choice.

That said, while it has been a while since I did so, following the instructions on AOL's website worked for me.

[http://www.aim.com/get_aim/linux/latest_linux.adp#install](http://www.aim.com/get_aim/linux/latest_linux.adp#install)

If you tried these and something went wrong in the terminal (konsole), post the error message(s) and we will help you through this.

---

### Post by misfitpierce on 2006-11-26
/usr/local/bin/aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory


Thats the error I recieve after I installed and tried to run like AIM website says!

---

### Post by misfitpierce on 2006-11-26
I read that newer versions of Debian dont carry that libstdc and the aim site says this...

When you run AIM, it looks for the library libstdc++-lib6.1-1.so.2. However, the latest Debian version doesn't come with this file by default, it comes with a newer version. You need to softlinking the new file to the old filename though: ln -s /usr/lib/libstdc++-libc6.1-2.so.3 /usr/lib/libstdc++-libc6.1-1.so.2

I dont understand what it means... Someone help

---

### Post by redDEADresolve on 2006-11-26
yeah you need to have those dependencies, but look into Gaim it does everything AIM does but made for Linux. The newest version also supports file transfers between the two.

---

### Post by misfitpierce on 2006-11-26
eh, I tried GAIM and ended up hating it. I like this look of AIM for linux but thats me... guess ill stick to Kopete... Thanks anyways.

---

### Post by junglepeanut on 2006-11-26
In your post your wrote exactly what you need to do.

```
ln -s /usr/lib/libstdc++-libc6.1-2.so.3 /usr/lib/libstdc++-libc6.1-1.so.2
```

You do still need to have version 3 though.

---

