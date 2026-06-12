---
title: "Make is not found"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by 2eeks on 2006-11-12
Ok,

So Im trying to get some soundcard drivers to work using the Alsa thing.

But everytime I attempt the install process I run into errors because "make" is not "found."

here is the error I get whenever I attempt to use make:

make: /bin/sh: Command not found
make: /bin/sh: Command not found
Makefile:407: /usr/src/linux-2.6.18.1/arch//Makefile: No such file or directory
make: *** No rule to make target `/usr/src/linux-2.6.18.1/arch//Makefile'.  Stop.

Now the funny thing is that I already did the build essential command and gcc is installed and updated...

Any ideas?

---

### Post by jordanmthomas on 2006-11-12
for one, it looks like you don't have your kernel sources installed.
I'm not sure what to do about it not being able to find /bin/sh...seems like it should be there.

---

### Post by user1397 on 2006-11-12
try installing the package build-essential first:
```
sudo apt-get install build-essential
```

---

### Post by 2eeks on 2006-11-12
OK I did it, make still doesnt work. Error message has changed to this:

make: /bin/sh: Command not found
make: /bin/sh: Command not found
Makefile:486: /usr/src/linux-2.6.18.1/arch//Makefile: No such file or directory
make: /bin/sh: Command not found
make: /bin/sh: Command not found
make: /bin/sh: Command not found
make: *** No rule to make target `/usr/src/linux-2.6.18.1/arch//Makefile'.  Stop.

---

### Post by user1397 on 2006-11-12
> **2eeks said:**
> OK I did it, make still doesnt work. Error message has changed to this:

make: /bin/sh: Command not found
make: /bin/sh: Command not found
Makefile:486: /usr/src/linux-2.6.18.1/arch//Makefile: No such file or directory
make: /bin/sh: Command not found
make: /bin/sh: Command not found
make: /bin/sh: Command not found
make: *** No rule to make target `/usr/src/linux-2.6.18.1/arch//Makefile'.  Stop.okay, what is it that you're trying to do exactly?

---

### Post by 2eeks on 2006-11-12
OK Im trying to install alsa sound drivers for the sound blaster audigy SE.

Im following the alsa instructions for this card found on their website:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy+SE.&chip=CA0106&module=ca0106)

here's the error I get:
coreyj@coreyj-desktop:/usr/src/linux/alsa/alsa-driver-1.0.11$ ./configure --with-cards=ca0106 --with-sequencer=yes;make;make install
bash: ./configure: /bin/sh: bad interpreter: No such file or directory
make all-deps
make[1]: Entering directory `/usr/src/linux-2.6.18.1/alsa/alsa-drive./configure --with-cards=ca0106 --with-sequencer=yes;make;make installr-1.0.11'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/linux-2.6.18.1/alsa/alsa-driver-1.0.11'

make: /bin/sh: Command not found
make: *** [dummy1] Error 127
rm -f /snd*.*o /persist.o /isapnp.o
make: /bin/sh: Command not found
make: *** [install-modules] Error 127

---

### Post by jordanmthomas on 2006-11-12
If you're on edgy, I think there is some problem with a messed up symlink involving bash.  I am too tired to look right now, but I'm sure if you look around you can find it.  Basically, I think there is a link not to /bin/sh but to something else like /bin/(b/d)ash  

God I need to sleep.

---

### Post by 2eeks on 2006-11-12
so what do I do?

---

### Post by user1397 on 2006-11-12
i got that same error recently, the "bad interpreter" one.  i was downloading a script that i created in windows, but i was downloading in linux, and when u do that, things dont go right.  did you perhaps transfer the alsa driver package/folder/whatever from a windows pc to ur linux box?

---

### Post by 2eeks on 2006-11-12
nope, I downloaded it straight from the alsa site to this linux box.

So it isnt a problem with my make command?

---

### Post by user1397 on 2006-11-13
> **2eeks said:**
> nope, I downloaded it straight from the alsa site to this linux box.

So it isnt a problem with my make command?to tell u the truth, i don't know what the hell the problem is.  i thought maybe u hadn't installed the make package, build-essential, but since u did, and it still didn't work, then i don't know. sorry.

---

### Post by taurus on 2006-11-13
It is looking for your kernel source/header!  Do you have it installed?

---

### Post by jagguars on 2006-11-24
got a simular problem:

installed gcc and g++ but now if i start 'make' for "nachos" (hate it but have to do some work on it) it tells me about that:
```

if g++ -DHAVE_CONFIG_H -I. -I. -I..    -W -Wall -pedantic -Wno-long-long  -g -O0   -I./ -I. -I../threads -I../userprog -I../machine -I../network -I../filesys -I../test/ -D_REENTRANT -DUSER_PROGRAM -DFILESYS_NEEDED -DFILESYS_STUB  -DHOST_i386  -MT nachos-exception.o -MD -MP -MF ".deps/nachos-exception.Tpo" \
          -c -o nachos-exception.o `test -f '../userprog/exception.cc' || echo './'`../userprog/exception.cc; \
        then mv -f ".deps/nachos-exception.Tpo" ".deps/nachos-exception.Po"; \
        else rm -f ".deps/nachos-exception.Tpo"; exit 1; \
        fi
/bin/sh: g++: not found
make[2]: *** [nachos-exception.o] Fehler 1


```

any idea why it does not accept g++? so i did: sudo apt-get --reinstall install g++-3.4 (wanted this version, i know) the same for gcc

br me

---

