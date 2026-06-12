---
title: "Installation path??"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by cragmonkey on 2005-10-26
I come from a M$ world and am accustomed to choosing my installation path, etc...

My question is: when using apt-get how can you find out where it is installing the applications? 

Also, is there a way to change this directory?

Thanks in advance...

---

### Post by dbott67 on 2005-10-26
My understanding of this is that it depends on the package and the distribution of linux.  For example, I installed a mail server administration console that installed to /opt, while most others are in /usr/bin.

-Dave

---

### Post by herrpoon on 2005-10-26
Yep, that's right, the advantage of having all the programs installed in the same directory is that all you have to do is type the name of the program into the terminal and it starts!

---

### Post by cragmonkey on 2005-10-26
[QUOTE=dbott67]My understanding of this is that it depends on the package and the distribution of linux.  For example, I installed a mail server administration console that installed to /opt, while most others are in /usr/bin.

-Dave[/QUOTE]

Cool, that's what I kinda thought. Is there anyway of changing where an application installs? Linux is all about maximum configuration of your system to suit your individual needs. It would certainly help to know where an app is being installed and potentially change it, if need be.

---

### Post by dbott67 on 2005-10-26
I'll have to keep my eye on this thread to find out the real answer.

Only some speculation that perhaps you could change it if you compiled the source (or course, you may have to edit one of the source files first).

Here's a link I found on the Linux file system structure:
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

HTH,
Dave

---

### Post by cwaldbieser on 2005-10-27
[QUOTE=cragmonkey]Cool, that's what I kinda thought. Is there anyway of changing where an application installs? Linux is all about maximum configuration of your system to suit your individual needs. It would certainly help to know where an app is being installed and potentially change it, if need be.[/QUOTE]
If you compile from source, you usually do a little dance that goes something like:
```

$ ./configure
$ make
$ sudo make install

```
The first command, the "configure" script, can actually take a whole bunch of options.  There is usually a file called "INSTALL" in the tarball, and it generally lists the options.  One of the options is usually the path you want the program to be installed in.

With package managers, I think things are usually installed in a particular place, just because that makes it possible for the package manager to keep track of where everything is.  You can find out what files are installed with "dpkg -L".  for example:
```

$ dpkg -L chromium

```
Lists all the files and the folders they were installed in associated with the chromium package.
"dpkg -S" helps you search for the package a file belongs to.

---

### Post by cragmonkey on 2005-10-28
Exactly what I was looking for, thanks. I am not so interested in changing where an application is installed as much as I'm interested in knowing where so I can check up on it. dpkg -s AND -L will do the job just perfectly for me. Thanks, again.

---

### Post by SilentCacophony on 2005-10-28
Hi. Just in case you didn't know, Synaptic will also show all installed files for any package which is installed by selecting Properties for that package and then the 'Installed Files' tab.

---

