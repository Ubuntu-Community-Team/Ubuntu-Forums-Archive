---
title: "Installing things manually"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Th3Futur3 on 2006-08-20
Well I learned about my Xubuntu now but the one thing I don't know what to do is to install a program manually, without using the package manger. I want to download this[http://www.gnomefiles.org/app.php/Gpredict]("http://www.gnomefiles.org/app.php/Gpredict")
but I dont know how to install it once I download it. Thanks in advance.

---

### Post by meng on 2006-08-20
Installing from source, see section 4:
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by Th3Futur3 on 2006-08-20
Ok i followed the source directions and install build essential but when i type in my zip file on my desktop in the command line it still dont work. I type in this......tar -xvzf gpredict.0.5.99.7.tar.gz and hit enter and it says error no such directory.

---

### Post by Th3Futur3 on 2006-08-20
Am I supposed to extract the files or just keep it in the tar.gz?

---

### Post by meng on 2006-08-20
Wait, what directory are you in when you type tar -xvzf ...(etc)?
Are you in the same directory as the downloaded file?

---

### Post by Th3Futur3 on 2006-08-20
When I downloaded the file I saved it on my desktop. I didnt extract it to anywhere. I just kept it a tar.gz on my desktop, and the syntax tar -xvzf gpredict.0.5.99.7.tar.gz wasent working.

---

### Post by meng on 2006-08-20
try:
cd Desktop
(actually this assumes you are in your own home directory, otherwise type: cd ~/Desktop)

then tar -xvzf (etc.)

You have to be in the same directory as the file you are unzip/tar-ing

BTW, as a shortcut, you can type
tar -xvzf gpred
and then press TAB to autocomplete the filename. Of course, the autocompletion won't work unless the file in question exists in the working directory.

If you're ever unsure which directory you are in
pwd
will print working directory.

---

### Post by Th3Futur3 on 2006-08-20
Well I typed in Cd desktop in the terminal on the desktop and nothing happened it still says no such directory. As of right I know i have the tar.gz on my desktop unextracted. Could you give me a walktrhough plz, Sorry that im a noob but I just want to learn to how to install from source.

---

### Post by meng on 2006-08-20
Well it has to be 
cd Desktop
for a start. Linux is case-sensitive, you can't get creative about upper/lower case.
If you did type it into your terminal correctly the first time, then something's not quite right. Try ls Desktop to see what's in that directory.

---

### Post by Th3Futur3 on 2006-08-20
Ok i got to it but when i type in sudo make install it says STOP. No rule to make target install.

---

### Post by Th3Futur3 on 2006-08-20
What directory should I put it in?

---

### Post by meng on 2006-08-20
Not every source install needs the full ./configure, make, sudo make install sequence.

Looking into your particular program, the suggestion from the README is as follows:

Furthermore, you should not install it system wide but use an installation
location in your home diretory, for example

./configure --prefix=/home/username/gpredict-rte

The answer, therefore, is that you can put it in pretty much any directory that you want, so long as you will remember to run it from there.

---

### Post by Th3Futur3 on 2006-08-21
Ok i had it running smoothly but this is what happened when i typed in configure

alex@alex-linux:~/Desktop$ gpredict-0.5.99.7/configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

---

### Post by Th3Futur3 on 2006-08-21
Ok well Im almost got it installed until this last thing came up. If i can get past this I can install it. Heres what it says in my terminal.

No package 'gtk+-2.0' found
No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by Th3Futur3 on 2006-08-21
Can comeone tell me how to get gtk2 and glib 2.0?

---

### Post by Th3Futur3 on 2006-08-21
Ok I ran /configure and it finished fine and put all these things on my desktop. After I run configure im not sure what to do. I did make and makefile and it said no such directory even though its right on my desktop.

---

### Post by Th3Futur3 on 2006-08-21
bump

sorry im getting really inpateint ive been trying to install this for 2days now.

---

