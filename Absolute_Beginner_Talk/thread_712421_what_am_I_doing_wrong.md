---
title: "what am I doing wrong?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by nbv4 on 2008-03-01
nbv4@nbv4-desktop:~$ cd yam-linux/
nbv4@nbv4-desktop:~/yam-linux$ ls
libfmodex.so.4.02.05  Readme.txt  YamiPod
nbv4@nbv4-desktop:~/yam-linux$ YamiPod
bash: YamiPod: command not found
nbv4@nbv4-desktop:~/yam-linux$ ./YamiPod
bash: ./YamiPod: No such file or directory


What the hell am I doing wrong? The YamiPod documentation says to just double click  on the binary file, but when I do that, nothing happens.

---

### Post by northern lights on 2008-03-01
[QUOTE=yamipod documentation]    * make sure you've used iTunes at least once (under Windows or Mac OS X)
    * have at least one song on iPod
    * copy the libfmodex audio library to /usr/lib (root priviledges needed). You'll find this file in the package you've downloaded
    * mount your iPod somewhere inside /mnt or /media with read/write access
    * make sure you have the df command installed, which is usually part of any standard linux distriburion. [/QUOTE]

Have you followed these instructions?

---

### Post by LuisGMarine on 2008-03-01
Are you sure you copied over the library to */usr/lib*?

go into your yam-linux directory where ever it is, then run this command:

```
sudo cp libfmodex.so.4.02.05 /usr/lib
```

then all you have to do is double click on the binary and it should run.

---

### Post by nbv4 on 2008-03-01
> **northern lights said:**
> Have you followed these instructions?

none of those things matter if I can't even start the damn program. You click on the file, the program launches, and then you go from there. Its acting as if the file doesn't exist. When I do a "ls", it clearly shows the file as being there. this is very odd.

---

### Post by nbv4 on 2008-03-01
> **LuisGMarine said:**
> Are you sure you copied over the library to */usr/lib*?

go into your yam-linux directory where ever it is, then run this command:

```
sudo cp libfmodex.so.4.02.05 /usr/lib
```

then all you have to do is double click on the binary and it should run.

yes i already copied over the lib. Would the lib not being there cause the "No such file or directory" error?

---

### Post by LuisGMarine on 2008-03-01
sorry let me re-think

---

### Post by jken146 on 2008-03-01
Please post the output of ```
ls -l ~/yam-linux
```

---

### Post by nbv4 on 2008-03-01
```
nbv4@nbv4-desktop:~$ ls -l /home/nbv4/Desktop/yam-linux
total 15844
-rwxr-xr-x 1 nbv4 nbv4  1040948 2005-12-20 21:42 libfmodex.so.4.02.05
-rw-r--r-- 1 nbv4 nbv4      781 2007-04-27 07:36 Readme.txt
-rwxrwxrwx 1 nbv4 nbv4 15150316 2007-11-15 15:54 YamiPod

```

---

### Post by LuisGMarine on 2008-03-01
Ok lets start from square one.

Download the Linux binary version, and save it to your desktop.  

Unzip the badboy with such command:

```
tar -xvzf yam-linux.tar.gz 
```

change directory to your new untared folder:

```
cd yam-linux/
```

Copy over the proper library:

```
sudo cp libfmodex.so.4.02.05 /usr/lib
```

Check to make sure the library is there, run this command if it returns something its good to go if it returns and error then that's something else
```

ls /usr/lib | grep libfmodex.so.4.02.05 
```

Open the yam-linux folder in your desktop and double click on the binary named something like Yamipod or something like that. 

Not make sure that your ipod is connected and you have write access and all that fancy stuff to it.  I noticed when I just installed it , that the program wouldn't go very far without my ipod being hooked up to the computer.

Good luck

---

### Post by jken146 on 2008-03-01
> **nbv4 said:**
> ```
nbv4@nbv4-desktop:~$ ls -l /home/nbv4/Desktop/yam-linux
total 15844
-rwxr-xr-x 1 nbv4 nbv4  1040948 2005-12-20 21:42 libfmodex.so.4.02.05
-rw-r--r-- 1 nbv4 nbv4      781 2007-04-27 07:36 Readme.txt
-rwxrwxrwx 1 nbv4 nbv4 15150316 2007-11-15 15:54 YamiPod

```

Well, it is executable.

---

### Post by nbv4 on 2008-03-01
> **LuisGMarine said:**
> Ok lets start from square one.

Download the Linux binary version, and save it to your desktop.  

Unzip the badboy with such command:

```
tar -xvzf yam-linux.tar.gz 
```

change directory to your new untared folder:

```
cd yam-linux/
```

Copy over the proper library:

```
sudo cp libfmodex.so.4.02.05 /usr/lib
```

Check to make sure the library is there, run this command if it returns something its good to go if it returns and error then that's something else
```

ls /usr/lib | grep libfmodex.so.4.02.05 
```

Open the yam-linux folder in your desktop and double click on the binary named something like Yamipod or something like that. 

Not make sure that your ipod is connected and you have write access and all that fancy stuff to it.  I noticed when I just installed it , that the program wouldn't go very far without my ipod being hooked up to the computer.

Good luck

I've done all of that, when I run that command to see if the library is installed, it spits out "libfmodex.so.4.02.05", meaning it's there. When I plug in my iPod, I get the little ipod icon on my desktop, but when I try to double click on the YamiPod icon, nothing happens. If the problem was with YamiPod, wouldn't it give me an error other than "directory does not exist"? I've been using Ubuntu for 2 years now and I've never seen anything like this...

---

### Post by nispe on 2008-06-06
I also have the same problem as nbv4, so any help would be appreciated.

---

