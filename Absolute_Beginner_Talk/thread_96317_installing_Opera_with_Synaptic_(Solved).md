---
title: "installing Opera with Synaptic (Solved)"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-28
hi, i want to install Opera with Syaptic but it's not on the list. can i edit it so it will install with Syaptic? thanks

---

### Post by Leif on 2005-11-28
you'll need one of the following lines in your sources.list, I'm not too sure which one will be ubuntu compatible, so try them in the order below :

# The Opera Web Browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) testing non-free
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

---

### Post by Danielle on 2005-11-28
thanks, i'll try it now. i know the command line to open the source list: 
sudo gedit /etc/apt/sources.list

but is this the same thing?
Settings > Repositories > Add > Custom

---

### Post by gord on 2005-11-28
pritty much yea :)

---

### Post by Danielle on 2005-11-28
i just got this for the first one "the following have unresolvable dependcies"
opera:
 Depends: libqt3c102-mt  but it is not installable

---

### Post by Danielle on 2005-11-28
[QUOTE=gord]pritty much yea :)[/QUOTE]
thanks, that's probably the first thing i have got right since i installed :D

---

### Post by Leif on 2005-11-28
is there an opera-static package ? if there is, try that

---

### Post by Danielle on 2005-11-28
i just tried that and during setup it said it wasn't authentic and now there are errors when it starts:

Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/netscape/plugins-libc6/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/mozilla/plugins
/usr/lib/netscape/plugins-libc6

and these errors too:

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

it does work though. can i fix it? or should i go to the next line on the list and put it in Synaptic?. i just rememebered how much better i think Opera is to Firefox. it seems so much more solid. plus Firefox is using 25/30% CPU and has crashed 3/4 times in the last week with lots of tabs open.

---

### Post by Leif on 2005-11-28
hmm, that's weird, it is their official repository. the last thing I can think of is to uninstall, download the package from their site manually, and install it that way. to do that, go to your download dir, and type "sudo dpkg -i opera??.deb" (fill in ?? as appropriate) at a terminal

---

### Post by Danielle on 2005-11-28
i'm downloading now :-D it's a newer version to the repos. version. i'm putting it on my desktop. is this correct?
cd Desktop
sudo dpkg -i opera??.deb
i'll put the correct version in. then to run:
sudo opera

thanks

---

### Post by Leif on 2005-11-28
you don't need to use sudo when running it, just when installing it.

---

### Post by gord on 2005-11-28
its generally a bad idea to run any program with root privilges (sudo) unless the program absoultly needs it (like mounting partitions or something), you could do damage to your installation and many programs will refuse to run.

---

### Post by Danielle on 2005-11-28
this is the error i get when i run:
cd Desktop
sudo dpkg opera_8.51-20051114.6-shared-qt_en_etch_i386.deb

dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

i tried:
sudo dpkg install opera_8.51-20051114.6-shared-qt_en_etch_i386.deb

---

### Post by gord on 2005-11-28
```
sudo dpkg **-i** opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
```

---

### Post by Danielle on 2005-11-28
hi, i just tried without sudo and it said i needed superuser privilege.
i did this, and this is the error:
 sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.de
dpkg: error processing opera_8.51-20051114.6-shared-qt_en_etch_i386.de (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera_8.51-20051114.6-shared-qt_en_etch_i386.de

i like installing with Synaptic.

---

### Post by Danielle on 2005-11-28
OK i'll try cding to Desktop first this time :-D

---

### Post by Leif on 2005-11-28
[QUOTE=Danielle]hi, i just tried without sudo and it said i needed superuser privilege.
i did this, and this is the error:
 sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.de
dpkg: error processing opera_8.51-20051114.6-shared-qt_en_etch_i386.de (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera_8.51-20051114.6-shared-qt_en_etch_i386.de

i like installing with Synaptic.[/QUOTE]

we all do :) you forgot the "b" at the end.

```

sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb

```

---

### Post by Danielle on 2005-11-28
i need superuser privilege. how do i do that? thanks

---

### Post by gord on 2005-11-28
you were fine the first time, just forgot to put an -i in there. also, dpkg allways needs sudo to install stuff

```

cd ~/Desktop 
sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb

```

---

### Post by Danielle on 2005-11-28
[QUOTE=Leif]you don't need to use sudo when running it, just when installing it.[/QUOTE]
thanks, i just saw your post. i think i was thinking of gksudo. i just looked it up on the wiki and it's not there and with google and there's nothing near the start that says exactly what it is :(

---

### Post by Leif on 2005-11-28
more than you probably want to know (but it is important stuff) :

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Danielle on 2005-11-28
[QUOTE=gord]you were fine the first time, just forgot to put an -i in there. also, dpkg allways needs sudo to install stuff

```

cd ~/Desktop 
sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb

```[/QUOTE]
thanks, gord. i am starting to see my mistakes and correct them, i noticed that just in time. i suppose i can't learn Linux in a week. i know i used superuser privilege once before but i can't rememeber how it works now. did you see post#18?

---

### Post by gord on 2005-11-28
using sudo gives you superuser privilages, what do you think the su stands for ;)

---

### Post by Danielle on 2005-11-28
[QUOTE=Leif]more than you probably want to know (but it is important stuff) :

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]
thanks, Leif. i've got lots of books to read too like Linux bible 2005 and lots more. 
i'm getting a headache, although i should be getting used to this by now, all my installs are like this. i'm going to make some tea. and stop for a couple of minutes. thanks for helping me :)

---

### Post by Leif on 2005-11-28
[QUOTE=Danielle]thanks, Leif. i've got lots of books to read too like Linux bible 2005 and lots more. 
i'm getting a headache, although i should be getting used to this by now, all my installs are like this. i'm going to make some tea. and stop for a couple of minutes. thanks for helping me :)[/QUOTE]

glad to help. the forums are full of friendly people, so just keep asking questions and you'll have a perfectly setup system in no time.

---

### Post by Danielle on 2005-11-28
it didn't work. there're dependency problems. i might have to try the second source list. this is the error:

Selecting previously deselected package opera.
(Reading database ... 66095 files and directories currently installed.)
Unpacking opera (from opera_8.51-20051114.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera

can i install these two files? or are they not conpatible with my system? thanks
 libqt3-mt
libqt3c102-mt

---

### Post by Leif on 2005-11-28
danielle, you need to download the static version of opera. right now you're trying to install the shared library version. the static version will contain all the libraries it needs, so things will work fine

---

### Post by gord on 2005-11-28
sudo apt-get install libqt3-mt

should fix it.. prolly. they are just parts of kde that opera needs apprently

---

### Post by Danielle on 2005-11-28
i just installed libqt3-mt, but i can't find libqt3c102-mt. i'm going to have a look with google now.

---

### Post by gord on 2005-11-28
just try it without, i don't know much about kde but im pritty sure that they are both the same thing

---

### Post by Danielle on 2005-11-28
no, i just tried another 2 versions each had a static version and i still got the error. it was the second on the list and this one:
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
 
i'll try the last one on the list now:

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

---

### Post by Danielle on 2005-11-28
hi, this is the fix:

1. Download lesstif source from sourceforge.net
2. configure, make BUT DO NOT make install
3. copy libXm.so.2 from compile directory to /usr/X11R6/lib/libXm.so.2
4. ldconfig

i am downloading lesstif source now. can someone help me with the rest, please? thanks

---

### Post by Danielle on 2005-11-28
this is the name of the file i downloaded to my desktop:

lesstif-0.94.4.tar.gz

---

### Post by Danielle on 2005-11-28
hi, i've made afew directories and installed libmotif3 lesstif2 and motif-clients.

i just need to install openmotif with the instructions from [here](http://ubuntuforums.org/showthread.php?t=74667) and i should have opera installed. can you help?

 so far i've taken 5 1/2 hours trying to install it. that's not too bad, i hope to rap it up within another 3 or 4. thanks

---

### Post by Turtle.net on 2005-11-28
Euh...just an assumption (I never tried to install Opera) but it seems that your package is not build for Ubuntu.
I have these two lines in my sources.list ```
$ grep freecontrib /etc/apt/sources.list
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

And I have an Opera package now with synaptic.

I don't know if it's good enough...maybe you can try that...

---

### Post by aysiu on 2005-11-28
5 1/2 hours?
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

### Post by Danielle on 2005-11-28
[QUOTE=aysiu]5 1/2 hours?
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)[/QUOTE]
yes, almost 6 now. i've tried it and the plugins don't work. 

i'm following the instructions from the link below.
[http://www.ubuntuforums.org/showthread.php?t=76236](http://www.ubuntuforums.org/showthread.php?t=76236)

i'm all the way up to post #15 then i followed all the next steps. now all i have to do is the bit above. can someone help?

---

### Post by aysiu on 2005-11-28
That's your problem. Don't use the link below. Use the link above (the one I linked to).

---

### Post by Danielle on 2005-11-28
thanks, i'm not sure if i've done that yet, i have edited lots of stuff in and out of the source list and downloaded about 8 different versions - static and the other one too, but they all have the same error.

 i have no idea why i did it but i started another thread after following lots of instructions and getting stuck on the very last step form another thread. i just thought i'd do the last step and it would be done as all the other steps had worked out so well. the other thread is [here](http://www.ubuntuforums.org/showthread.php?p=528601&posted=1#post528601)
sorry, i won't do it again :(

---

### Post by Danielle on 2005-11-28
i'll try it now, i just realised i have now installed the two files which where causing the errors last time i tried your link.

can i install on top of the version i have? i'm scared of uninstalling the dependencies which i just installed when i uninstall it.

---

### Post by erikpiper on 2005-11-28
I havent read the whole thread, but just so you know, the exelent Automatix by arnieboy installs operah for you, as well as a whole lot of other stuff :) 
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by Danielle on 2005-11-28
Wow, thanks erikpiper. i was going to install that easyubuntu install but i noticed i had installed most of the stuff already. i might try and install it one more time (opera) and if it doesn't work then use Automatix tomorrow. thanks for the help :)

---

### Post by aysiu on 2005-11-28
Don't uninstall anything unless you know it's a problem.
Go to the Opera website and download the appropriate package (see attached screenshot) to your desktop.
For the sake of simplicity, rename the package to be opera.deb
Then, open up a terminal (Applications > Accessories > Terminal) and type ```
cd Desktop
sudo dpkg -i opera.deb
``` If you get any errors, post them here exactly as they are (just copy and paste).

---

### Post by Danielle on 2005-11-28
it worked. i feel abit underwhelmed by it all now :D i used one of the downloads i'd used before from my desktop. last time it gave me an error about a couple of motif files it needed. but i just installed them before i started this thread. so i hope that was the reason it worked. anyway, thanks alot for your help, i'm very grateful. :cool:

---

### Post by Danielle on 2005-11-28
aysiu, can you put solved on the thread below? thanks

[http://www.ubuntuforums.org/showthread.php?t=96317](http://www.ubuntuforums.org/showthread.php?t=96317)

---

### Post by aysiu on 2005-11-28
[QUOTE=Danielle]aysiu, can you put solved on the thread below? thanks

[http://www.ubuntuforums.org/showthread.php?t=96317](http://www.ubuntuforums.org/showthread.php?t=96317)[/QUOTE] Done.

---

