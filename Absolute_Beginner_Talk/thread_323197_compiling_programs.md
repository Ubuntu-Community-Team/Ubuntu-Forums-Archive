---
title: "compiling programs"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by flash2lightning on 2006-12-21
when i use checkinstall to compile from source, (or any other method), it says

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

what do i need to do?

---

### Post by maddog39 on 2006-12-21
You need to run ./configure from the applications source folder first.

---

### Post by aysiu on 2006-12-21
What's the package you're trying to install? Is it not available through the repositories?

---

### Post by Sef on 2006-12-21
Have you installed build-essential?  If not, open the terminal, and type this:

```
sudo aptitude update
```

```
sudo aptitude install build-essential
```

You will need the disk that you installed Ubuntu with (whatever flavor of Ubuntu you used.)

---

