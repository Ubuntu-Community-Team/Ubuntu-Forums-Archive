---
title: "Frets On Fire"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by yimmmy on 2007-07-16
hi 
i was wondering how exactly to install frets on fire in linux and make a desktop icon for it,  i havent realy done much searching in this forum for it but i have looked around google and havent really found my answer, 
i would be a great help if some one showed me what to do thanks
                                                  FRETS RULES

---

### Post by loserboy on 2007-07-16
i saw this [http://debaday.debian.net/2007/07/01/frets-on-fire-play-the-guitar-with-your-keyboard-rock-em/](http://debaday.debian.net/2007/07/01/frets-on-fire-play-the-guitar-with-your-keyboard-rock-em/)

but it looks like it points to a gutsy package

---

### Post by yimmmy on 2007-07-16
yea i want it on feisty   when i get gusty ill put it on there but for now i realy want to play it again

---

### Post by yimmmy on 2007-07-16
Bump To The Maxxxx

---

### Post by loserboy on 2007-07-16
are you trying not to compile one? they have a tarball on their sourceforge page

---

### Post by yimmmy on 2007-07-16
can u walk me threw the fulll steps of what to do with it i downloaded the tar.z file\
tha would be coooool thanks

---

### Post by loserboy on 2007-07-17
well maybe we can learn together.

ok when you have the package then you need to install some programs for compiling

```
sudo apt-get install build-essential
```

and go ahead and do this too although i think the first one contains it
```
sudo apt-get install gcc
```

now in the terminal change to the directory where you downloaded the tarball , i recommend giving it it's own folder (Desktop/FoF)

then in the same terminal 

```
tar xzvf FretsOnFire-1.2.451-linux.tar.gz
```

if you plan on copy/pasting that, make sure the file name is the exact same as yours

now, in that same directory still, type
```
./configure
```

then you should see it do some stuff, copy everything it says in case there is a problem that will tell us as far as dependencies.

now type

```
make
```

then

```
sudo checkinstall
```

and now you should be ready to jam out...if not then have a look at this site, I pulled everything from it as I have compiled things before but I was just pasting what I was told [http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

lemme know how it goes

---

### Post by yimmmy on 2007-07-17
that helped great   there was a file in there called fretsonfire and i double clicked on it and it ran frets on fire 
thanks alot 



frets RULES FULES

---

### Post by loserboy on 2007-07-17
lol you mean you didn't have to compile anything and I typed all that? :(  well anyway I'm glad it works

---

