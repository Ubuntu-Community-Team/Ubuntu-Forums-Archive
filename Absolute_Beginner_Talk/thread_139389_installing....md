---
title: "installing..."
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by montablac on 2006-03-03
can i get a walkthrough on how to install a .tar.gz package

or if you can find a .deb mp3 encoder ill take that

many thanks
 -montablac

---

### Post by codejunkie on 2006-03-03
[QUOTE=montablac]can i get a walkthrough on how to install a .tar.gz package

or if you can find a .deb mp3 encoder ill take that

many thanks
 -montablac[/QUOTE]
enable the universe & multiverse repos in your sources.list file run 
```
sudo apt-get update
```then```
sudo apt-get install lame lame-extras
```

---

### Post by darth_vector on 2006-03-03
codejunkie... i've heard that handle before.

are you a totsean?

---

### Post by codejunkie on 2006-03-04
[QUOTE=darth_vector]codejunkie... i've heard that handle before.

are you a totsean?[/QUOTE]
if i new what you ment by **are you a totsean** i'd be able to answer that one, but mostly im confused just confused. ;)

---

### Post by montablac on 2006-03-04
ok,well,im DLing the package info now

but the .tar.gz package WAS lame and i was hoping for a quick walk through for it

oh well,thanks any way,this should be easer

---

### Post by codejunkie on 2006-03-04
[QUOTE=montablac]ok,well,im DLing the package info now

but the .tar.gz package WAS lame and i was hoping for a quick walk through for it

oh well,thanks any way,this should be easer[/QUOTE]

if you really wan't to compile it open a terminal run 
```

sudo apt-get install linux-headers-`uname -r` build-essential automake

```
extract the file by right clicking on it and choose extract open the terminal cd into that folder then run these commands in order.
```
./configure --prefix=/usr
```
wait until it finishes
then run
```
make
```
again wait till this finishes then run this if everything compiled without errors
```
sudo make install
```
if you get error's while running ./configure --prefix=/usr look through the output where it stopped, and install the dependicies it needs and rerun ./configure --prefix=/usr

if you get a make error look at the bottom of the output and install those dependicies rerun make
i now this is a vague walk through but every package is different so the instructions change for every package but this will work for most. 

and to run lame open a terminal cd to dir contaning the audio file and run 
```
lame fileyouwantconverted
```

---

### Post by darth_vector on 2006-03-05
[QUOTE=codejunkie]if i new what you ment by **are you a totsean** i'd be able to answer that one, but mostly im confused just confused. ;)[/QUOTE]

lol, soz. i meant a member of totse; [http://www.totse.com/](http://www.totse.com/)

there is a mod there called lifejunkie and i got confused :-)

---

### Post by codejunkie on 2006-03-05
> **darth_vector]lol, soz. i meant a member of totse said:**
> http://www.totse.com/[/url]

there is a mod there called lifejunkie and i got confused :-)
nope not a member there, ubuntuforums is where i spend all my posting time.

---

