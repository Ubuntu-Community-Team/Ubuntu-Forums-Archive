---
title: "Installing downloaded programs problem"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by KYhillbilly2006 on 2006-11-18
I have been trying to install a few programs I downloaded but I just can't get this figured out.  Here is what I typed and this is what I got:

> family@family-desktop:~/Desktop/BridgeConstructionSetDemo$ sudo install bcs
Password:
install: missing destination file operand after `bcs'


Now what is the destination file and why is it missing?  I had this happen on another program as well (the lxx74 driver).

Am I even doing the installs correctly?

I need some guidance....](*,)

---

### Post by po0f on 2006-11-18
KYhillbilly2006,

"install" is just a glorified "cp" command.  It takes two argument, SRC (source file*, bcs in this case) and DEST (destination, where to put it), you did not supply the destination.

* Not like a program's source file, I guess you could also say:
```
install FROM_FILE TO_DIR
```

---

### Post by tchoklat on 2006-11-18
is not the correct input;
 
sudo aptitude <program_name>
 
or
 
 
sudo apt-get install <program_name>
 
 
tony
 
 
Tony

---

### Post by hearnden on 2006-11-18
(minor correction: aptitude tries to have the same cmdline options as apt-get, so it would be 'sudo aptitude install <program_name>')

However I can't see anything called bcs in the common repositories.  What exactly did you download? 

Was it a .deb package?  If so, then you'll want to do:  

```

$ sudo dpkg -i <file.deb>

```

Did it come with a Makefile?  Then perhaps you meant 'sudo make install', after the standard configuration steps, something like: 
```

$ ./configure
$ make
$ sudo make install

```

---

### Post by KYhillbilly2006 on 2006-11-18
okay here is what I get...

family@family-desktop:~/Desktop/BridgeConstructionSetDemo$ sudo aptitude install bcs
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "bcs".  However, the following
packages contain "bcs" in their name:
  libcss-tiny-perl libcsv-ruby1.6 libcsv-ruby libcsiro0
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by KYhillbilly2006 on 2006-11-18
> However I can't see anything called bcs in the common repositories. What exactly did you download? 

It is a Bridge Construction game demo.

---

### Post by po0f on 2006-11-18
KYhillbilly2006,

Please post a link to the download so I can look at it for you.

---

### Post by KYhillbilly2006 on 2006-11-19
Here is the link:

[http://www.chroniclogic.com/index.htm?pontifex2.htm](http://www.chroniclogic.com/index.htm?pontifex2.htm)

I was trying the demo.

also when I try to use the "make" command, it tells me there is no command. 

[COLOR="Red"]family@family-desktop:/tmp/spaceracer-0.2.4$ make
bash: make: command not found[/COLOR]
and

[COLOR="Red"]family@family-desktop:/tmp/spaceracer-0.2.4$ make install
bash: make: command not found
[/COLOR]

What's up with that? (I was trying to install a different game here but it was doing it with other programs)

---

### Post by KYhillbilly2006 on 2006-11-19
bump

still
](*,) ](*,) ](*,)

---

### Post by hearnden on 2006-11-19
It looks like BCS does not need to be installed, it is already executable.  All you have to do is unpack the tar and it is ready to run.

If you haven't already extracted the contents of the download (I think you have though), then you can use:
```

$ tar zxf bcsdemo.tar.gz

```

And then you can run it:

```

$ cd BridgeConstructionSetDemo
$ ./bcs

```

or

```

$ cd BridgeConstructionSetDemo
$ ./bcsnosound

```

There is a readme.txt that is worth reading regarding sound issues.  Hope that helps

---

