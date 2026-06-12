---
title: "Compile + Install with koverartist"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by ZERO_SHIFT on 2006-10-02
I seem to always have problems while trying to install software on my desktop with ubuntu.

Problem with installing Koverartist:-

I tried to compile by: ./configure
every thing went well untill the end when it gave this---->checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths! 

then:

zaidammar@ubuntu:~/koverartist$ make
make: *** No targets specified and no makefile found.  Stop.
zaidammar@ubuntu:~/koverartist$ sudo make
Password:
make: *** No targets specified and no makefile found.  Stop.
zaidammar@ubuntu:~/koverartist$ sudo make install
make: *** No rule to make target `install'.  Stop.

what should I do??:-k  should I use the RPM file?:-k 

Thanks in Advance (tia)

---

### Post by pay on 2006-10-02
I think that it wants the development files for X. Try ```
sudo aptitude install xserver-xorg-dev
```

---

