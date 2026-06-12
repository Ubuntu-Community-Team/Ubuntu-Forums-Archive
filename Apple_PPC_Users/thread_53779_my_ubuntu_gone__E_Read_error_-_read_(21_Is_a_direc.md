---
title: "my ubuntu gone : E: Read error - read (21 Is a directory)"
date: 2005-08-02
forum: Apple PPC Users
---

### Post by lycos on 2005-08-02
my ubuntu cant be updated anymore..  :? 
also, i cant install any program  :mad: 

when i tried to install a program via the console;
Reading Package Lists... Done
E: Read error - read (21 Is a directory)
i get this error alltimes.  ](*,) 

when i open the synaptic,
the same message again:  ](*,) 
E: Read error - read (21 Is a directory)
and i cant see any program in the list.

pls somebody help me :)  :roll:

---

### Post by craks on 2005-08-02
check your source.list firstly, maybe it contains wrong syntax

---

### Post by lycos on 2005-08-02
i checked the sources.list file but i found nothing wrong?
it is driving me crazy :)

but if somebody can send me an original sources.list file; it will be usefull :???: 
thanks for your time..

---

### Post by lycos on 2005-08-03
cant anybody help me ?  :roll:  :roll:  :roll:

---

### Post by varunus on 2005-08-03
What did you do right before this error occured?  Did you install anything?  Do something accidentally in sudo nautilus or from a root terminal?

Here's a working sources.list file:
```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## Multiverse repositories
 deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse

## Hoary Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

 deb http://security.ubuntu.com/ubuntu hoary-security multiverse
 deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

```

---

### Post by lycos on 2005-08-05
](*,)  
i tried the source.list file but nothing changed.
i dont really remember what i did with the synaptic before :(
i cant solve this mystery???
i can update repositories via apt-get update command,
but when i tried the apt-get install or remove command allways saying:
E: Read error - read (21 Is a directory)

when i opened synaptic, it is saying the same thing...
:neutral:  :-#  [-X  O:)  :| 
i am totally lost...

---

### Post by varunus on 2005-08-05
I googled the error, and saw two references to it, but neither one resulted in a solution...Sorry, it looks like you'll have to reinstall.  I have no idea what happened to cause this problem...Sorry.  At least you have the chance to get your files off since your computer isn't totally dead.

What kind of hard drive do you have?  Are you overclocking any?  How old is the hard drive?  Maybe its a hardware problem?  I don't know...

Sorry for all the problems...hopefully you'll reinstall and keep with ubuntu, its a great distro.  (And I've never seen that problem before...and apparently, only two other ppl on google have seen that problem.)

---

### Post by lycos on 2005-08-05
thanks anyway, :)
it seems i am one of the tree unlucky guys in the world  ](*,) 
my hard drive is new..
my mac is g4.
i have mac x too.
i can reinstall the ubuntu..
it is really a good distro.

---

### Post by kriegtheone on 2007-10-24
Hola

me a pasado lo mismo, lo e corregido eliminando de /var/lib/dpkg el directorio status y creando el 
archivo status...


# rmdir /var/lib/dpkg/status
# touch /var/lib/dpkg/status

bueno para mi funciono }:^)

---

