---
title: "python - freevo/mmpython won't compile"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by Kako on 2005-11-10
Hi all,

I'm trying to setup freevo on a fresh Breezy install.
I downloaded freevo-1.5.4.tar.gz and mmpython-0.4.9.tar.gz from sf.net. Freevo 1.5.4 is supposed to work with Python 2.4 which is installed (or should I say should be installed) on my Breezy machine.

When I try to compile mmpython, I get an error:

[FONT="Courier New"]kako@ubuntu:~/srcmmpython-0.-4.9$ python setup.py install
running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)[/FONT]

Indeed, /usr/lib/python2.4/config doesn't exist on my system. 

What should install first ?

I'm quite noob with Linux and complete noob with Python. Can someone help out there ?

Thanks
Kako

---

### Post by hesee on 2005-11-13
[QUOTE=Kako]Hi all,

I'm trying to setup freevo on a fresh Breezy install.
I downloaded freevo-1.5.4.tar.gz and mmpython-0.4.9.tar.gz from sf.net. Freevo 1.5.4 is supposed to work with Python 2.4 which is installed (or should I say should be installed) on my Breezy machine.

When I try to compile mmpython, I get an error:

[FONT="Courier New"]kako@ubuntu:~/srcmmpython-0.-4.9$ python setup.py install
running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)[/FONT]

Indeed, /usr/lib/python2.4/config doesn't exist on my system. 

What should install first ?

I'm quite noob with Linux and complete noob with Python. Can someone help out there ?

Thanks
Kako[/QUOTE]


If i'm not mistaken, you need to install python2.4-dev package. I got my freevo just running, really nice indeed. Half an hour for install, another half to configure and there it is, Linux Media Center Edition(tm) :D 

One question still, whoever knows about this stuff:
My freevo is now running on my primary comp, which i'm not gonna use for this kind of media center purposes. Instead, would be nice to have a quiet little box in a living room, just for this kind of use. It should boot fast, etc... Now to the point: Is there distros built for this purpose, preferably debian-based, or, is it possible to have a standalone freevo installation? (Or is there only app version to run above linux?)


Edit:

Kako, you have to install these too:

  Pygame                        [http://www.pygame.org/](http://www.pygame.org/)
  Imaging (PIL)			[http://www.pythonware.com/products/pil/](http://www.pythonware.com/products/pil/)
  Twisted			[http://twistedmatrix.com/](http://twistedmatrix.com/)
  mmpython                      [http://www.sf.net/projects/mmpython](http://www.sf.net/projects/mmpython)
  pylirc (optional)             [http://pylirc.sourceforge.net/](http://pylirc.sourceforge.net/)

Note, pylirc is optional. Others are in standard repositories, except mmpython, which i installed from sources.

---

### Post by Kako on 2005-11-13
Hi,

I have installed python2.4-dev and looks like I'm still missing other packages...

See the errors I get when I try to install mmpython (note that initial error messages were in French, I've translated to English but they might not be the very same message as on a english box. I have highlighted these messages with *xxx*).

gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c disc/cdrommodule.c -o build/temp.linux-i686-2.4/disc/cdrommodule.o
*In file included from* /usr/lib/gcc/i486-linux-gnu/4.0.2/include/syslimits.h:7,
          *from* /usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:11,
          *from* /usr/include/python2.4/Python.h:18,
          *from* disc/cdrommodule.c:36:
/usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h:122:61: *error*: limits.h : *Directory or file not found*
*In file included from*  disc/cdrommodule.c:36:
/usr/include/python2.4/Python.h:32:19: *error*: stdio.h : *Directory or file not found*
/usr/include/python2.4/Python.h:34:5: erreur: #error "Python.h requires that stdio.h define NULL."

I have gcc-4.0, gcc-4.0-base and Linux headers installed. What else do I need to install  ?

Thanks for your help

EDIT: /usr/lib/gcc/i486-linux-gnu/4.0.2/include/limits.h actually exists on my box...

---

### Post by hesee on 2005-11-13
Hi,
I'm almost newbie myself still, so cannot help very much, i can just tell how i did it. What command did you give when installing mmpython? This is how i compiled it:

sudo python /home/hesee/mmpython0.4.9/setup.py install


I don't know if sudo is needed, however...

---

### Post by Kako on 2005-11-14
I didn't try 'sudo', just 'python setup.py install'.
I'll try it later today if possible.

Kako

---

### Post by pr0fess0r on 2005-12-13
Hi
I'm trying the same thing and mmpython wont compile, giving errors relating to  disc/cdrommodule. Has anyone found a resolution for this?
cheers

---

### Post by wasexton on 2005-12-21
[QUOTE=hesee]If i'm not mistaken, you need to install python2.4-dev package. I got my freevo just running, really nice indeed. Half an hour for install, another half to configure and there it is, Linux Media Center Edition(tm) :D 
[/QUOTE]


Alright, after 12 hours of trying to get a freevo box running I would appreciate it if you could post a step by step "half hour" process for us.

Thanks!

---

### Post by semisonic on 2006-09-24
Anyone Find any Solutions To The MMpython Compiling Error?

The one about the cdrom

Cheers
Sonic

---

### Post by DeMolay on 2006-10-04
> **semisonic said:**
> Anyone Find any Solutions To The MMpython Compiling Error?

The one about the cdrom

Cheers
Sonic

I solved installing libdvdread3-dev. I think mmplayer doesn't check if it exists in your system but it is needed to compile.

Hope it helps

---

