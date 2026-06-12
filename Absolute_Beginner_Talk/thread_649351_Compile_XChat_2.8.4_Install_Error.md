---
title: "Compile XChat 2.8.4 Install Error"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by nicholas1520 on 2007-12-24
Hi, I've been having some troubles compiling XChat 2.8.4 (yes I know it's in the repositories now) but I've wanting to compile for myself to gain some experience on how-to compile other software.

Command

```
make install
```

I get the following:

make[2]: Entering directory `/home/nicholas/Desktop/xchat-2.8.4/po'
rm -f be.gmo && : -c --statistics -o be.gmo be.po
mv: cannot stat `t-be.gmo': No such file or directory
make[2]: *** [be.gmo] Error 1
make[2]: Leaving directory `/home/nicholas/Desktop/xchat-2.8.4/po'
make[1]: *** [stamp-po] Error 2
make[1]: Leaving directory `/home/nicholas/Desktop/xchat-2.8.4/po'
make: *** [install-recursive] Error 1

It's almost similar when I also run:

```
make
```

make[3]: Entering directory `/home/nicholas/Desktop/xchat-2.8.4/po'
rm -f be.gmo && : -c --statistics -o be.gmo be.po
mv: cannot stat `t-be.gmo': No such file or directory
make[3]: *** [be.gmo] Error 1
make[3]: Leaving directory `/home/nicholas/Desktop/xchat-2.8.4/po'
make[2]: *** [stamp-po] Error 2
make[2]: Leaving directory `/home/nicholas/Desktop/xchat-2.8.4/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nicholas/Desktop/xchat-2.8.4'
make: *** [all] Error 2

I install build-essential and libglib2.0-dev to solve other problems when I ran the configure script. When I run the following commands above I get those errors. Am I doing something wrong?

---

### Post by srunni on 2007-12-25
Did you try ```
sudo apt-get build-dep xchat
``` That command will install all the packages that XChat is dependent on, which might help.

---

### Post by nicholas1520 on 2007-12-25
> **srunni said:**
> Did you try ```
sudo apt-get build-dep xchat
``` That command will install all the packages that XChat is dependent on, which might help.

It worked! Thanks I wouldn't even have guessed that I had to install other packages instead of libglib2.0-dev and build-essential.

Thanks,
Nicholas

---

### Post by srunni on 2007-12-25
Whenever you are compiling a program, you need to install additional packages that the package manager would've automatically installed for you. You also need some packages specific to compilation; these packages tend to end in '-dev'. Using ```
sudo apt-get build-dep <package>
``` will always work if the program you're trying to compile is also in the repositories.

---

