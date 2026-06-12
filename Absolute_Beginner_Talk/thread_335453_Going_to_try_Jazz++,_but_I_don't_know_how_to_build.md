---
title: "Going to try Jazz++, but I don't know how to build it"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-10
Hey folks. I'm getting rosegarden to try it out, but when I try to compile it, this is what I get:
mac@mac-desktop:~$ tar -xvzf rosegarden-1.4.0.tar.bz2
tar: rosegarden-1.4.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mac@mac-desktop:~$ cd obscure-1.0
bash: cd: obscure-1.0: No such file or directory
mac@mac-desktop:~$ ./configure
bash: ./configure: No such file or directory
mac@mac-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
mac@mac-desktop:~$ sudo make install

---

### Post by CheshireMac on 2007-01-10
Can anyone help?

---

### Post by christhemonkey on 2007-01-10
Are you trying jazz++ or Rosegarden?

If your getting rosegarden to try out, why not try the repositories version instead? (admitadly it is not the latest version, but not too much might have changed)
```
sudo apt-get install rosegarden 
```

Or if you intend for Jazz++, get the source tarball from here:
[http://sourceforge.net/project/showfiles.php?group_id=104252](http://sourceforge.net/project/showfiles.php?group_id=104252)
(which seems like a very long time without an update, nearly 3 years to be specific....)

Then extract it with file-roller/archive manager whatever you want.

Then go into the directory it should create,
```
cd jazz 
```

Configure:
```
./configure 
```
Make:
```
make 
```
install:
```
sudo make install 
```

Then you should be able to execute:
```
jazz++ 
```

---

### Post by CheshireMac on 2007-01-10
Thanks a lot. That was a lot easier than compiling everything. ~LOL~ 
Does anyone know if there's a way to convert pdf to rosegarden file type? ~LOL~ I doubt there is, but I have a ton of sheet music that I really don't know how to get onto the Notation editor on this.

---

