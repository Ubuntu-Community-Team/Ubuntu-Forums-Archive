---
title: "software"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by emo on 2005-10-02
I can't install any software I need help :(

---

### Post by aysiu on 2005-10-02
Read the last link in my sig.

---

### Post by TristanMike on 2005-10-02
What exactly have you done that hasn't gone as expected.  Have you edited you sources.list file yet? If not, a nice one can be found [Here for Hoary](http://paste.ubuntulinux.nl/969) and [Here for Breezy](http://paste.ubuntulinux.nl/2325).  Once you do that, and ```
sudo apt-get update
```you can search via Synaptic for software that floats your boat and install that way, or find the name in Synaptic and install it using the *exact* name in the terminal by ```
sudo apt-get install <ExactPackageName>
```If by chance it doesn't appear in the menu's you can run via the terminal by just typing it's name. For instance, "cdcat" a cd/dvd cataloger can be run with the command ```
cdcat
```
Hope this helps

---

### Post by emo on 2005-10-03
/home/emerson/Desktop/Screenshot.png
]

---

### Post by emo on 2005-10-03
root@ubuntuemerson:/home/emerson # sudo apt-get install RealPlayer 10GOLD.bin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package RealPlayer
root@ubuntuemerson:/home/emerson #

Hi guys perhaps I'm too silly like you see I still got a problem....:(

---

### Post by darkmatter on 2005-10-03
[QUOTE=emo]root@ubuntuemerson:/home/emerson # sudo apt-get install RealPlayer 10GOLD.bin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package RealPlayer
root@ubuntuemerson:/home/emerson #
Hi guys perhaps I'm too silly like you see I still got a problem....:([/QUOTE]

Are you on Hoary or Breezy? It will help point us in the right direction to assist you.

---

### Post by cwaldbieser on 2005-10-03
[QUOTE=emo]root@ubuntuemerson:/home/emerson # sudo apt-get install RealPlayer 10GOLD.bin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package RealPlayer
root@ubuntuemerson:/home/emerson #
Hi guys perhaps I'm too silly like you see I still got a problem....:([/QUOTE]
"RealPlayer 10Gold.bin" is the name of an executable off of Real's download page.  It isn't the name of the package in the repositories.  The package name is "realplayer".

If you have their binary, you run it like
```

$ ./"RealPlayer 10Gold.bin"

```

---

### Post by Mustard on 2005-10-03
try

```
sudo apt-get install realplayer
```

As has been said earlier the binary you are trying to install works differently to downloading software using Synaptic.

---

