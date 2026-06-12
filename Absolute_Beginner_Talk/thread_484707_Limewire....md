---
title: "Limewire..."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by night_raiders on 2007-06-26
Can someone help me try to install limewire when i go to install it just says can only run 1 software management

---

### Post by Pizzarth on 2007-06-26
don't. use frostwire. it's just like it, cept it has chat and you can install it from the repositories. only thing you'll find on the limewire site is the .rpm seriously, frostwire is almost a clone of limewire. it uses the gnutella network too.

---

### Post by REDISISTone.nl on 2007-06-26
If you are looking for software alternative&#8217;s just take a look at [this]("http://linuxappfinder.com/windows") website...

Good Luck ;)

---

### Post by night_raiders on 2007-06-26
it stills says only one software mamagement is allowed to run... idk what a other software management thing would be

---

### Post by cosborn72 on 2007-06-26
I know that, in the past, I was unable to run synaptic or any other package manager while Adept notifier was on.  Do you get notifications in your panel when updates are avaible?  If so, that my be you problem.   However, I wouldn't think that Limewire would affect it, since it is a totally different beast from synaptic/adept/apt.

---

### Post by 3rdalbum on 2007-06-26
The Add/Remove Programs
Synaptic Package Manager
Update Manager
If you've run apt-get from the command-line and it's waiting for input from yourself, then that will also do it.

If you've checked all those and none of them are open, try restarting.

---

### Post by night_raiders on 2007-06-26
i tried goin to the sypnaptic thing and this popped up and it also happens when i try to install some things 
 >  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E:_cache->open() failed, please report. 

---

### Post by night_raiders on 2007-06-26
help....

---

### Post by Pizzarth on 2007-06-27
I suggest you run the code it said to ^^ dpkg --configure -a

just saying though, frostwire would have been simpler. synaptic it

---

### Post by night_raiders on 2007-06-27
yea i dont i am trying to get frostwire but i gotta get the code thing tooken care of

---

### Post by southernman on 2007-06-27
do this in a terminal, as the terminal and others asked you to do... then install frostwire.

> sudo dpkg --configure -a 

---

### Post by cwood06 on 2007-06-27
if you want to get it from a repo do 

```


sudo apt-get install frostwire

```

that will download and install all the necessary dependences.

---

### Post by night_raiders on 2007-06-27
that didnt do anything it says when i try to install error: failed to satisfy all dependencies (broken cache)

---

### Post by cwood06 on 2007-06-27
try updating your source list i just did it for mine and it worked fine. 
```
colin@colin-desktop:~$ sudo apt-get install frostwire 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  java-common liblog4j1.2-java libltdl3 memtester odbcinst1debian1 procinfo
  sun-java6-bin sun-java6-jre sysutils tofrodos unixodbc
Suggested packages:
  equivs libgnumail-java sun-java6-plugin ia32-sun-java6-plugin
  sun-java6-fonts ttf-sazanami-gothic ttf-sazanami-mincho libmyodbc
  odbc-postgresql libct1
The following NEW packages will be installed:
  frostwire java-common liblog4j1.2-java libltdl3 memtester odbcinst1debian1
  procinfo sun-java6-bin sun-java6-jre sysutils tofrodos unixodbc
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.6MB of archives.
After unpacking 112MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

to update do sudo apt-get update

---

### Post by night_raiders on 2007-06-27
>  chris@c-68-53-27-92home:~$ sudo apt-get install frostwire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package frostwire 

well

---

### Post by cwood06 on 2007-06-27
actully if you dont have this software check it out 
[http://www.getautomatix.com/](http://www.getautomatix.com/)
this has frostwire along with alot of other great apps makes it easy \\:D/

[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.7-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.7-7.04feisty_i386.deb)

---

### Post by night_raiders on 2007-06-27
well its installing as of now.... thanks for the help and that made this alot easier

---

### Post by cwood06 on 2007-06-27
yea automatix is the crap for this stuff it installs alot of stuff likethe flash plugins for firefox and such has alot of good stuff.

(damn you stuff)

---

### Post by southernman on 2007-06-27
Not to rub it in, but I just installed all the java needed, and frostwire... in the last 20 minutes. Frostwire is running perfectly.

I did so using the help guide for ubuntu found here... [https://help.ubuntu.com/community/FrostWire]("https://help.ubuntu.com/community/FrostWire")

---

### Post by cwood06 on 2007-06-27
> **southernman said:**
> Not to rub it in, but I just installed all the java needed, and frostwire... in the last 20 minutes. Frostwire is running perfectly.

I did so using the help guide for ubuntu found here... [https://help.ubuntu.com/community/FrostWire]("https://help.ubuntu.com/community/FrostWire")

Yea you can do it that way but automatix is just nice to have I wish i knew of this program when i was just starting to use linux

---

### Post by night_raiders on 2007-06-27
i dont know if its supposed to be like this but it is still on the same step it was on 20 mins ago when i got in the shower is it just slow or is there probably a problem

---

### Post by cwood06 on 2007-06-27
probbly depends on your internet connection i think it has to dl 40mbs of stuff should be all good

---

