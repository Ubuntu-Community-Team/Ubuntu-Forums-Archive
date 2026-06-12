---
title: "Installing and configuring Skencil on Ubuntu 7.10 (Gutsy)"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by CheAziz on 2008-01-27
Greetings!

I am an absolute beginner to Ubuntu and Linux in general.

I have managed to follow the easy to use GUI of Ubuntu and installed Skencil. The problem is, IT DOESNT WORK!

Can anyone tell me how to do a step-by-step installation and configuration?

Thank you.

./cheaziz

---

### Post by fenian on 2008-01-27
I got skencil working by doing this,open a terminal and enter the following lines (enter each line seperately)...

> sudo apt get installl tcl8.4-dev tk8.4-dev

cd /tmp

sudo apt-get install python2.4 python2.4-dev build-essential

sudo apt-get remove skencil

sudo apt-get source skencil

cd skencil-0.6.17/

sudo python2.4 setup.py configure --prefix=/usr/local

sudo python2.4 setup.py build

sudo python2.4 setup.py install

sudo perl -pi -e 's,env python,env python2.4,' /usr/local/lib/skencil-0.6.17/*.py

You can start skencel from the terminal by typing...

> skencil

To add skencil to the applications menu...

Right click the applications menu,choose edit menus,click graphics,click theNew Item button,under name enter Skencil,under command enter skencil,click close.
You should now be able to start skencil rom Applications>Graphics>Skencil.

---

### Post by CheAziz on 2008-01-27
Fabian,

I got error on command...

sudo apt-get install tclB.4-dev tkb.4 dek

E: Couldnt find package tclB.4-dev

---

### Post by CheAziz on 2008-01-27
Fabian

Please ignore previous posts... I didnt quite read the command sequence properly.. my error.

---

### Post by CheAziz on 2008-01-27
Fenian

Thank you again for the terminal commands, which I tried... some worked others didnt...

sudo apt get installl tcl8.4-dev tk8.4-dev [this worked]

cd /tmp [this worked]

sudo apt-get install python2.4 python2.4-dev build-essential [this worked]

sudo apt-get remove skencil [this worked]

sudo apt-get source skencil [this didnt - failed to get source of skencil]

cd skencil-0.6.17/ [this didnt - no such directory]

sudo python2.4 setup.py configure --prefix=/usr/local [this didnt - no such file 'setup.py']

sudo python2.4 setup.py build [this didnt - same reason as above]

sudo python2.4 setup.py install [this didnt - same reason as above]

sudo perl -pi -e 's,env python,env python2.4,' /usr/local/lib/skencil-0.6.17/*.py [this didnt - same reason as above]

I will be waiting to hear from you for suggestions on how I can successfully install Skencil.

Thank you.

./cheaziz

---

### Post by fenian on 2008-01-27
First open Synaptic package manager (System>Administration>Synaptic Package Manager).
Go to the settings menu and choose repositories,click the third-party software tab and check the box next to line...

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner(Source Code)

close synaptic open a terminal and install the python-dev tools with this command...

> sudo apt-get install python-dev

Then try following my previous instructions.

---

### Post by CheAziz on 2008-01-28
Fenian

Thanks for ur clarification. I will do as suggested.

But, in the meantime, I managed to install Phython 2.4 via Synaptic Package Manager. I installed pretty much everything that was associated with Python 2.4, including the dev files.

Still, Skencil wont work. Does this mean that Skencil doesnt work when in stalled via Synaptic? How come other packages work when installed this way?

Or, is there a configuration file I can send you, which will show you how and what is installed under Python 2.4, so that you can suggest upgrades and updates?

Incidentally, I thought that by removing Python 2.5 the problem would be solved. In reality, Ubuntu is pretty heavily built around Python 2.5. In fact, ALL of it is built under that way. As I selected Puthon 2.5 for removal, I watched applications being removed, up to where I decided to apply a COLD BOOT, and had to re-install Ubuntu all over again. I guess I learned that some things are better when left untouched. I am learning... LOL

Thanks.

./cheaziz

---

### Post by fenian on 2008-01-29
The version of skencil in the repositories does not work.In order to get it to work you need to recompile the source code to use python 2.4,the instructions I posted in my first post do this.The instructions in my second post (choosing repository) will enable you to grab the source code.

---

### Post by CheAziz on 2008-01-29
Fenian

Hi. I added the repository source as you suggested and started repeating the procedure you first posted, I got the following error message...

[INDENT]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)[/INDENT]

What could be wrong?

./cheaziz

---

### Post by fenian on 2008-01-29
Run this command...

> sudo apt-get update

and try again.

---

### Post by lswest on 2008-01-29
were you downloading or installing anything else or updating programs? because that error means that the software program (apt-get;synaptic;add/remove) is running already, and so you can't install/update anything else until that installation/update is done.  just try again in a few minutes^^

---

### Post by CheAziz on 2008-01-29
I just did, and this is what I got

Fetched 29.5kB in 8s (3490B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

A propos, do you have a Yahoo or MSN Messenger ID? It seems a lot easier if we could solve this problem via Instant Messenger.

You can add me on. I use Pidgin. My ID is aziz_mongi on both Yahoo and MSN.

./cheaziz

---

### Post by lswest on 2008-01-29
that error states that the program is in use at the moment, and you must wait for it to finish before installing it; if it persists, try rebooting the computer and trying again...probably installing updates.

---

### Post by CheAziz on 2008-01-30
All,

This is the update on this thread so far.

1) Apparently, as Skencil worked with Python 2.4, since the introduction of Ubuntu 7.10 (which has Python 2.5) it ceased to work. You cant have Python 2.4 and 2.5 in the same environment, and you cannot remove Python 2.5 (as I found out) because it will make Ubuntu 7.10 inoperable.

2) Someone apparently fixed the problem by making Skencil compatible and functional under Python 2.5. The source code can be downloaded by entering the following command under Terminal
[INDENT]
svn checkout [https://scm.wald.intevation.org/svn/skencil/skencil/branches/skencil-0.6](https://scm.wald.intevation.org/svn/skencil/skencil/branches/skencil-0.6)[/INDENT]

3) Having done that, one has to enter the following commands to setup and install Skencil. These commands are run from within the skencil-0.6 directory.


[INDENT]./setup.py configure[/INDENT]

[INDENT]./setup.py build[/INDENT]

[INDENT]./setup.py install[/INDENT]

4) You get to the ./setup.py install stage IF the ./setup.py build command completes successfully. However, I get the following error when running the command.

running 'make' in Pax
./paxmodule.o ./tkwinobject.o ./gcobject.o ./cmapobject.o ./pixmapobject.o ./regionobject.o ./fontobject.o ./imageobject.o ./borderobject.o ./clipmask.o ./paxutil.o  -L/usr/lib -L/usr/X11/lib -ltk8.4 -ltcl8.4 -lX11 -lXext  -o ./paxmodule.so
make: execvp: ./paxmodule.o: Permission denied
make: *** [paxmodule.so] Error 127
exiting because of errors

Can anyone tell me what is wrong here? Why is there a 'permission denied' error?

Thank you.

---

### Post by CheAziz on 2008-02-01
Hi All,

I finally managed to get Skencil 0.16 configured, built and installed on my Ubuntu 7.10 (Gutsy) build, which runs with Python 2.5.

Now, my next problem is, HOW do I migrate fully from Adobe Illustrator CS2 to Skencil? Skencil wont open the files created with Adobe Illustrator CS2 (Windows).

Please help.

./cheaziz

---

### Post by pugia on 2008-02-05
can you tell us how you solve your problem?
I have the same following your instruction:
```
make: execvp: ./paxmodule.o: Permission denied
```

thanks

---

### Post by J77 on 2008-02-08
Do the above as su

Then add /usr/local/bin/skencil to your path (ie. in .login)

---

### Post by Dithers on 2008-03-02
> **CheAziz said:**
> Hi All,

I finally managed to get Skencil 0.16 configured, built and installed on my Ubuntu 7.10 (Gutsy) build, which runs with Python 2.5.

Now, my next problem is, HOW do I migrate fully from Adobe Illustrator CS2 to Skencil? Skencil wont open the files created with Adobe Illustrator CS2 (Windows).

Please help.

./cheaziz



I would make an action in CS2 that opens from a dir, creates outlines, expands warps and evelopes and saves as an SVG or EPS legacy  in a new dir. this should solve your problem.

---

### Post by fanou on 2008-03-04
Hi all
I have also followed the instruction to install skencil and I am stuck to the 


running 'make' in Pax
./paxmodule.o ./tkwinobject.o ./gcobject.o ./cmapobject.o ./pixmapobject.o ./regionobject.o ./fontobject.o ./imageobject.o ./borderobject.o ./clipmask.o ./paxutil.o -L/usr/lib -L/usr/X11/lib -ltk8.4 -ltcl8.4 -lX11 -lXext -o ./paxmodule.so
make: execvp: ./paxmodule.o: Permission denied
make: *** [paxmodule.so] Error 127
exiting because of errors


Executing 

    ./setup.py configure

    ./setup.py build

    ./setup.py install

with a sudo does not change anything.

I might have misunderstand the solution. Can someone give me some more information ?

Thanks

---

