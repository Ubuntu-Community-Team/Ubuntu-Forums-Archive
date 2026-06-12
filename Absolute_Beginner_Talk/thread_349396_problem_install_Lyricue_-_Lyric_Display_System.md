---
title: "problem install Lyricue - Lyric Display System"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by ez3401 on 2007-01-30
Just intalled unbuntu for the first time. Please forgive me if I ask questions that should have obvious answeres.
I am having a problem insalling "Lyricue - Lyric Display System".
THese are the directions on the webpage on how to install Lyricue:
The easiest way to download/install is using Debian or Ubuntu
Just add
deb [http://www.adebenham.com/debian/](http://www.adebenham.com/debian/) ./
to your /etc/apt/sources.list file then install the "lyricue" package
How do I add it to */ect/apt.*.. Where is that? If someone could hold my hand I am sure I will progress in my skills with linux.



PS
I live in Latvia where people don't have much money to spend on Windows etc. and pirate the programs they do have. My goal is to learn linux and help Latvians and others to use open source software. I have a long way to go. Thank you for your helping me.

---

### Post by lisje on 2007-01-30
> **ez3401 said:**
> ...
THese are the directions on the webpage on how to install Lyricue:
The easiest way to download/install is using Debian or Ubuntu
Just add
deb [http://www.adebenham.com/debian/](http://www.adebenham.com/debian/) ./
to your /etc/apt/sources.list file then install the "lyricue" package


What they meant by "just add" is:

1) open up a terminal
2) type:
```

sudo gedit /etc/apt/sources.list

```
3) add the line they suggested at the end of the file (do not change anything else):
```

deb [http://www.adebenham.com/debian/](http://www.adebenham.com/debian/) ./

```
4) save the file, close it and then run:
```

sudo apt-get update

```
5) if everything went okay (no error messages) you can now install lyrique:
```

sudo apt-get install lyrique

```

I hope that helps.

Greets,
Lisje

---

### Post by efrenjiji on 2008-01-22
Hi I just followed the steps you've written here and it gives me this result, can I ask for more help? thanks

efren@efren-desktop:~$ sudo apt-get update
Get:1 [http://www.adebenham.com](http://www.adebenham.com) ./ Release.gpg [189B]                
Ign [http://www.adebenham.com](http://www.adebenham.com) ./ Translation-en_US                            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Get:3 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Hit [http://www.adebenham.com](http://www.adebenham.com) ./ Release
Err [http://www.adebenham.com](http://www.adebenham.com) ./ Release                           
  
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports Release            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Translation-en_US
Get:6 [http://www.adebenham.com](http://www.adebenham.com) ./ Release [495B]                     
Ign [http://www.adebenham.com](http://www.adebenham.com) ./ Release                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Translation-en_US
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/main Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release.gpg [191B] 
Ign [http://www.adebenham.com](http://www.adebenham.com) ./ Packages                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/universe Packages  
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://www.adebenham.com](http://www.adebenham.com) ./ Packages                             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/main Sources       
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) feisty-backports/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Fetched 690B in 5s (131B/s)
Reading package lists... Done
W: GPG error: [http://www.adebenham.com](http://www.adebenham.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A7BC8E1B734D1F5
W: You may want to run apt-get update to correct these problems

---

### Post by lisje on 2008-01-28
> **efrenjiji said:**
> 
W: GPG error: [http://www.adebenham.com](http://www.adebenham.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A7BC8E1B734D1F5
W: You may want to run apt-get update to correct these problems

The error you get here is because you don't have a key. Though I don't think it prevents you from installing the program.

I did some research on the program and searched it in the Ubuntu repository and it is actually there.
So you do not need to add the repository to the sources.list .

You should be able to install it via the package manager or apt-get or whatever you want to use.

---

