---
title: "ubuntu frequently freezes"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by djowtlawz on 2008-03-24
Im not sure why, but my ubuntu frequently freezes. I have thought of a few possible reasons why, however I saw an earlier post of a similar type about the swap not being used and that is not it.

Possible reasons:
 
1. my graphics card's drivers aren't functioning properly?
2. I am using the wrong architecture? I am using i386 with an AMD x86_64 build
3. another reason I am not aware of? I would like to try another means to solve this before I reformat and install an x86_64 architecture if that is the problem.

Thank you in advance.

---

### Post by djowtlawz on 2008-03-24
update, well I found out I actually have no video card drivers...and found a set for Linux. However it says that an X server is running. What do I do?:(

---

### Post by cotcot on 2008-03-24
i386 should work fine. 
I had some freezes with an nvida graphics card. After installing an older nvidia driver (96.43) it was solved.
You can check the graphics card type with this command :
```
lspci
```

You can reconfigure xorg with :
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by djowtlawz on 2008-03-24
Thanks for the help however I get this
```

root@Pons:/home/P/Desktop# sudo -dpkg-reconfigure xserver-xorg
sudo: please use single character options
sudo: illegal option `-dpkg-reconfigure'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
```

---

### Post by cotcot on 2008-03-25
Sorry I made a typo error. I have corrected it in my first post.

---

### Post by uberlube on 2008-03-25
Grab ENVY and use it to install your drivers.

---

