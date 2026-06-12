---
title: "cant install w64codecs"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by sentient.being on 2008-01-04
i simply cant seem to get .rm files to play.... :C
reading the RestrictedFormats section on Ubuntu's site, 
i added the medibuntu repo to my software sources and tried to install w64codecs.
it says 'package not found' so i use -
wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu2_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu2_amd64.deb)

to get it. and 'sudo dpkg -i w64codecs_20061203-0medibuntu2_amd64.deb' to install it.

but it says -

w64codecs depends on libc6 (>= 2.6-1); however:
Version of libc6 on system is 2.5-0ubuntu14.
w64codecs depends on libgcc1 (>= 1:4.2.1); however:
Version of libgcc1 on system is 1:4.1.2-0ubuntu4.
w64codecs depends on libstdc++6 (>= 4.2.1); however:
Version of libstdc++6 on system is 4.1.2-0ubuntu4.
dpkg: error processing w64codecs (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
w64codecs

help somebody :::

---

### Post by steeleyuk on 2008-01-04
Have you ran **sudo apt-get update** and **sudo apt-get upgrade** since adding the repository? This will update the list of repositories and upgrade the packages it finds. Then it should also you to install w64codecs.

---

### Post by LowSky on 2008-01-04
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

```
sudo apt-get install w64codecs
```

---

### Post by LowSky on 2008-01-04
.rm files are real media right? Try to install helix player

---

### Post by Perfect Storm on 2008-01-04
w64codecs handles rm files very well. Alternative is using VLC - It doesn't require anything extra.

---

### Post by sentient.being on 2008-01-04
sorry i forgot to mention, i am using ubuntu 7.04 with amd64.

@steeleyuk
yes...i updated the repo several times..

@lowsky
yes, i.rm == real files. but can helix run them? i heard i need to install real playre...but there r several problems of realplayer with amd64

@Artificial Intelligence
i have got VLC, but it dosnt seem to run .rm and .rmvb files.

---

### Post by LowSky on 2008-01-04
helix is te linux open version of real
use synaptic to install helix it will deal with all the 64bit issues, at least i should

as for my codes, heres the fiesty ones
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by sentient.being on 2008-01-05
could you give me the code to install helix player?

and i rand 'apt-get upgrade' and again 'apt-get update'.
now i tried to install w64codecs and it did!!!
but mplayer still does not play .rm/.rmvb files  :-C
whats the problem?

---

