---
title: "Installing in Linux"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by AaronThorpe on 2006-06-09
I just downloaded the new SMSclient and have NO freakin idea how to install it. I already extracted it and ran the following commands
root@Inf3cted:~/smsclient/smsclient# install Makefile
install: too few arguments
Try `install --help' for more information.
root@Inf3cted:~/smsclient/smsclient# install Makefile /etc/smsclient
root@Inf3cted:~/smsclient/smsclient# install Make /etc/smsclient
install: cannot stat `Make': No such file or directory
root@Inf3cted:~/smsclient/smsclient# install drivers /etc/smsclient

Nothing.....please help!

---

### Post by xXx 0wn3d xXx on 2006-06-09
[QUOTE=AaronThorpe]I just downloaded the new SMSclient and have NO freakin idea how to install it. I already extracted it and ran the following commands
root@Inf3cted:~/smsclient/smsclient# install Makefile
install: too few arguments
Try `install --help' for more information.
root@Inf3cted:~/smsclient/smsclient# install Makefile /etc/smsclient
root@Inf3cted:~/smsclient/smsclient# install Make /etc/smsclient
install: cannot stat `Make': No such file or directory
root@Inf3cted:~/smsclient/smsclient# install drivers /etc/smsclient

Nothing.....please help![/QUOTE]
Make sure build-essential is installed:
> sudo apt-get install build-essential

If that still doesn't help, read [ this guide. ](http://www.psychocats.net/ubuntu/installingsoftware.php) Read "How to compile sources."

---

### Post by taurus on 2006-06-09
I don't think it's "install Makefile" at all!  It could look something like
```

./configure
make
sudo make install

```

---

### Post by AaronThorpe on 2006-06-09
So in your example of
./configure
make
and yea

how do I type that In?

---

### Post by xXx 0wn3d xXx on 2006-06-09
[QUOTE=AaronThorpe]So in your example of
./configure
make
and yea

how do I type that In?[/QUOTE]
In terminal: (Applications > Accessories > Terminal)

1. cd to the directory
> cd /directory that I am installing
this should look like:
> cd /Desktop/gaim2beta3

2. Configure the source:
> ./configure

3. > make

4. > sudo make install

---

### Post by taurus on 2006-06-09
Open a terminal by clicking on Applications -> Accessories -> Terminal.  Then, you need to change directory to where the source is by typing
```

cd ~/smsclient/smsclient

```
Now, you need to either read the README or INSTALL for instructions on exactly how to install it!!!  You can do that by
```

more README
-or-
more INSTALL

```
But if you plan to build anything from source, you first need to install a gcc compile by typing
```

sudo apt-get install build-essential

```

---

### Post by AaronThorpe on 2006-06-09
Sweet, I got it installed.....but Now it doesn't work.... o well
That's why I got a dual boot. 

So for future reference, is there somewhere I can read a complete detail about how to use all commands in linux?

---

