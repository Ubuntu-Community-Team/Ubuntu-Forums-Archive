---
title: "HELP with make...."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-18
hey, I'm trying to get the 3d windows plugin compiled and working with my compiz-fusion. 


I first used:
sudo apt-get install gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc

and then typed in:
git clone git://anongit.compiz-fusion.org/fusion/plugins/3d



and then I went to my ~/3d dir, and tried:
make

and I get this error:
```

b34st1y@zer0cool:~/3d$ sudo make && sudo make install
convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: not found
make: *** [build/3d_options.h] Error 127
b34st1y@zer0cool:~/3d$ make
bcop'ing  : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: not found
make: *** [build/3d_options.h] Error 127
b34st1y@zer0cool:~/3d$ 

```



any help would be SO incredibly appreciated. Help me out!!

---

### Post by nowshining on 2007-12-18
actually 

cd into the src directory of the untared/unzipped file

issue the following

./configure

if u get errors post back..

then it's

make

then 

sudo make install

then sudo make clean



if u have checkinstall installed u  can create a deb file for later re-install and so forth..then u'd do the following

,/configure

make

sudo checkinstall -D make install

follow the directions,  input a name change version info and so forth

then

sudo make clean to remove tmp files.

oh and cd back into the main direcoty for make if it does not work out in the src folder by typing the terminal the command

cd and two dots or periods and hitting enter.

---

### Post by B34ST1Y on 2007-12-18
works great, thx fro the help

---

### Post by nowshining on 2007-12-18
ur welcome and also just in case u'd like to build again


sudo apt-get install build-essential

it grabs all basic needed libs/dev files and stuff for compiling.

---

### Post by hyper_ch on 2007-12-18
don't do
```

sudo make

```

sudo should only be used for the installation...

---

