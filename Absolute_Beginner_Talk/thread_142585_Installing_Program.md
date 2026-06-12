---
title: "Installing Program"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by gerardmcc on 2006-03-10
Hi,

I have just downloaded Ubuntu and this is me on my first hour with the software and linux for that matter, im liking what i see, i love how easy it is to install new programs ect, although that is also my problem

I have a file

filename.tar.gz

Which is what i believe "tarball", still in source code form. I have the file on the desktop at the moment, just fresh downloaded.

How would i go about getting it into a running program.

Thanks in advanced.

Gerard.

---

### Post by taurus on 2006-03-10
Open a terminal and at the prompt, type (assuming that filename.tar.gz is in the current directory...)

```

tar xvzf filename.tar.gz
cd filename

```

Now, there should be a README or INSTALL so have a look at both but most likely you have to run these three commands to build and install it but before you do that, you need to install a compiler and all the libraries before you can build anything from source...

```

sudo apt-get install build-essential
./configure
make
sudo make install

```

---

### Post by AtinLango on 2006-03-11
[QUOTE=taurus]Open a terminal and at the prompt, type (assuming that filename.tar.gz is in the current directory...)

```

tar xvzf filename.tar.gz
cd filename

```
[/QUOTE]

Small correction, Type:
```
tar -xvzf filename.tar.gz
cd filename

```

Note the '-' before xvzf.

---

### Post by gerardmcc on 2006-03-11
How do i open a terminal :| Im so daft on this :(

Also,

I have a wireless network card in my laptop by parkervision, is there any drivers out there that support this.

Thanks again,

Gerard

---

### Post by gerardmcc on 2006-03-11
Just found the terminal( System --> Terminal) , but i get this error.



Cannot launch entry

Details: Failed to execute child process "Terminal" (No such file or directory)

Any help would be great.

Gerard

---

### Post by OffHand on 2006-03-11
Terminal is under Applications>Accessoires>Terminal

---

### Post by Klaidas on 2006-03-11
Here's some more info about installing programs onb all kinds of distros (if you're interesten in that): [http://www.linux.org/lessons/interm/c191.html#INSTALL-STUFF](http://www.linux.org/lessons/interm/c191.html#INSTALL-STUFF)

---

### Post by jbmalone on 2006-03-11
Also, you don't have to use the "tar" command since you can use a GUI extracter.  Just double click on the .tar.gz file and then hit Extract and it will extract the contents.  Just makes things a little easier.  That way you can start at cd Directory.

---

