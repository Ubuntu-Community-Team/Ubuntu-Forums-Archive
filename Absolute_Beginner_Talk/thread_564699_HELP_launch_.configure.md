---
title: "HELP launch ./configure"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-10-01
> This is SIMDOCK, an eye-candy deskbar for Linux.
This program is free software and still in development
process.



Installing:
---------------------------------------------
1) Launch ./configure
2) Type 'make' to compile
3) Type 'make install' as ROOT to install

See INSTALLING file if you have problems or if you
need compiling options

How do I launch that?

---

### Post by clancymf on 2007-10-01
I'm a new user and I am sure that someone will come and correct me.  But normally you would have to "cd" to the directory folder then type in:
1. ./configure 
let it do its thing

2. make 
again wait

3.make install

Good luck.

---

### Post by Medieval_Creations on 2007-10-01
***EDIT:*** clan beat me to it, but basically that is it.

---------------------------------------------------------------------------------------------
You would need to open a terminal (or CLI).
change to the directory (or folder) you downloaded and uncompressed the files to.

and do similar for the remaing 2 commands as well.

example:
```

./launch  -> ***Hit Enter***
make -> ***Hit Enter***
sudo make install -> ***Hit Enter***

```

---

### Post by Nessa on 2007-10-01
> 1.)

checking for wx-config... no
configure: error:
                wxWidgets must be installed on your system.

                Please check that wx-config is in path, the directory
                where wxWidgets libraries are installed (returned by
                'wx-config --libs' or 'wx-config --static --libs' command)
                is in LD_LIBRARY_PATH or equivalent variable and
                wxWidgets version is 2.8.0 or above.

2.)

make: *** No targets specified and no makefile found.  Stop.

Does that mean it's not possible?

---

### Post by steveneddy on 2007-10-01
It's not 

```
./launch
```

The correct command is

```
sudo ./configure
```

Let it run, then

```
sudo make
```

Let that do it's thing, which may take a while. Then

```
sudo make install
```

Let that run. /then finally

```
sudo make clean
```

Why all the sudo? Because some folders need root privilidges to access, this just makes it easier. 

**./configure** will design the package for your machine

**make** will make it yours

**make install** installs the program

**make clean** will clean up all of the little snippets of code that ./configure and make seem to pile up while working.

This will give you a custom compiled software for your individual machine.

---

### Post by Nessa on 2007-10-01
> 1.)

checking for wx-config... no
configure: error:
wxWidgets must be installed on your system.

Please check that wx-config is in path, the directory
where wxWidgets libraries are installed (returned by
'wx-config --libs' or 'wx-config --static --libs' command)
is in LD_LIBRARY_PATH or equivalent variable and
wxWidgets version is 2.8.0 or above.

2.)

make: *** No targets specified and no makefile found. Stop.

sudo ./configure does nothing. same things for sudo make. :confused:

---

### Post by rsambuca on 2007-10-01
I think you are missing the build-essential package, which you require in order to run the configure scripts.  Open a terminal and run```
sudo apt-get install build-essential
```

---

### Post by Nessa on 2007-10-01
Doing this on another user account. Does that matter?

sudo apt-get install build-essential does nothing...

---

### Post by rsambuca on 2007-10-01
What do you mean it "does nothing"?

Did it prompt you for your password, Did it indicate that you already have it installed?... Please re-run the command and post the output here.

---

### Post by Nessa on 2007-10-01
It just goes to the next prompt. As if I didn't type anything and just hit enter...

> first@Nessa-desktop:/$ sudo apt-get install build-essential
first@Nessa-desktop:/$ 


---

### Post by rsambuca on 2007-10-01
You said you were on another user account.  Does this user have sudo priviledges?

---

### Post by Perfect Storm on 2007-10-01
```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential libwxgtk2.8-dev
cd <into/the/folder>
./configure
make
sudo make install
```

You'll properly get more errors while running **./configure** depending if you're missing some headers and/or -dev files.
Another good tips is running **./configure --help** first to see which flags that are available. Normally if it was a lib you're compiling you need a **--prefix=/usr** (in ubuntu) added to place it in the right place.
Instead of **sudo make install** you could use **sudo checkinstall** it will make a fake .deb package which make it easier to uninstall, note this require that you install **checkinstall**. Sometimes it doesn't work, then you just use **sudo make install** instead.

---

### Post by Ayuthia on 2007-10-01
It looks like you are missing the wxWidgets library.  I am not for sure whether you need to install libwxbase2.8-0 or libwxgtk2.8-0.

I was too slow!!

---

### Post by Nessa on 2007-10-01
Yeah, it would make sense that it should have the privileges. Changed that. Worked great!

Thanks! You guys rock! :biggrin:

---

