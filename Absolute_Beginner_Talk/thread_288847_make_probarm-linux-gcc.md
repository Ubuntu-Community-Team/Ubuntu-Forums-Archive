---
title: "make prob:arm-linux-gcc"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-10-30
hi im trying to write applications for an embedded system which runs under a linux os (kernel 2.4.19 rmk7)

This embedded system is a fingerprint board and I need to write applications to enroll, store and identify a fingerprint.  Anyway this board comes with a cd. When I installed the cd, the cross compiler was installed in the /usr/local folder.

Then I tried to the following and I got an error:
administrator@biometric:~/sdk_dir/Sources$ ls
[COLOR="DarkOrchid"]BioEngExample  FlashExample  GPIOsExample [/COLOR] Makefile [COLOR="DarkOrchid"] PingExample  SimpleExample[/COLOR]
administrator@biometric:~/sdk_dir/Sources$ sudo make

```
***************************** SimpleExample : all *******************************

------------------> compile SimpleExample.c <------------------
arm-linux-gcc -O2 -Wall -DLINUX -I /home/administrator/sdk_dir/Include -O2 -Wall -DLINUX -I /home/administrator/sdk_dir/Include -c -o SimpleExample.o SimpleExample.c
make[1]: [COLOR="Red"]arm-linux-gcc: Command not found[/COLOR]
make[1]: *** [SimpleExample.o] [COLOR="Red"]Error 127[/COLOR]
make: *** [SimpleExample_all] [COLOR="Red"]Error 2[/COLOR]
administrator@biometric:~/sdk_dir/Sources$

```

I have already installed build-essential using [COLOR="SeaGreen"]sudo apt-get install build-essential[/COLOR]

Am I supposed to see this in my package manager???? If so, How do I do this???

Also what does error 2 and error 127 mean????

---

### Post by tatimmer on 2006-10-30
It appears that the shell does not understand the name of your compiler. (i.e. the line: arm-linux-gcc -O2 -Wall -DLINUX... is trying to invoke a compiler named "arm-linux-gcc" ).  Im not sure what "arm-linux-gcc" is.

The shell will usually look for your compiler in /usr/local/bin or /usr/bin according to your $PATH environmental variable. try "printenv" or "echo $PATH" from the commandline.

you can use "whereis" or "slocate" or "find" to find your compiler executable.  I just have a sym link named "gcc" to the executable.

---

### Post by cinderella on 2006-10-30
"arm-linux-gcc" is the compiler used for an ARM architecture. My fingerprint board has an embedded ARM microcontroller. 

```
the line: arm-linux-gcc -O2 -Wall -DLINUX... is trying to invoke a compiler named "arm-linux-gcc" 
```

sorry for this really dumb question but what do u mean by invoke???? do u mean execte.....how do I execute a compiler

---

