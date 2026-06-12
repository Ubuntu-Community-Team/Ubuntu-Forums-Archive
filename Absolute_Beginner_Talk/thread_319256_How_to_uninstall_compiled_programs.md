---
title: "How to uninstall compiled programs?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by bibstha on 2006-12-15
I have a faint heart for compiling source codes and usually prefer precompiled binaries in packages. The reason is because i dont know how to uninstall them.

Now since i dont know how to uninstall, what if they mess up certain files in my pc and things become bad or something.

Recently i needed a pppoe client software, the default way for pppoe in (k)ubuntu is pon-poff but i didn't feel it very user friendly. After looking for a decent client program i found tk-pppoe in rp-pppoe*.tar.gz

I didn't find a .deb so i had to compiled it. After compiling i could connect to the Internet but no program would work, i couldn't even ping localhost, i got so frustrated i thought of reinstalling the whole OS.
After some time, i it occured to me to check the iptables and to my god fortune, i saw the problem was that my INPUT policy was defined as to DENY. And so the problem was fixed (after couple of days).

That was one scary moment and i always think twice before compiling anything from source. Is there anyway to do that?? If not doesn't ur pc get messy and messy after u install a lot of programs to just try out coz u dont have a way to remove them?

Regards
bibstha

---

### Post by Ben Sprinkle on 2006-12-15
1:
```

sudo aptitude

```
And search for it, 2:
```

sudo apt-get remove <program-name>

```

---

### Post by shirilover on 2006-12-15
If you have compiled and installed a program from source and have not deleted the source folder, you can uninstall the program by opening a termial:
```

cd path/to/program/sourcefolder
sudo make uninstall

```

---

### Post by igknighted on 2006-12-15
Instead of compiling the program directly, you can make it into a .deb package and run 'sudo dpkg -i packagename.deb' to install it.  This makes uninstalling much easier.  I forget the exact command to do this, but if you do a quick search it was discussed not to long ago.

---

### Post by zgornel on 2006-12-15
> **igknighted said:**
> Instead of compiling the program directly, you can make it into a .deb package and run 'sudo dpkg -i packagename.deb' to install it.  This makes uninstalling much easier.  I forget the exact command to do this, but if you do a quick search it was discussed not to long ago.
man checkinstall ;)
If there is no *make uninstall* rule, do ```
./configure --prefix=/path/myprogram 
```, then ```
make install
``` and see in /path/myprogram what the program installed. Then delete the files manually :D . This is also useful if you want to install the program into a certain directory (/opt is usually the one). Also, another method of controlling where installed programs will go is to edit the Makefile and search for INSTALL_DIR variable is no configure script exists. The disadvantage of installing in custom locations is that usually these locations are not found in the PATH variable (you have to manually write the actual path to the program). The most ellegant way of compiling&installing is with checkinstall.

---

