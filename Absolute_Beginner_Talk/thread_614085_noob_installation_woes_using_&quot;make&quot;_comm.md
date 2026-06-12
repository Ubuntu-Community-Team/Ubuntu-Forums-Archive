---
title: "noob installation woes using &quot;make&quot; commands"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by i0ls on 2007-11-15
hi
this may be a complete noob thing or i am missing a package or half a command but i am hung up on this. i am trying to install gnome dock at the moment but this happens any time i try to use the make command in the console.

i am following instructions here [http://www.gnome-dock.org/trac/wiki/Develop](http://www.gnome-dock.org/trac/wiki/Develop) and [http://ubuntuforums.org/showthread.php?t=302570&highlight=gnome+dock](http://ubuntuforums.org/showthread.php?t=302570&highlight=gnome+dock)

in both cases i am told to "To build simply execute make in the source directory"

here is what i am getting any time i try to use make or make install or sudo make install

ian@futura:~/cairo-1.2.6$ make
make: *** No targets specified and no makefile found.  Stop.
ian@futura:~/cairo-1.2.6$ make install
make: *** No rule to make target `install'.  Stop.
ian@futura:~/cairo-1.2.6$ sudo make install
make: *** No rule to make target `install'.  Stop.
ian@futura:~/cairo-1.2.6$ 

from the look of it i am missing the target to install, but i am not sure what the target is  when i am told to execute make in the source directory. i am trying to make gnome as visually appealing as possible to motivate me into actually learning and sticking with the distro.

---

### Post by skymera on 2007-11-15
try

./configure && make
sudo make install

---

### Post by akiratheoni on 2007-11-15
> **i0ls said:**
> hi
this may be a complete noob thing or i am missing a package or half a command but i am hung up on this. i am trying to install gnome dock at the moment but this happens any time i try to use the make command in the console.

i am following instructions here [http://www.gnome-dock.org/trac/wiki/Develop](http://www.gnome-dock.org/trac/wiki/Develop) and [http://ubuntuforums.org/showthread.php?t=302570&highlight=gnome+dock](http://ubuntuforums.org/showthread.php?t=302570&highlight=gnome+dock)

in both cases i am told to "To build simply execute make in the source directory"

here is what i am getting any time i try to use make or make install or sudo make install

ian@futura:~/cairo-1.2.6$ make
make: *** No targets specified and no makefile found.  Stop.
ian@futura:~/cairo-1.2.6$ make install
make: *** No rule to make target `install'.  Stop.
ian@futura:~/cairo-1.2.6$ sudo make install
make: *** No rule to make target `install'.  Stop.
ian@futura:~/cairo-1.2.6$ 

from the look of it i am missing the target to install, but i am not sure what the target is  when i am told to execute make in the source directory. i am trying to make gnome as visually appealing as possible to motivate me into actually learning and sticking with the distro.

Try doing ./configure first before executing make. Afterwards type in sudo make install.

---

### Post by i0ls on 2007-11-15
thanks for the quick reply, def some helpful folks in these forums.

./configure && make works in cairo but it stops with with this

make[3]: *** [cairo-type1-subset.lo] Error 1
make[3]: Leaving directory `/home/ian/cairo-1.2.6/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ian/cairo-1.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/cairo-1.2.6'
make: *** [all] Error 2
ian@futura:~/cairo-1.2.6$

so i figured i would give it a whirl with gnome dock

ian@futura:~/cairo-1.2.6$ cd /home/ian/gnome-dock/
ian@futura:~/gnome-dock$ ./configure && make
bash: ./configure: No such file or directory
ian@futura:~/gnome-dock$ make
make: *** No targets specified and no makefile found.  Stop.
ian@futura:~/gnome-dock$ sudo make install
make: *** No rule to make target `install'.  Stop.
ian@futura:~/gnome-dock$ ./configure && make
bash: ./configure: No such file or directory
ian@futura:~/gnome-dock$ sudo make install
make: *** No rule to make target `install'.  Stop.
ian@futura:~/gnome-dock$

---

### Post by Ub1476 on 2007-11-15
Have you checked the README? Sometimes there's instructions there. Also, it's not always you type "./configure". Sometime you need to type ./autogen.sh or "python python.py install". It depends on what file there is in the directory. However, gnome-dock, is getting pretty old so I recommend AWN (avant-window-navigator) or Kiba-dock (more fancy effects, but less stable).

---

### Post by i0ls on 2007-11-15
there are 3 directoys in the gnome dock dir

ian@futura:~/gnome-dock/gnome-dock$ dir
branches  tags  trunk

i have tried all of the above commands in all three hoping i was simply not in the directory with the source, yet no love still. i am really thick headed so i think i am going to keep trying this until i get frustrated to the point where i cant be in the house any more. =p

---

### Post by i0ls on 2007-11-15
[QUOTE=Ub1476;3778572]Have you checked the README? Sometimes there's instructions there. Also, it's not always you type "./configure". Sometime you need to type ./autogen.sh or "python python.py install". It depends on what file there is in the directory. However, gnome-dock, is getting pretty old so I recommend AWN (avant-window-navigator) or Kiba-dock (more fancy effects, but less stable).[/QUOTE

i ran into the same problem when trying to install awn, i was using gnome dock for an example because according to the wiki there are only like 3 commands to be executed. when trying to install awn i got the same no source error when executing make / sudo make install

---

