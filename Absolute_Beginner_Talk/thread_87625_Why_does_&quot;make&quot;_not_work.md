---
title: "Why does &quot;make&quot; not work?"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by EC-Rider on 2005-11-08
Since I tried every sugestion within this forum to get my Officejet R45 going with the HPOJ program (scanner part, printer is working perfectly), I though to do compiling and linking myself. I downloaded the hpoj driver from hpoj.sf.net and did nicely ./configure. This was going well and within a minute I got the message to type in "make". After several seconds I was back at the command prompt... The message I received is: 

         -L/home/jan/hpoj-0.91/lib/ptal -L/home/eric/hpoj-0.91/lib/sane
        -DHPOJIP_INTERNAL -fPIC -c -o xjpg_fix.shared.o xjpg_fix.c
        xjpg_fix.c: In function ‘jpgFix_getActualTraits’:
        xjpg_fix.c:512: error: invalid lvalue in assignment
        xjpg_fix.c:533: error: invalid lvalue in assignment
        xjpg_fix.c:549: error: invalid lvalue in assignment
        xjpg_fix.c:560: error: invalid lvalue in assignment
        xjpg_fix.c:581: error: invalid lvalue in assignment
        xjpg_fix.c:587: error: invalid lvalue in assignment
        xjpg_fix.c:595: error: invalid lvalue in assignment
        xjpg_fix.c:605: error: invalid lvalue in assignment
        xjpg_fix.c:610: error: invalid lvalue in assignment
        make[1]: *** [xjpg_fix.shared.o] Error 1
        make[1]: Leaving directory `/home/jan/hpoj-0.91/lib/hpojip'
        make: *** [just_compile] Error 2

Does anyone know what I did wrong? 
Am I missing a package?
Is compiling/linking and installing yourself not possible in Ubuntu?

I hope someone can help me with an answer on all my questions. Thank you very much in advance.

---

### Post by ssam on 2005-11-08
i dont know about your specific printing problem, but i can help you get the compile to work.

first off, ubuntu does not install very much be default, just what you need for a basic desktop system. compilers and developement libraries are one of the things left out. luckily they are easy to install.

open up synaptic package manager, and search for build-essential. then click the box by its name and select install. then click apply. this will install the essentials for building software, including make.

the ./configure will probably go a bit further now, and then stop at some other message. there are likely to be several dependancies that you need. for example if it said you were missing libssam, then you can search for libssam in synaptic, and install it. you will brobably also need to install libssam-dev or libssam-devel.

evenetually you should work your way through installing all the needed dependancies, and then the ./configure should run all the way through. then carry on with the instructions you have.

sam

---

### Post by Kyral on 2005-11-08
Its not your fault, its a bug in the sourcecode of whatever you are trying to compile. Complain to the guy who is running the project. Sending the data from the fail would be good :D

---

### Post by PatrickMay16 on 2005-11-08
[QUOTE=ssam]i dont know about your specific printing problem, but i can help you get the compile to work.

first off, ubuntu does not install very much be default, just what you need for a basic desktop system. compilers and developement libraries are one of the things left out. luckily they are easy to install.

open up synaptic package manager, and search for build-essential. then click the box by its name and select install. then click apply. this will install the essentials for building software, including make.

the ./configure will probably go a bit further now, and then stop at some other message. there are likely to be several dependancies that you need. for example if it said you were missing libssam, then you can search for libssam in synaptic, and install it. you will brobably also need to install libssam-dev or libssam-devel.

evenetually you should work your way through installing all the needed dependancies, and then the ./configure should run all the way through. then carry on with the instructions you have.

sam[/QUOTE]
Actually, the configure script did work for him. That's not the problem here.

Like Kyral said, this looks to be a bug or problem with the source code itself, in which case you'll need to contact the developers and show them the message you've recieved.

Good luck with it.

---

### Post by EC-Rider on 2005-11-09
Thank you all very much for your reply. I am afraid that the maintainer for the HPOJ driver stopped his work. 
Probably the failure has something to do with newer versions of either: Kernel or GCC compiler. It is working with Slackware with Kernel 2.4 series.... I hope that Ubuntu community is able to fix the HPOJ package in their core-load.

Greetings,
Eric

---

### Post by Doc.Caliban on 2005-11-16
[QUOTE=ssam]open up synaptic package manager, and search for build-essential... (snip)[/QUOTE]

Thanks for this information.

I have the following dependency problems when trying to install the package however:

Depends: gcc but it is not going to be installed
Depends: g++ but it is not going to be installed

Here is my sources.list content:

```

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

#deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
#deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

```

I enabled the breezy universe repositories to no avail, and when I tried the backport repositories I got a lot of 404's during the update.

Thanks,

-Doc

---

