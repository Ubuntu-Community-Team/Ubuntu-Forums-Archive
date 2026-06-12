---
title: "No Such File or Directory"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Ouoertheo on 2007-12-05
I'm trying to get Ubuntu Studio 64 to work, and I just installed it and tried to compile my wireless drivers. All it gives me is an error code somewhat like this after I type in make/make install:

lib\modules\2.6.22-14\build. No such file or directory. Stop
[install] error 2

I've downloaded and istalled-
-dpkg-dev_1.14.5ubuntu16_all.deb
-g++_4.1.2-9ubuntu2_amd64.deb
-gcc_4.1.2-9ubuntu2_amd64.deb
-libc6-dev_2.6.1-1ubuntu9_amd64.deb
-linux-source-2.6.22_2.6.22-14.46_all.deb
-make_3.81-3build1_amd64.deb

Is there something obvious that I'm missing? 
I'd really like some help on this if anyone could spare some :)

Thanks
Jamin

---

### Post by wormser on 2007-12-05
You need to be in the same directory to run the command.  Use **cd** and **ls** commands to get to the folder with the files.  The **./** means run in the current directory.  If you are not in the same directory you have to specify the path to the file like /home/username/filetorun.

---

### Post by Ouoertheo on 2007-12-06
Thanks for the quick reply. I'm in the directory that i extracted from the tarball when I run the make command.

I run it in /home/ouoertheo/Desktop/wireless-driver-2.6
and then I run the make command, and thats where it gives me the error.

---

### Post by Dr Small on 2007-12-06
Have you installed build-essential ?
```
sudo apt-get install build-essential
```

---

### Post by Ouoertheo on 2007-12-06
yes, it says it's installed... i think. I think more of what I did was install all the components of it, since I had to download the .debs in windows and transfer them to linux. there was no big build essential package that i saw to download. if there is, can you point me to it?

---

