---
title: "Compile package"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-12-23
Using Ubuntu 7.10 & wish to compile  the file “avant-window-navigator_0.2.1.orig.tar.gz
”
So I tar it and get to the point shown in the screen dump attached.

As you can see from the terminal process I cannot compile?????

Can you show me where I am missing out?

Thanks

Bernard

---

### Post by vayde on 2007-12-23
you need to be in the directory that you created by extracting that tarball.

cd <name of new directory>

'./configure' technically means 'run the configure script in this directory' and it's not there, hence the error.

---

### Post by bern1939 on 2007-12-23
Thanks your reply but ......

I tarred the .tar.gz file in the directory called 'nav'
That produced a new directory within 'nav' called  -- “avant-window-navigator_0.2.1 
”
But when I cd to that new directory I am getting the following:

bernard@bernard-desktop:~/Desktop/nav$ cd avant-window-navigator_0.2.1 

bash: cd: avant-window-navigator_0.2.1: No such file or directory

bernard@bernard-desktop:~/Desktop/nav$ 


Cannot understand where I am going wrong here!!


Bernard

---

### Post by vayde on 2007-12-23
shoot back another screenshot of your terminal window, and I'll take a look

---

### Post by bern1939 on 2007-12-23
Many thanks
Oh dear this was a typo error !!! Corrected it and used ./configure
All went well until I got the following:

"No package 'pygtk-2.0' found
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details."

That file is not in Synaptic .... where would I find it please.

Thanks again


Bernard

---

### Post by vayde on 2007-12-23
Sometimes the name of a library, and the name of the package which contains the library are very different.  It's frustrating, but that's the way it goes.  I believe the package you are looking for is called 'python-gtk2' try installing that package, and you should be golden.

good luck.

---

### Post by bern1939 on 2007-12-23
Many thanks


Bernard

---

