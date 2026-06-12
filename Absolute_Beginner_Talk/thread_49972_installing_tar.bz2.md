---
title: "installing tar.bz2"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by beamo on 2005-07-18
How do I unpack and install a tar.bz2 file?

---

### Post by damonw5 on 2005-07-18
[QUOTE=beamo]How do I unpack and install a tar.bz2 file?[/QUOTE]
 What are you trying to install? The way you are trying can be very complicated.

Try doing the following:

*Enable repositories: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
*Open Synaptic (under System->Administration menu)
*Click the "refresh" button
*Search for the program you're looking for
*If it's there, then you can install it right in Synaptic!

---

### Post by souki on 2005-07-18
```
# to list the files:
tar jtf file.tbz2

# to extract:
tar jxvf file.tbz2
```

---

### Post by Kyral on 2005-07-18
First off. Do you need to? 98% of the software can be installed through Synaptic and the extra Repos like Backports.

Anyway, to install a tar.bz2 you have to decompress it with the command tar -jxvf <filename>

Then you have to read the README in the file to find out what to do.

---

### Post by beamo on 2005-07-18
Thanks for the help. I extracted and set up the directory following the readme instructions. When I try to tun the file they say to run, i get this error:

root@ubuntu:/games/mistland/zerofpsv2/bin # ./runmistserver.sh
Running in workdirectory, and setting LD_LIBRARY_PATH to curent direcotry
./mistserver.bin: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory

Do I need to add a library or something?

---

### Post by Kyral on 2005-07-18
[QUOTE=beamo]Thanks for the help. I extracted and set up the directory following the readme instructions. When I try to tun the file they say to run, i get this error:

root@ubuntu:/games/mistland/zerofpsv2/bin # ./runmistserver.sh
Running in workdirectory, and setting LD_LIBRARY_PATH to curent direcotry
./mistserver.bin: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory

Do I need to add a library or something?[/QUOTE]
 Yup

Do a sudo apt-get install libsdl-net1.2 libsdl-net1.2-dev

---

