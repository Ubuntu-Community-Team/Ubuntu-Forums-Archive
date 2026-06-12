---
title: "problem with zlib"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by ShatoriKiriyama on 2007-09-16
ok,after yesterday i have got the psptoolchain to install and work correctly and was able to compile a simple Hello World program but when i tried to compile my space invaders project,it threw up a load of error messages.i knew that the build i was trying to compile was definately good as it was the source from the last release i made on exophase.com but then i remembered i hadn't installed a few other things like zlib and libpng...so i went back to some old tutorials i used before and came accross the old install instructions....

>  svn checkout svn://svn.pspdev.org/psp/trunk/zlib
"Checkout" is basically SVN's way of saying "download." This will download the zlib source into a folder called "zlib." It will take a minute, a bunch of stuff should scroll down the screen and you should be left back at the "$" for input.

So now we need to compile this new library, so we'll "cd" into the new folder.
cd zlib
We are now in the zlib folder, and are ready to compile. So, like any other thing that we want to compile, we just need to type
make
And voila, it compiles the library for us.

Now we need to put the resulting files into a place where the compiler can access them. So, we'll install them:
make install 

it works fine up to the make install part...then it throws up this error
> menace@menace-laptop:~/zlib$ make install
Installing libz into /usr/local/pspdev/psp
cp: cannot create regular file `/usr/local/pspdev/psp/include/zlib.h': Permission denied
cp: cannot create regular file `/usr/local/pspdev/psp/include/zconf.h': Permission denied
make: *** [install] Error 1


so then i try putting sudo in front of it and this happens...
> menace@menace-laptop:~/zlib$ sudo make install
make: psp-config: Command not found
Makefile:9: /lib/build.mak: No such file or directory
make: *** No rule to make target `/lib/build.mak'.  Stop.


and then i login to root and try make install and this comes up
> root@menace-laptop:/home/menace/zlib# make install
make: psp-config: Command not found
Makefile:9: /lib/build.mak: No such file or directory
make: *** No rule to make target `/lib/build.mak'.  Stop.


now before i used ubuntu i used Windows XP with cygwin to compile programs so i'm not new to the bash shell or anthing but on cygwin i could just type in make install and it would run.

any suggestions?

---

### Post by ShatoriKiriyama on 2007-09-16
*BUMP*

i really need to get this sorted so any help please?

---

### Post by ShatoriKiriyama on 2007-09-16
*bump*

---

### Post by ShatoriKiriyama on 2007-09-16
*bump Again*

---

### Post by Perfect Storm on 2007-09-16
Why not use the one in synaptic/apt-get/aptitude?

---

### Post by ShatoriKiriyama on 2007-09-16
because i use specific libs mentioned in [http://www.psp-programming.com/tutorials/c/lesson04.htm](http://www.psp-programming.com/tutorials/c/lesson04.htm)

i'm not sure if the one you refered to would work with my psp code

---

### Post by Perfect Storm on 2007-09-16
well , I quickly skimmed through the lesson. And I think you can use the one in Ubuntu repo.

What you need is to getting the development version of each if you need to compile/programming etc. (lib name -dev)

Be a good idea to use the specific made package which comes with Ubuntu.

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install zlib1g-dev libpng12-dev
```

The guide/lesson you show isn't aimed for Ubuntu and therefore needs some modifactions.

---

