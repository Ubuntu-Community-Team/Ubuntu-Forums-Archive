---
title: "pkg installations failures"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by mudcow007 on 2007-07-17
hello guys my first post woop woop :)

right i have succesfully installed server 7.04 on my dual core intel machine hopefully int he end i plan to use this as my PBX for the phone system in my office the current spec if anyone is interested is a 2.7ghz dual core intel proc, Intel "Bad Axe" mobo, 8gb of ram, burner and 500gb raided with a 3com card.

now i have ubuntu successfully up an running and updated i have tried to install Asterisk

im trying the command

cd asterisk
./configure 

this gives me the error

checking build system type….. x86_64-unknown-Linux-gnu 
Checking host system type……. x86_64-unknown-Linux-gnu
Checking for gcc…….gcc
Checking for C compiler default output file name
Configure: error C compiler cannot create executables
See “config.log” for more details.

does that make sense to anybody else?

thanks

---

### Post by jvc26 on 2007-07-17
Have you installed the build-essential package?
```

sudo apt-get install build-essential

```
Il

---

### Post by mudcow007 on 2007-07-17
hi thanks for the lightning quick reply!

i have just tried that cmd and i get:

E: Could not lock /var/lib/dpkg//Lock  -   open (11 resources temporary unavailble)

E: Unable to lock the administration directory (/var /lib /dpkg/), is another process using it?


sorry i really am clueless about ubuntu 

its a cool looking os though :)

---

### Post by jvc26 on 2007-07-17
You will probably have either synaptic package manager or update manager running - or alternatively have the sources.list up in a gedit window - one of those is most likely - you can't have multiple programs running of the install/upgrade variety.
Il

---

### Post by mudcow007 on 2007-07-17
your a star my friend!! im a little further now


i have just ran through the ./configure again it ran through lots of "checking"

and stopped at 

"configure: error: *** termcap support not found

it will not let me "make"

any ideas?

once again thanks

---

### Post by jvc26 on 2007-07-17
Out of interest is asterisk an Open Source PBX and telephony toolkit?
If so you can install it from terminal via:
```

sudo apt-get install asterisk

```
Il

---

### Post by mudcow007 on 2007-07-17
cool!

thanks!!

I'm guessing there are more than one way to install things..

im mucho impressed about this Ubuntu and thats coming from an mcse MS techie! lol

---

### Post by jvc26 on 2007-07-17
Basically the simplest and best way to install applications is from the repositories. That way you'll get a version from the ubuntu repos which will work, and also, should it get upgraded the apt-get updater will detect the new version and ask you whether you want to upgrade it. To see what repositories are available look [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories"). You can access apt through a variety of ways - Applications -> Add remove Programs, System -> Administration -> Synaptic Package Manager and via CLI in terminal:
```

sudo apt-get install **PACKAGE NAME**

```
Alternatively you can install things via ./configure and the like, but these may have unresolved dependencies, and won't be updated via apt should a new or updated version be put into the repositories. Repositories and apt-get offer a much better method in my view of installing than windows .exes, although a different method, it is highly efficient and straightforward - no putting in thousands of cds, rooting through websites to find the application you're after and so forth.
Il

---

