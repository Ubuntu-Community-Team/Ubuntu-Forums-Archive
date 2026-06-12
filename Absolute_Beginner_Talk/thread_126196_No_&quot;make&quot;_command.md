---
title: "No &quot;make&quot; command"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-05
I'm trying my hand at installing a "tar" file. I've followed the instructions for doing so that were included in the file.  However, when I enter the "make" command I receive the following: ***bash: make: command not found***.

What am I doing wrong?

Thanks...

---

### Post by BoyOfDestiny on 2006-02-05
sudo apt-get install build-essential

---

### Post by Cousindaddy on 2006-02-05
Thanks.

Will that command also install the program? and if so, where will it appear?

---

### Post by BoyOfDestiny on 2006-02-05
[QUOTE=Cousindaddy]Thanks.

Will that command also install the program? and if so, where will it appear?[/QUOTE]

Basically it will give you most of the tools you need to build applications (i.e. make).

For the app you are trying to build from a tarball...(I'd suggest making sure ubuntu doesn't already have it in the repos, enable universe etc in /etc/apt/sources.list)

./configure (sometimes ./autogen.sh too, if you see it go ahead and run it)
make
make install

You can also use checkinstall to install the application. Just play around with it, if you get any errors during ./configure or make, it will tell you "such and such" is missing. Use synaptic to get these "dependencies".

Anyway best of luck to you, it seems strange at first, but once you get the hang of it, building applications from source is not so bad. :)

---

### Post by Cousindaddy on 2006-02-05
thanks again..

after running ./configure I received the following:
***configure: error: libxml2 needed and xml2-config not found***

can I proceed with ***make*** and then ***make install***?

---

### Post by BoyOfDestiny on 2006-02-05
[QUOTE=Cousindaddy]thanks again..

after running ./configure I received the following:
***configure: error: libxml2 needed and xml2-config not found***

can I proceed with ***make*** and then ***make install***?[/QUOTE]

No problem,

fire up synaptic, and search for libxml. You should see something like libxml2-dev (these dev files are needed). Keep trying, if more things are reported missing, head back to synaptic and search again. A bit of a pain, but it's basically a one time thing.

---

### Post by Cousindaddy on 2006-02-05
I found the tvtime program in the repository...unfortunately, after installing it I find that my cheapo tv card isn't supported...oh well, at least I arrived at a definitive conclusion...which is a first for me...

thanks for your help...

BTW, know of any good TV cards?

---

