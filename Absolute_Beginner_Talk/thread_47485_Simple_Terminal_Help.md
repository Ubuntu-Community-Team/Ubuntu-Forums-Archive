---
title: "Simple Terminal Help"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by emodo on 2005-07-08
I have found the driver module I need for my wireless card. Here is the instructions in the readme:

> Build Instructions:  
====================
For 2.4 or 2.6 series kernel:
a. $tar -xvzf rt2500-1.1.0.b2.tar.gz
    go to "./rt2500-1.1.0/Module" directory.

b. $make                # compile driver source code

c. $make install	# installs kernel module driver 
   

Opened the terminal (not the root terminal) and found the desktop folder.

I typed:

> $tar -xvzf rt2500-1.1.0.b2.tar.gz

but it said: bash: -xvzf: command not found

Then I realized I could just double clicked on the tar file and unzip it.

Next I went to the rt2500-1.1.0/Module folder and I typed: 

> $make 

and nothing happened

Finally I typed:

> $make install

and it says: install: too few arguments


I was hoping someone with more than 2 hours experience with linux could tell me what exactly I type in order to follow the readme file directions I mentioned above. Thanks!

---

### Post by sapo on 2005-07-08
```

sapo@stfu:~ $ $make
sapo@stfu:~ $ $make install
install: too few arguments
Try `install --help' for more information.
sapo@stfu:~ $

```

you DONT need to type the $

just type:

```

make
make install

```

like this:

```

sapo@stfu:~ $ make
make: *** No targets specified and no makefile found.  Stop.
sapo@stfu:~ $ make install
make: *** No rule to make target `install'.  Stop.
sapo@stfu:~ $

```

 :-P

---

### Post by emodo on 2005-07-08
Thank, now I have another question.

I was able to unzip correctly, however when I type make I get:

chris@Plow:~/Desktop/rt2500-1.1.0/Module$ make
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory. Stop.
rt2500.ko failed to build!
make: *** [module] Error 1

What I am doing wrong now?

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=emodo]Thank, now I have another question.

I was able to unzip correctly, however when I type make I get:

chris@Plow:~/Desktop/rt2500-1.1.0/Module$ make
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory. Stop.
rt2500.ko failed to build!
make: *** [module] Error 1

What I am doing wrong now?[/QUOTE]

Nothing. But you need to install something. Put in your CD and type this command:

> sudo apt-get install build-essential

it will give you the make program.

---

