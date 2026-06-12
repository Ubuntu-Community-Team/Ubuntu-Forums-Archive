---
title: "Simple question about .bin files"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by dljesse on 2007-08-10
I don't know how to execute them. I'm aware that I need to use <chmod +x> and <./>, but I don't know where to put these. For example, if I want to execute lolifox.bin and it's in the   home/jesse/lolifox       directory, how do I exucute it. An example would be great. I trIed google, but they only put  <chmod+x lolifox.bin>  or  <./lolifox.bin> without the directory.

---

### Post by Pragmatist on 2007-08-10
Normally you put individual user applications in /usr/local directories such as /usr/local/share  You need to use sudo for this.
Edit: This is just a convention.  You can put them almost anywhere.  Another popular location is somewhere in the user's home directory.
```
sudo cp $HOME/filename.bin /usr/local/share
``````
cd /usr/local/share
``````
chmod a+x filename.bin
``````
sudo ./filename.bin
```

---

### Post by Majorix on 2007-08-10
Change the working directory to /home/jesse/lolifox:
```
cd ~/lolifox
```
Make the file executable:
```
chmod +x lolifox.bin
```
Run it:
```
./lolifox.bin
```

Hope it helps you.

---

### Post by dljesse on 2007-08-10
Never mind that

---

### Post by Pragmatist on 2007-08-10
Ok :)

---

### Post by dljesse on 2007-08-10
jesse@jesse-desktop:~$ cd /home/jesse/lolifox
jesse@jesse-desktop:~/lolifox$ chmod +x lolifox.bin
jesse@jesse-desktop:~/lolifox$ ./lolifox.bin
./lolifox.bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

This what I typed in, and got that error

---

### Post by Pragmatist on 2007-08-10
Is there a README or INSTALL file in the lolifox directory?  If there is, read them.  You might need to run the .bin with sudo:
```
sudo ./lolifox.bin
```

---

