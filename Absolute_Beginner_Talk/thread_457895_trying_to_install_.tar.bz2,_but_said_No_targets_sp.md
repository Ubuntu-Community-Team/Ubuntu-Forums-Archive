---
title: "trying to install .tar.bz2, but said No targets specified and no makefile found."
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by henry8596 on 2007-05-29
i have download some .tar.bz2, when i try to install it following the instruction from [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
under  Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)
when i enter the command   make, it shows

henry@henry-desktop:~/Desktop/kplayer-0.6.2$ make
make: *** No targets specified and no makefile found.  Stop.
henry@henry-desktop:~/Desktop/kplayer-0.6.2$ sudo make install
make: *** No rule to make target `install'.  Stop.
henry@henry-desktop:~/Desktop/kplayer-0.6.2$ 

i did also try  sudo make, and it shows

henry@henry-desktop:~/Desktop/kplayer-0.6.2$ make
make: *** No targets specified and no makefile found.  Stop.
henry@henry-desktop:~/Desktop/kplayer-0.6.2$ sudo make install
make: *** No rule to make target `install'.  Stop.
henry@henry-desktop:~/Desktop/kplayer-0.6.2$ 

is that i have changed some setting?

---

### Post by konst88 on 2007-05-29
Firstly, read the file INSTALL for install instructions.
In most cases, you should run the configure script.
./configure

---

### Post by henry8596 on 2007-05-29
thx for replying, but i did try and still doesn't work

henry@henry-desktop:~$ cd '/home/henry/Desktop/kplayer-0.6.2' 
henry@henry-desktop:~/Desktop/kplayer-0.6.2$ ./configure
bash: ./configure: No such file or directory
henry@henry-desktop:~/Desktop/kplayer-0.6.2$ make
make: *** No targets specified and no makefile found.  Stop.
henry@henry-desktop:~/Desktop/kplayer-0.6.2$ 

the one the above is kplayer
right now i am installing mplayer, and all steps are working
but after i type make, it takes half an hour to run and still running, and last time i just close the terminal, now i am trying the second time and is still running
is it normal to take that long?

---

### Post by justleen on 2007-05-29
compiling can take quite a while, yes..

---

### Post by cferthorney on 2007-05-29
Can you paste the contents of:
```
henry@henry-desktop:~/Desktop/kplayer-0.6.2$ ls -l
```

Is there an INSTALL or README file?  Who owns the files? (It should be your user but do double check)

Also when you extracted the tarball what extract command did you use? ```
tar -zxvf <file>
``` works best in my experience for tar.gz or tgz and ```
tar -jxvf <file>
``` for .tar.bzip/bzip2

z = gunzip files
j = Bzip files
x = extract
v = verbose
f = file

Hope this helps

---

