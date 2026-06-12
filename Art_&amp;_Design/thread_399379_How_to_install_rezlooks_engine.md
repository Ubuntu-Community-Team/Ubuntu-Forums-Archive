---
title: "How to install rezlooks engine?"
date: 2007-04-02
forum: Art &amp; Design
---

### Post by gnrlove on 2007-04-02
Hi everyone!

I've just found this awesome theme, which I want to use, but it says I need the rezlooks engine... now, I've found the source files, and I've tried to follow the instructions in the readme file, but when I get to the part where I run "./configure" , I get the following message:

```
gnrlove@gnrlove-desktop:~/Desktop/rezlooks-0.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
gnrlove@gnrlove-desktop:~/Desktop/rezlooks-0.6$ 

```

When I try to run "make" , I get the following:

> gnrlove@gnrlove-desktop:~/Desktop/rezlooks-0.6$ make
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./engines/rezlooks/src -I./engines/crux/src -I./engines/smooth/src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT rezlooks_rc_style.lo -MD -MP -MF ".deps/rezlooks_rc_style.Tpo" -c -o rezlooks_rc_style.lo `test -f './src/rezlooks_rc_style.c' || echo './'`./src/rezlooks_rc_style.c; \
        then mv -f ".deps/rezlooks_rc_style.Tpo" ".deps/rezlooks_rc_style.Plo"; else rm -f ".deps/rezlooks_rc_style.Tpo"; exit 1; fi
/bin/sh: Can't open ./libtool
make: *** [rezlooks_rc_style.lo] Error 1


can anyone help me out, so that I can get that theme?

---

### Post by ComplexNumber on 2007-04-02
the engine needs to be installed in /usr/lib/gtk-2.0/2.10.0/engines. when you type in "./configure" without any arguments, it just assumes  to install it in /usr/local. that won't work for any of the engines. therefore, you need to use the following instead:

**./configure --prefix=/usr**

---

### Post by gnrlove on 2007-04-02
Am I supposed to replace prefix and usr with anything?

Thanks for your reply btw... :D

---

### Post by ComplexNumber on 2007-04-02
> **gnrlove said:**
> Am I supposed to replace prefix and usr with anything?

Thanks for your reply btw... :D
no, just type that in exactly how its written. what its saying is that it is going to install it in /usr. 
if you just type in "./configure", this _assumes_ that its going to install it in /usr/local. the engines won't work if they go in usr/local*/*lib/gtk-2.0/2.10.0/engines

---

### Post by gnrlove on 2007-04-02
When i try to run 
> ./configure --prefix=/usr

I get the same message as when I run

> ./configure

that was not supposed to happen I guess... :)

---

### Post by ComplexNumber on 2007-04-02
are you using dapper?
also, have you got 'build-essential' package installed (have a look in synaptic to check)?

---

### Post by gnrlove on 2007-04-02
I checked out that buid-essentials thingy... turnes out I didn't have that, so I installed it...

about dapper, I don't know, actually I don't even know what dapper is... :)

---

### Post by ComplexNumber on 2007-04-02
> **gnrlove said:**
> I checked out that buid-essentials thingy... turnes out I didn't have that, so I installed it...

about dapper, I don't know, actually I don't even know what dapper is... :)
sometimes the errors that 'configure' and 'make'  scripts can be really cryptic. 
the build-essentials should help with making it work. did you try running the configure script after you installed it?

dapper is the version of ubuntu that you may be using (a bit like if someone asks you what version of windows you're using, you may answer something like "vista" or "XP"). the latest is called edgy eft. the next release is called feisty fawn. releases are released approximately every 6 months. if you go to your main menu, then click on 'system', then 'about ubuntu', it will tell you there.

---

### Post by gnrlove on 2007-04-02
I've got 6.10, so i guess that's edgy then... :)

I tried running ./configure again, now with build-essentials installed, and yeah, it was a lot simpler... now it said that i need GTK+-2.8 to compile rezlooks... so I'm updating to 2.8 now, and I'l try again.. :)

---

### Post by ComplexNumber on 2007-04-02
> **gnrlove said:**
> I've got 6.10, so i guess that's edgy then... :)

I tried running ./configure again, now with build-essentials installed, and yeah, it was a lot simpler... now it said that i need GTK+-2.8 to compile rezlooks... so I'm updating to 2.8 now, and I'l try again.. :)
right, install the "dev" version of the package of gtk. fire up synaptic and install the following package:
**libgtk2.0-dev**



when youre compiling packages from source, its important to realise that you need to have the "dev" packages installed. for example, if you have libgtk2.0 but you don't have libgtk2.0-dev, the configure script won't be able to detect if gtk is installed or not. the reason why is because the configure script looks in the following 2 locations to determine if  a particular dependency is installed:
/usr/lib/pkgconfig
/usr/local/lib/pkgconfig
if you have a look in these 2 locations, you will see lots of "pc" packages. these "pc" packages are only installed with "dev" packages.

---

### Post by gnrlove on 2007-04-02
ok, I've installed that package, can I now try to compile rezlooks?

---

### Post by ComplexNumber on 2007-04-02
> **gnrlove said:**
> ok, I've installed that package, can I now try to compile rezlooks?
yes. however, the deb package should make things easier for you. its in post 40 in [this]("http://ubuntuforums.org/showthread.php?t=175777&page=4&highlight=rezlooks+deb+edgy") thread. once you've downloaded it, extract it by right click on it and selecting 'extract here'. to install it, double click on it.

---

### Post by gnrlove on 2007-04-03
ok, I installed the deb package, and rebooted, what do I do now to apply the theme?

thanks for your patience... :D

---

### Post by ComplexNumber on 2007-04-03
yup. apply the theme and then post back to let me know that all is ok.

---

### Post by gnrlove on 2007-04-03
well, the thing is that I don't know how to apply it... :D

---

### Post by ComplexNumber on 2007-04-03
have you installed any rezlooks themes yet? 

after you've downloaded and extracted the theme, place themes in either /usr/share/themes(this will mean that the theme can be used by everyone, including root) or /home/<your-username>/.themes. 

to apply them, go to the main menu -> system -> preferences -> themes. if its not shown in the list, click  'theme details', then 'contols'. then select the theme.

---

### Post by gnrlove on 2007-04-03
When I try to move the theme I want to install to /usr/share/themes, I get a message saying I don't have permission to write to this folder... I'm the only user of the computer, so if I don't have permission, who has? :)

---

### Post by ComplexNumber on 2007-04-03
> **gnrlove said:**
> When I try to move the theme I want to install to /usr/share/themes, I get a message saying I don't have permission to write to this folder... I'm the only user of the computer, so if I don't have permission, who has? :)
thats because you need to be root to place them in there. i was going to suggest a command on the commandline for you to place them in there, but i think its probably safer if you just place them in /home/<your-username>/.themes instead.

note that files that are preceded by a dot are hidden files. if you can't see hidden files and directories, go into the 'Edit' menu in nautilus, select 'preferences', then tick 'show hidden and backup files'

---

### Post by gnrlove on 2007-04-03
what file type should the theme be?

The theme I'm trying to install is called Lily, and in the folder, there are some subfolders, like lily_green and lily_blue, but when i try to place the whole folder in /home/%usrname%/.themes, it doesn't show up in System/preferences/themes...

---

### Post by ComplexNumber on 2007-04-03
> **gnrlove said:**
> what file type should the theme be?

The theme I'm trying to install is called Lily, and in the folder, there are some subfolders, like lily_green and lily_blue, but when i try to place the whole folder in /home/%usrname%/.themes, it doesn't show up in System/preferences/themes...
take the themes out of the extracted folder, then place them in .themes directory. you should find 2 gtk themes (have a look inside to check) called Lily-blue and Lily_pink

---

### Post by gnrlove on 2007-04-03
so this is how it should look:

/home/%USRNAME%/.themes/Lily/ lily_blue/gtk-2.0/gtkrc
/home/%USRNAME%/.themes/Lily/ lily_pink/gtk-2.0/gtkrc

---

### Post by ComplexNumber on 2007-04-03
> **gnrlove said:**
> so this is how it should look:

/home/%USRNAME%/.themes/Lily/ lily_blue/gtk-2.0/gtkrc
/home/%USRNAME%/.themes/Lily/ lily_pink/gtk-2.0/gtkrc
no, it should look like this:


/home/%USRNAME%/.themes/lily_blue/gtk-2.0/gtkrc
/home/%USRNAME%/.themes/lily_pink/gtk-2.0/gtkr

---

### Post by gnrlove on 2007-04-03
still nothing in System>preferences>themes

---

### Post by ComplexNumber on 2007-04-03
there is. click on 'theme details', then look for it in 'Controls'.

---

### Post by gnrlove on 2007-04-03
well, now it looks like human just, that the borders are blue, and tabs are a bit different...

do you know how to make it look like the preview [here]("http://www.deviantart.com/deviation/49478473/")?

---

### Post by ComplexNumber on 2007-04-03
> **gnrlove said:**
> well, now it looks like human just, that the borders are blue, and tabs are a bit different...

do you know how to make it look like the preview [here]("http://www.deviantart.com/deviation/49478473/")?
the reason why is that you are using Human metacity(ie window manager). i don't know what the metacitytheme is, but you could download [this]("http://gnome-look.org/content/show.php/SmoothCL?content=35106"), right click on it to extract it, then place it in .themes. 
then select 'smoothcl' from the list of window borders.

---

### Post by gnrlove on 2007-04-03
thanks a lot.... now it looks awesome... appreciate your patience with a complete linux noob... :D

---

### Post by ComplexNumber on 2007-04-03
glad to help...as always :)

---

### Post by Evangeline on 2008-07-16
> **ComplexNumber said:**
> there is. click on 'theme details', then look for it in 'Controls'.

Sorry for bumping such an old thread :/ 

click on theme details where? :confused:

---

