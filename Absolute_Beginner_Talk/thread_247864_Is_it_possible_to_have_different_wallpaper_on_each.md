---
title: "Is it possible to have different wallpaper on each desktop?"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by amished on 2006-08-31
I have quite a few great wallpapers, and I'd like to be able to see them all, but as soon as I switch it on one desktop, all of them switch to the new one.

I was just wondering if there's a way to lock say desktop 1 in place, then just be able to change the rest, and go down the line, or something like that.

Any help is greatly appreciated (also, I'm still using Breezy, not upgraded to Dapper yet, if that makes any difference)

tc,
Amished

---

### Post by bernied on 2006-08-31
This is definitely possible using kde (kubuntu), don't know about gnome. In kde, there is a selection in the desktop settings for 'this desktop' or 'all desktops' when you change wallpaper.

---

### Post by toasted on 2006-08-31
> **bernied said:**
> This is definitely possible using kde (kubuntu), don't know about gnome. In kde, there is a selection in the desktop settings for 'this desktop' or 'all desktops' when you change wallpaper.

I want to know this too. In Gnome there is NOT an option like you say that there is in KDE. So, maybe Gnome is not able to do this?

I would like a different wallpaper so that when I spin my cube all sides are different :biggrin:

---

### Post by Bagnaj97 on 2006-08-31
I'm not sure, but I think there might be an option somewhere if you play around in gconf-editor. I'll have a play around when I get home later.

---

### Post by toasted on 2006-08-31
> **Bagnaj97 said:**
> I'm not sure, but I think there might be an option somewhere if you play around in gconf-editor. I'll have a play around when I get home later.

I looked through it and didnt see anything... 

/desktop/gnome/applications/background     is where the wallpaper is

---

### Post by John.Michael.Kane on 2006-08-31
This maybe of use [mybackground-properties]("http://www.gnomefiles.org/app.php/mybackground-properties")

---

### Post by Metacarpal on 2006-08-31
> **SD-Plissken said:**
> This maybe of use [mybackground-properties]("http://www.gnomefiles.org/app.php/mybackground-properties")

Sweeeeeeeeeeeeeet.  Is this in the repos, or am I about to get more practice at compiling from source?

---

### Post by toasted on 2006-08-31
> **Metacarpal said:**
> Sweeeeeeeeeeeeeet.  Is this in the repos, or am I about to get more practice at compiling from source?

I dont see it in Synaptic

I did see wallpaper-tray though -  some may be interested
Its a wallpaper auto switcher

---

### Post by toasted on 2006-08-31
> **SD-Plissken said:**
> This maybe of use [mybackground-properties]("http://www.gnomefiles.org/app.php/mybackground-properties")

Sounds great! Thanks!!
How do we know if we can trust a source that we download from? Obviously if its in the repos its trustworthy but what about this particular one?

---

### Post by John.Michael.Kane on 2006-08-31
The trust of the source is not know,however. if you can understand code then you could in theory look through it,and fix or make it better.since it would seem the dev is no longer developing this app.

---

### Post by toasted on 2006-08-31
Ok then my next question should be... has anyone else tried this yet?
LOL
ok im chicken :mrgreen:

---

### Post by amished on 2006-08-31
Hehe, I'm kinda chicken too, and very beginner, what steps would I have to go through to "install" this package? I'm not that great at reading the instructions that they give me a lot of times...

---

### Post by John.Michael.Kane on 2006-08-31
You would download the file there is a **Basic Installation** walk through in the .tar file.

---

### Post by amished on 2006-08-31
I realize that there is a walkthrough in the .tar file, but like I said, I never seem to be able to understand/follow through on their instructions.  If I try to compile (not sure if I'm even doing this right) I get a message saying "not a directory"

```
amished@amish:~$ cd /home/amished/mybackground-properties-0.0.1/install-sh/configure
bash: cd: /home/amished/mybackground-properties-0.0.1/install-sh/configure: Not a directory 
```

---

### Post by toasted on 2006-08-31
I think you have to go in the src folder so its

cd /home/amished/mybackground-properties-0.0.1/src

then
./configure

Maybe?

---

### Post by amished on 2006-08-31
That didn't work either, anyone have success with this at all?

---

### Post by toasted on 2006-08-31
Ok try this then

```
cd /home/amished/mybackground-properties-0.0.1
./configure
```

Once you get into the folder that holds the source code (its either mybackground-properties-0.0.1  or  src) then type 

```
ls 
```

that will print out whatever files are in the directory that your are currently in (in the terminal)
You should be able to figure out if you are in the right place

You may have to do
```
 sudo ./configure
```
Just thought of that  :D

---

### Post by b1g4L on 2006-08-31
This is what you want:

[http://www.ubuntuforums.org/showthread.php?t=69507](http://www.ubuntuforums.org/showthread.php?t=69507)

Download it from the main site:
[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

---

### Post by amished on 2006-08-31
Sorry that I'm not that linux-compatible yet, so now I got that (semi) working, and this pops out:
```

amished@amish:~$ cd /home/amished/mybackground-properties-0.0.1
amished@amish:~/mybackground-properties-0.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
configure: error: XML::Parser perl module is required for intltool
amished@amish:~/mybackground-properties-0.0.1$ ls
aclocal.m4    config.sub    intltool-extract.in  missing        stamp-h.in
AUTHORS       configure     intltool-merge.in    mkinstalldirs  TODO
ChangeLog     configure.in  intltool-update.in   NEWS
config.guess  COPYING       ltmain.sh            po
config.h.in   INSTALL       Makefile.am          README
config.log    install-sh    Makefile.in          src 
```

and config.guess, config.sub, configure, install-sh, missing, mkinstalldirs are in green, and po and src are in blue.  any clues as to what this might mean, or what the next step is?

--edit-- 
seeing if the "wallpapoz" will work for me, if so, i'll edit again, and either way, thanks for the help.  maybe i can get both working, and understand it a bit more :smile:

---

### Post by toasted on 2006-08-31
> **amished said:**
> Sorry that I'm not that linux-compatible yet, so now I got that (semi) working, and this pops out:
```

amished@amish:~$ cd /home/amished/mybackground-properties-0.0.1
amished@amish:~/mybackground-properties-0.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
configure: error: XML::Parser perl module is required for intltool
amished@amish:~/mybackground-properties-0.0.1$ ls
aclocal.m4    config.sub    intltool-extract.in  missing        stamp-h.in
AUTHORS       configure     intltool-merge.in    mkinstalldirs  TODO
ChangeLog     configure.in  intltool-update.in   NEWS
config.guess  COPYING       ltmain.sh            po
config.h.in   INSTALL       Makefile.am          README
config.log    install-sh    Makefile.in          src 
```

and config.guess, config.sub, configure, install-sh, missing, mkinstalldirs are in green, and po and src are in blue.  any clues as to what this might mean, or what the next step is?

--edit-- 
seeing if the "wallpapoz" will work for me, if so, i'll edit again, and either way, thanks for the help.  maybe i can get both working, and understand it a bit more :smile:

The first part was the program trying to configure but you got some errors

The second part (after the ls) is just a listing of what is in that directory. Different types of files are different colors

---

### Post by amished on 2006-09-02
Wallpapoz ended up working, and I abandoned my quest to get mybackground properties to work, just cause i have one thing that already does what i want it to.  Thanks again for the help!

---

### Post by toasted on 2006-09-02
I got the wallpaper to change using wallpapoz, but they are all the same on the different workspaces. I am running XGL/Compliz though, so maybe that is the difference

---

### Post by yeehawjared on 2006-09-02
anyone figure out how to have multiple backgrouns with XGL?  wallpapoz didn't work for me either.  It's also tedius to manually add each image with wallpapoz

---

