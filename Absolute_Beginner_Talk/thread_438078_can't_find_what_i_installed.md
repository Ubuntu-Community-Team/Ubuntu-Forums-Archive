---
title: "can't find what i installed"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Eredeath on 2007-05-09
I installed aivdemux using the package manager but can't seem to find where it went. I'll open the terminal and type in "avidemux" and i get

"The program 'avidemux' is currently not installed.  You can install it by typing:
sudo apt-get install avidemux
Make sure you have the 'multiverse' component enabled
bash: avidemux: command not found"

so i do what it tells me and it runs a few lines and nothing happens, it tells me nothing has been installed or upgraded. I've checked my add/remove programs which says its installed and my synaptic package manager which also says it's installed.

I've just switched from windows to Ubuntu so i tend to use the GUI more than the terminal but I'm not afraid to use it. Any help would be appreciated. Thanks.

---

### Post by Bachstelze on 2007-05-09
```
avidemux2
```

---

### Post by Nythain on 2007-05-09
do you have the universe and multiverse repositories enabled... if yes, then type
sudo apt-get install avidemux
tell us what it says

nevermind... thanks hymm

---

### Post by Bachstelze on 2007-05-09
Actually, you might be more right than me, the Ubuntu package for Avidemux installs the executable in /usr/bin/avidemux...

Eredeath > Are you sure Avidemux is installed ?

```
dpkg -l | grep avidemux
```

---

### Post by Eredeath on 2007-05-09
yea i'm pretty sure it's installed. This is the code i got after i typed in "dpkg -l | grep avidemux"

"ii  avidemux                                   2.3.0-prev1-1                          Package created with checkinstall 1.6.0"

aslo avidemux2 didn't work...

---

### Post by Eredeath on 2007-05-09
this is what i get when i put in avidemux2

"avidemux2: error while loading shared libraries: libsmjs.so.1: cannot open shared object file: No such file or directory"

---

### Post by Bachstelze on 2007-05-09
Then you didn't install avidemux from the Ubuntu repositories.... You'll have to install the needed libraries yourself :

```
sudo apt-get instal libsmjs1
```

---

### Post by Eredeath on 2007-05-09
Okay i did that and it said it installed, again i tried to run avidemux but got 
"avidemux2: error while loading shared libraries: libmp3lame.so.0: cannot open shared object file: No such file or directory"
so following your example i put "sudo apt-get install libmp3lame" 
and it spat back
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmp3lame"

---

### Post by Bachstelze on 2007-05-10
The name of the package is not always the same as the name of the file. Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for that file in the fied at the bottom of the page, it will tell you which package the file is in.

---

### Post by Eredeath on 2007-05-10
YAY I DID IT! Thank you so much HymnToLife (which by the way is an awsome sn) i'll be sure to pass on what i learned if someone needs it. Thanks again :-)

---

### Post by Eredeath on 2007-05-10
one more question, how did you know that i had to put in avidemux2 and not just avidemux?

---

