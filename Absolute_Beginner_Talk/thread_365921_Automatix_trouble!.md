---
title: "Automatix trouble!"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by olskar on 2007-02-20
I get this kind of message whatever I try to install with automatix2

WARNING: The following packages cannot be authenticated!
libvorbisfile3 python-elementtree python-mutagen python-pyogg python-pysqlite2
python-pyvorbis
E: There are problems and -y was used without --force-yes

Please help me!!

---

### Post by jvc26 on 2007-02-20
How are you trying to install automatix? Have you tried the instructions here?:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)
Il

---

### Post by olskar on 2007-02-20
I have tried that..still got the 'cannot be authenticated' messages...

---

### Post by louis_nichols on 2007-02-20
First off, especially if you're using edgy, but also for breezy, I wouldn't recommend using Automatix. That was useful back in the hoary days, but the last time I used it there weren't any packages that you couldn't install in a different and ultimatelly safer way.

As for your error, there are 2 ways to get rid of it. One is to add the keys the packages are signed with to apt's list and another way is to modify the automatix script to use the --force-yes flag.

The first method is difficult because you have to find ut where the keys are stored on the web. If you do find them, what you need to do is:

```
wget *path-to-key-file* | sudo apt-key add - 
```

The second method is difficult because you have to edit the script file, find where the failing command is and adding the flag --force-yes at the end.

The choice is yours. I recommend simply using synaptic, though.

---

### Post by olskar on 2007-02-20
I really want to use automatix..It seems so much easier.. Why is it working for everyone else? Where do they get there keys? :S Please help me with this...

---

