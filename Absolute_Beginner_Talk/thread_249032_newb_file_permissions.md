---
title: "newb file permissions"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by jim_ryan on 2006-09-02
/home/jim_ryan/xpad360   is locked.

I'm trying to download files into that folder but cant because it is locked. 

I ran gksudo nautilus but could navigate to /home/jim_ryan/xpad360 because I am a newb and cant find jim_ryan/xpad360 while im using gksudo nautilus.

How do you copy files into a folder that is in your home directory but locked?  or rather, how do you unlock a folder in your home directory?

cheers,

jim_ryan

---

### Post by bodhi.zazen on 2006-09-02
If you want this to be "personal" (user only):
in a terminal:
```
chmod 700 /home/jim_ryan/xpad360
```

User + group
```
chmod 770 /home/jim_ryan/xpad360
```

World (everyone)
```
chmod 777 /home/jim_ryan/xpad360
```

If, perchance you get errors
```
sudo chwon jim_ryan:users /home/jim_ryan/xpad360
```
and re-try above chomd command.

---

### Post by jim_ryan on 2006-09-02
thanks that worked.  That folder is now open to the world.  Thanks.

I was able to save the 3 files (xpad.c, xpad.h, makefile) to in the directory/home/jim_ryan/xpad360.

But when i: 
run make in ~/xpad360

i get an error saying:
bash: run: command not found

why doesn't it find the command make?

again cheers,

jim_ryan

---

### Post by bodhi.zazen on 2006-09-02
You need a little more install
Again, in a terminal:
```
sudo aptitude install build-essential checkinstall
```

Now:
```
./configure
make
sudo make checkinstall
```

Occasionally checkinstall fails, in that case use make install
```
./configure
make
sudo make install
```
You do not have to repeat the ./configure or make steps.

---

### Post by 3rdalbum on 2006-09-02
The 3rd line in the second block of commands should be "sudo checkinstall", not "sudo make checkinstall".

---

### Post by DonS on 2006-09-02
and since there is no configure script (just a premade makefile), you don't need to run the
'./configure' step above, just make; sudo checkinstall

---

