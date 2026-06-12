---
title: "Installing Third-Party Plugins For Pidgin"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by TeXperten on 2008-03-09
How do I install the "normal" plugins for Pidgin, from [http://developer.pidgin.im/wiki/ThirdPartyPlugins]("http://developer.pidgin.im/wiki/ThirdPartyPlugins")?

Please give me a lot of details--I've only used Linux for a few weeks.

---

### Post by herbster on 2008-03-09
It depends on the plugin. Some you have to compile, which means you download a .tar or some compressed archive (similar to a rar/zip file) and open it, inside it will be the source files. There's almost always a readme file in the archive that will tell you exactly how to install it.

---

### Post by kevdog on 2008-03-10
Which one do you want to install -- Ill walk you through it -- best to start off with a real life example!

---

### Post by TeXperten on 2008-03-13
I would really like to install pidgin-latex.

---

### Post by kevdog on 2008-03-13
Ok, download the tar.bz2 file from the website -- its named: pidgin-latex-1.2.1.tar.bz2

Place the file in your ~ directory

cd ~
tar -jxvf pidgin-latex-1.2.1.tar.bz2
cd pidgin-latex

Here you can read the instructions contained in the README file.  Note its incompatible with the encryption plugin.  Depending on how you installed pidgin (Im going to assume you installed it from a .deb or repository), I would do the following:

make
sudo make install PREFIX="/usr"

Restart pidgin and everything should work!

---

### Post by TeXperten on 2008-03-13
I got some help installing Pidgin v2.4.0 after compiling it from the source code. The newest version in the repository is 2.2.4.

I read the README file and tried (almost) the same as you suggest, but got the following error messages:


mads@ubuntu:~/Desktop/pidgin-latex$ make
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
gcc  -fPIC -c LaTeX.c -o LaTeX.o  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DHAVE_CONFIG_H
I filen inkluderet af LaTeX.c:32:
LaTeX.h:45:36: error: libpurple/conversation.h: No such file or directory
LaTeX.h:47:29: error: libpurple/debug.h: No such file or directory
LaTeX.h:48:31: error: libpurple/signals.h: No such file or directory
LaTeX.h:49:32: error: libpurple/imgstore.h: No such file or directory
LaTeX.h:50:28: error: libpurple/util.h: No such file or directory
LaTeX.h:51:30: error: libpurple/notify.h: No such file or directory
LaTeX.h:52:30: error: libpurple/server.h: No such file or directory
LaTeX.h:53:27: error: libpurple/log.h: No such file or directory
LaTeX.h:54:31: error: libpurple/version.h: No such file or directory
In file included from LaTeX.c:32:
LaTeX.h:89: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_blacklisted’
LaTeX.h:101: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘latex_to_image’
LaTeX.h:108: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘analyse’
LaTeX.h:119: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pidgin_latex_write’
LaTeX.h:122: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘message_send’
LaTeX.c:47: fejl: expected ‘)’ before ‘*’ token
LaTeX.c: In function ‘getdirname’:
LaTeX.c:101: fejl: ‘G_DIR_SEPARATOR’ undeclared (first use in this function)
LaTeX.c:101: fejl: (Each undeclared identifier is reported only once
LaTeX.c:101: fejl: for each function it appears in.)
LaTeX.c:111: advarsel: incompatible implicit declaration of built-in function ‘malloc’
LaTeX.c: In function ‘getfilename’:
LaTeX.c:124: fejl: ‘G_DIR_SEPARATOR’ undeclared (first use in this function)
LaTeX.c:127: advarsel: incompatible implicit declaration of built-in function ‘malloc’
LaTeX.c:133: advarsel: incompatible implicit declaration of built-in function ‘malloc’
LaTeX.c: In function ‘searchPATH’:
LaTeX.c:161: advarsel: incompatible implicit declaration of built-in function ‘malloc’
LaTeX.c: In function ‘execute’:
LaTeX.c:237: advarsel: incompatible implicit declaration of built-in function ‘malloc’
LaTeX.c: Ved øverste niveau:
LaTeX.c:291: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_blacklisted’
LaTeX.c:306: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘latex_to_image’
LaTeX.c:380: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘analyse’
LaTeX.c:522: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pidgin_latex_write’
LaTeX.c:555: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘message_send’
LaTeX.c:589: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_load’
LaTeX.c:604: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_unload’
LaTeX.c:615: fejl: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘info’
LaTeX.c:651: fejl: expected ‘)’ before ‘*’ token
LaTeX.c: In function ‘PURPLE_INIT_PLUGIN’:
LaTeX.c:655: fejl: expected ‘{’ at end of input
make: *** [LaTeX.o] Fejl 1


Danish translation:
I filen inkluderet af = in file included by
fejl = error
advarsel = warning

---

### Post by kevdog on 2008-03-13
Where did you get the instructions to compile pidgin, it looks like you are missing some dependencies?

---

### Post by TeXperten on 2008-03-13
From a friend of mine, who has used Linux for a few years.

---

### Post by kevdog on 2008-03-14
If you want to start receiving informative help, then you have to start sharing some information.  Telling me you received instructions from a friend good with linux is no help.  What were the instructions??  Did you install any package dependencies?

---

### Post by aperson on 2008-06-15
Sorry for reviving a dead topic but in case somebody else finds it through the search function:

You have to install the pidgin-dev packages additionally to the normal pidgin package. After that kevdog's instructions work.

---

