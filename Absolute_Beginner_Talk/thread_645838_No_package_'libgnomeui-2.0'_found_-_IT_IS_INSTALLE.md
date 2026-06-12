---
title: "No package 'libgnomeui-2.0' found - IT IS INSTALLED???"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by xeb07170 on 2007-12-20
I have ran into so many problems trying to install regviewer - and everything else needed to install gtk.

I finally got gtk installed. I was ruunning the confingure command on regviewer and got this message

hecking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (libgnomeui-2.0) were not met:

No package 'libgnomeui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@paul-desktop:~/Desktop/regviewer-0.1#      


-----------------------------------------------------------------------------------------------------------------

I have tried installing this package from the source and also - having looked from answers elsewhere, ran the following;

paul@paul-desktop:~$ sudo -s
[sudo] password for paul:
root@paul-desktop:~# apt-get install libgnome2-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libgnome2-dev is already the newest version.
libgnome2-dev set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@paul-desktop:~#



stumped.............again

---

### Post by odiseo77 on 2007-12-20
Did you install libgnomeui-dev ? This is probably the package you're missing.

---

### Post by nihildeclaro on 2008-05-10
Hi odiseo77; I'm not the original author of this question, but I have to say (to you and others that will find this thread after a Google search) that your solution is correct; I tried to install "configure-trackpoing" from source, and I got a "No package 'libgnomeui-2.0' found" after ./configure. Following your tip, I installed "libgnomeui-dev", and now "configure-trackpoint" is installed and working.

Thanks for your help!

---

### Post by odiseo77 on 2008-05-10
You're welcome!

Tip: Anytime you're compiling a program from source and you get missing dependencies for a given library, you must install the library itself, as well as its headers/development files (for example, if you get "no package python-2.5 found", you must install "python", as well as "python-dev", so you can compile the package.

Anyway, glad you got it working! :)

---

