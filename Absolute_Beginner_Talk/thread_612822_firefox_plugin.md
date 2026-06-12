---
title: "firefox plugin"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by kaidenet on 2007-11-14
I am having problems getting flash player,real player, Java, etc to be installed onto my Firefox. Every time I download a .rmp .yum or .tar.gz files, I just cannot load this programs to get the plugins installed. What should I do?

---

### Post by Znort_Ubern00b on 2007-11-14
go to firefox website and look for the add ons on the extensions page.  they now have real player, win media player add ons for firefox

---

### Post by Inxsible on 2007-11-14
> **kaidenet said:**
> I am having problems getting flash player,real player, Java, etc to be installed onto my Firefox. Every time I download a .rmp .yum or .tar.gz files, I just cannot load this programs to get the plugins installed. What should I do?

Ubuntu is a Debian derivative. It cannot install .yum or .rpm(red hat) installers. It can only install .deb files. If .deb files are available, you should download those.

Having said that, you can also use alien to convert the .rpm files to .deb and then install them.

---

### Post by kaidenet on 2007-11-14
Ok, alien. I see, where do I get alien or is it alr in my OS?

---

### Post by Inxsible on 2007-11-14
> **kaidenet said:**
> Ok, alien. I see, where do I get alien or is it alr in my OS?
```
sudo aptitude install alien
```

---

### Post by philinux on 2007-11-14
It's in synaptic

---

### Post by svalding on 2007-11-14
```
 sudo apt-get install alien 
``` will get it for you. 

You can always unpack the .tar.gz files and build it from source using the instructions that come inside the folder. Typically it is a 4 step process

cd to directory where you downloaded the file to and unpack
```

./configure 
make
make install

```

and you're in business!

---

### Post by kaidenet on 2007-11-15
> **svalding said:**
> ```
 sudo apt-get install alien 
``` will get it for you. 

You can always unpack the .tar.gz files and build it from source using the instructions that come inside the folder. Typically it is a 4 step process

cd to directory where you downloaded the file to and unpack
```

./configure 
make
make install

```

and you're in business!


Erm, so how do I type in the code sudo apt-get install alien.....

Sorry but it's a real Linux n00b here, need a lot of dummy help.

---

### Post by Inxsible on 2007-11-15
open up a terminal (Applications>>Accessories>>Terminal) and type it in

---

### Post by ukripper on 2007-11-15
may interest you [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jryprt on 2007-11-15
> **kaidenet said:**
> I am having problems getting flash player,real player, Java, etc to be installed onto my Firefox. Every time I download a .rmp .yum or .tar.gz files, I just cannot load this programs to get the plugins installed. What should I do?

Check out this thread [http://ubuntuforums.org/showthread.php?t=612906](http://ubuntuforums.org/showthread.php?t=612906) it is how I got flash player in firefox

---

