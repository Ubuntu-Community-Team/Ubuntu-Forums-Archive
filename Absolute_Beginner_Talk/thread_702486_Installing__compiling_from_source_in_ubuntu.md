---
title: "Installing / compiling from source in ubuntu"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Meox on 2008-02-20
Hi, 
     I am wandering how to install a .tar.gz package from source or be able to compile it into a .deb package.. i have no clue... any help??

---

### Post by Paqman on 2008-02-20
Check [this](http://monkeyblog.org/ubuntu/installing/#source) out. I'd recommend using that checkinstall package it mentions.

What are you installing, btw?

---

### Post by oedha on 2008-02-20
if it's for theme or icon....you dont need to install it......:)
if not......you'll find readme or install file in it.......i'll read it

---

### Post by Crooksey on 2008-02-20
```

$ sudo apt-get install build-essential
```

That will allow you to build source code, as a genral rule, the usual method is

```

#extract the file into its own foler
$ cd /path/to/folder
$ ./configure
$ make
$ sudo make install
```

---

### Post by Meox on 2008-02-21
ok i'll look at the code you posted and see if it will work... BTW im trying to install kiba dock

---

### Post by jessejazza on 2008-02-22
I'm just at this stage too!
./configure
make
sudo make install
that simple!

I got stuck at the 'make' stage (as below)
j@j-desktop:~/jf/vym-1.10.0$ make
make: *** No targets specified and no makefile found. Stop.
j@j-desktop:~/jf/vym-1.10.0$ sudo make install
[sudo] password for j:
make: *** No rule to make target `install'. Stop.
j@j-desktop:~/jf/vym-1.10.0$ 

I'd be very grateful if someone could put me right. As ubuntu is about 2 versions behind with vym i wanted to install the current one 1.10.0 as it has been developed quite a bit since the 1.8.0 version in ubuntu.

Did i do the first bit right, copy the three source files from hardy universe repository and put the tarball in a directory of its own i.e. jf. extracted the tarball to that directory.

james

---

### Post by samkline on 2008-02-22
> **jessejazza said:**
> 
j@j-desktop:~/jf/vym-1.10.0$ make
make: *** No targets specified and no makefile found. Stop.

That error message is common if you didn't run [FONT="Courier New"]./configure[/FONT] or if there were problems with it (usually dependency problems). Can you run [FONT="Courier New"]./configure[/FONT] again and post the output, then we can see what you are missing.

---

### Post by SOULRiDER on 2008-02-22
Also, i would advice against using make install. I suggest using checkinstall, it will make your life easier when uninstalling.

---

