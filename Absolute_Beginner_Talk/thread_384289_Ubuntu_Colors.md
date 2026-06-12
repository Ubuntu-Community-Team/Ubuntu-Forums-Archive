---
title: "Ubuntu Colors"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-14
I would like to know how to edit Ununtu Colors. It's not that I think it's ugly... i'm just a huge blue fan lol. I tried to right click on the desktop like on windows and then desktop background, but when I changed the color to blue, nothing happened.

---

### Post by DaveyG on 2007-03-14
System > Preferences > Theme  \\:D/

---

### Post by 3rdalbum on 2007-03-14
Probably best if you go to System > Preferences > Themes and change the theme to something like Clearlooks or Industrial Tango. When you want the caramel colour again (because you will :-)  ), you can just switch it back to the Human theme.

---

### Post by julie_lebou on 2007-03-14
ok cool thanks, i have a blue theme now, but how do i change the desktop background to blue?

---

### Post by ComplexNumber on 2007-03-14
> **julie_lebou said:**
> ok cool thanks, i have a blue theme now, but how do i change the desktop background to blue?
right click on the desktop and select 'change desktop background'. 

if you're feeling slightly more daring, you could install [this ]("http://gnome-look.org/content/show.php/gnome-color-chooser?content=47349")- it allows you to permanently set the colours on the fly of a theme whatever theme you've selected. for example, if you have the clearlooks theme (note: has creamy coloured background), you can set it so that clearlooks and every other theme that you select has blue background (for example). here is a screenshot showing it in action. note that i'm merely showing you an example - i would never be likely to try and blend a light blue background with lots of green mixed in :p.

---

### Post by julie_lebou on 2007-03-14
I downloaded it... but how to install?

---

### Post by ComplexNumber on 2007-03-14
> **julie_lebou said:**
> I downloaded it... but how to install?
fire up the terminal and go *into* where you extracted it.  for example, if you extracted to /home/<your-userame>/gtk-colour-chooser, then type the following in the commandline:
**cd ~/gtk-colour-chooser**

then type the following in the terminal:
[B]./configure

[/B]it may come up with some errors. if it does, post the end of the configure script where it may say that certain dependencies aren't met or it cant find such and such a package. if it does successfully configure (you may get a message such as "ok. you can type in 'make' now"), then type in:
**make**

wait for that to finish. then type in the following:

[B]sudo make install

[/B]
it should then appear in your menu in main meenu -> system -> preferences.

---

### Post by julie_lebou on 2007-03-14
julie@julie:~/gnome-color-chooser-0.1.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

julie@julie:~/gnome-color-chooser-0.1.3$

---

### Post by ComplexNumber on 2007-03-14
> **julie_lebou said:**
> julie@julie:~/gnome-color-chooser-0.1.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

julie@julie:~/gnome-color-chooser-0.1.3$
you need to install the following:
libgtkmm2.0-dev
libglademm-2.4-dev
libxml2-dev

---

### Post by julie_lebou on 2007-03-14
now its 

configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

---

### Post by ComplexNumber on 2007-03-14
> **julie_lebou said:**
> now its 

configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
maybe because you don't have *build-essentials* installed. install build-essentials and see if that works. i've never come across that error before, so its just a guess.

---

### Post by Patrick K on 2007-03-14
I've been following this and have ran "make install" with no apparent errors. It doesn't show up in the menus or in alacarte, though. I tried running the executable in its directory but got this "cannot open theme database. exiting". Thoughts?

---

### Post by ComplexNumber on 2007-03-14
> **Patrick K said:**
> I've been following this and have ran "make install" with no apparent errors. It doesn't show up in the menus or in alacarte, though. I tried running the executable in its directory but nothing happened. Thoughts?
the executable is called gnome-color-chooser. don't know if you know. if not, run that in the terminal (for the time being). sometimes they don't show up in the menu until the next time you log in.

after you ran "sudo make install", did it appear to install ok with no errors?

---

### Post by Patrick K on 2007-03-14
Well :) I ran make install without sudo. I went back and ran it again with sudo. This time running from the terminal I have the dialog box up and running. Strange there were no complaints about running make install without being root. 

This showed up in the term window > Unable to find include file: ".gtkrc-2.0-gnome-color-chooser"
However, it looks to be running properly and is in the menu system now. Thanks!

---

### Post by ComplexNumber on 2007-03-14
> **raidlost said:**
> Second curtian

no luck with the needed server after so many hours
no docs to do the trick
not enough sleep

and my boss walks in with red hat enterprise, now if that is not a hint

my heart goes out to ubuntu so if any one can help soon i might be able
to restore whatever reputation there is 

please check the threads i have

ps sorry for doing this..... you have the highest views
what on earth are you on about man?:confused:

---

### Post by raidlost on 2007-03-14
[http://ubuntuforums.org/showthread.php?t=384161](http://ubuntuforums.org/showthread.php?t=384161)

---

### Post by raidlost on 2007-03-14
[http://ubuntuforums.org/search.php?searchid=16237873](http://ubuntuforums.org/search.php?searchid=16237873)

---

### Post by ComplexNumber on 2007-03-14
why are you posting that in this thread about ubuntu colour configuring?

---

### Post by Patrick K on 2007-03-14
Sorry for the double post

---

### Post by julie_lebou on 2007-03-14
Everything worked.. i think...

 ''it should then appear in your menu in main meenu -> system -> preferences.''

Under what name? I can't find it!

---

### Post by Patrick K on 2007-03-15
I was waiting for ComplexNumber to return. Did you use "sudo" when you issued the "make install" command. The program didn't show up in the menu untill I ran the command as sudo. Without sudo it did not show up and there were no error messages in the terminal. It looked like everything worked properly. 

Its menu name is Gnome Color Control.

---

### Post by julie_lebou on 2007-03-15
found it, i guess i had to reboot for it to be there!!

What i did is after it was all configured, i typed 

make

then when that was all finished

sudo make install

then.... haha reboot!

---

### Post by Patrick K on 2007-03-15
Glad you got it working. I'm surprised you had to reboot. Anyway it's working. It's a pretty nifty program. I haven't really explored it yet but will. Enjoy!

---

