---
title: "another youtube solution - democracy player"
date: 2007-06-16
forum: Apple PPC Users
---

### Post by ssam on 2007-06-16
it lets you search for and watch youtube videos (as well as video pod casts).

Its in the feisty repositories, its a bit old but it works. the package name is democracyplayer.

to get the lastest version get the latest source tarball from [http://www.getdemocracy.com/downloads/](http://www.getdemocracy.com/downloads/)

extract it
```
tar xvf Democracy-0.9.6.tar.gz
```

get the build dependencies (there might be more, post of you get compile error messages)

```
sudo apt-get install python-pyrex libboost-python-dev python-gtk2-dev python-gnome2-extras-dev libxine-dev libnspr-dev firefox-dev build-essential
```

and run it (on the first run it will be compiled)

```
cd Democracy-0.9.6/platform/gtk-x11/
./run.sh

```

---

### Post by ubuntubrian on 2007-06-16
this is good news! I have gnash-0.8 working mostly but this may be better. I'm going to try to make a backport to Dapper using prevu.:)

---

### Post by ubuntubrian on 2007-06-16
well, the backport didn't work so I just downloaded the tarball and ran the script and it seems to be working. I got all the dependencies from a Mepis thread on Democracyplayer and installed them thru synaptic.
This may just work. What does it use for codecs-just curious

:)

---

### Post by shen-an-doah on 2007-06-16
If you look on the downloads page, there's a link that shows you how to add their repository, which is easier than building from source. It has ones for Edgy and Dapper too.

---

### Post by stmiller on 2007-06-17
> **ubuntubrian said:**
> What does it use for codecs-just curious

:)

I think democracy player uses VLC as the backend. So should be able to play anything.

---

### Post by ssam on 2007-06-17
> **shen-an-doah said:**
> If you look on the downloads page, there's a link that shows you how to add their repository, which is easier than building from source. It has ones for Edgy and Dapper too.

the repo did not seem to have powerpc packages in.

---

### Post by ubuntubrian on 2007-06-17
No ppc packages. It's really easy to install from source.
Download the .gz source file
unpack somewhere
cd into the directory and bore down to the gtk-x11 directory in "platform"
run ./run.sh in the gtk-x11 directory.
No building, no compiling.
The only pain is having to go into that directory from the command line and run the ./run/sh command. the launcher I created won't start it.

---

### Post by Calash on 2007-06-23
I know this is a simple question, but google is not being kind to me today.

How do I make a launcher to run that  in xubuntu?  I tried simply having it point to the run.sh but it does nothing.


Thanks

---

### Post by ubuntubrian on 2007-06-23
It won't run from a launcher for some reason, at least when I tried. I just do the same thing as i did when i installed it:

cd into the directory and bore down to the gtk-x11 directory in "platform"
run ./run.sh in the gtk-x11 directory.

---

### Post by Calash on 2007-06-23
I need to setup an automatic way to run it...I am not going to be the one using it on the iBook.  There should be some way to have a launcher do the same actions.....I am just not sure how to do it on Ubuntu yet :)  Windows I could script it via a batch file, or set the shortcut to the working directory.

Just need to find how to do that here ;)

---

### Post by ubuntubrian on 2007-07-02
you could definitely make a shell script and keep it on your desktop, make it executable and click on it and the player should launch. Someone on the forums should be able to make a simple one given the info on this thread-not me though

:popcorn:

---

### Post by Twiggy003 on 2007-07-05
While compiling it gave an error

gcc: error trying to exec 'cc1plus': execvp: No such file or directory
error: command 'gcc' failed with exit status 1


what does that mean? do i need to install something else to make it work?

thanks,

---

### Post by xubu_caapn on 2007-07-06
i don't want all these gnome packages on my xubuntu!
is there any way to run this without all those packages?

---

### Post by avtolle on 2007-07-06
[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce) may help you, xubu_caapn.

---

### Post by kano on 2007-07-07
you should be able to just make a script that cd's to the path and runs it... then you can make a launcher to that script.

```

#!/bin/sh

cd path/to/run.sh
./run.sh

```

---

### Post by ssam on 2007-07-09
> **Twiggy003 said:**
> While compiling it gave an error

gcc: error trying to exec 'cc1plus': execvp: No such file or directory
error: command 'gcc' failed with exit status 1


what does that mean? do i need to install something else to make it work?

thanks,

yes you will probably need build-essential (i have added it to the top post)

---

### Post by nerdmods on 2007-07-17
I know this may be a totaly stupid question, but was wondering how to make a script and create a launcher for it for the player. Running newest build Ubuntu 7.04 - the Feisty Fawn.

First time user on any platform.

---

### Post by johng4 on 2007-07-18
Oddly enough, Democracy works better for me straight from the Ubuntu Repos on PPC than the same version does on my x86 machine.

Same with Banshee.

---

### Post by ssam on 2007-07-18
there is a new version out. they are moving to the new name miro
[http://www.getmiro.com/](http://www.getmiro.com/)

i have not had a chance to try it yet

---

### Post by johng4 on 2007-07-18
The repository listed does not provide ppc packages :/

I'm going to attempt to build this from source.

---

### Post by 4ebees on 2007-07-19
> **Twiggy003 said:**
> While compiling it gave an error

gcc: error trying to exec 'cc1plus': execvp: No such file or directory
error: command 'gcc' failed with exit status 1


what does that mean? do i need to install something else to make it work?

thanks,

I'm using Dapper and to get this installed I had to do the following:

> 
Ubuntu:
-------

To build and run:
   sudo apt-get install python-pyrex libboost-python-dev python-gtk2-dev python-gnome2-extras-dev mozilla-dev libxine-dev


This is contained within the README found in this part of the package:

Miro-0.9.8/platform/gtk-x11/

Hope this helps

---

### Post by stmiller on 2007-07-20
Argh! When trying to execute that run.sh, it complains of no xulrunner-xpcom, mozilla-xpcom or firefox-xpcom. When I try to install the appropriate package ( libxul-dev ) it will not install, claiming dependency issues. Hmmmm...

EDIT: Solved! I guess it helps for me to actually read the instructions. There's a line in here about what packages you have to install on Feisty:

[https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs)

---

