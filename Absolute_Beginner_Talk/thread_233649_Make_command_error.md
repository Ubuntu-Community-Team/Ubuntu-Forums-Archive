---
title: "Make command error"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Betta on 2006-08-10
I am trying to install [Hamachi](http://hamachi.cc). I have downloaded and installed the gnumake program from synaptic package manager, and extracted the hamachi folder. When I run 'sudo make install' inside the folder, it starts working, but then stops. Here is the error I recieve:

> 
betta@FAST:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo make install

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Copying tuncfg into /sbin ..
install: cannot run strip: No such file or directory
install: strip failed
make: *** [install] Error 1


Any help is appreciated.

-Betta

---

### Post by kebes on 2006-08-10
strip is a unix command:
[http://unixhelp.ed.ac.uk/CGI/man-cgi?strip](http://unixhelp.ed.ac.uk/CGI/man-cgi?strip)

Do you have it installed? Try:
$ which strip
To see where it is located (if anywhere!).

If it is not installed, then install it ("sudo aptitude install strip"). If it is already installed, make sure it is on the path. If you type "strip" does the strip command run?

---

### Post by taurus on 2006-08-10
Don't you usually have to do

```

./configure
make
sudo make install

```
Also, make sure you belong to groups adm & admin before you run the sudo command...

```

id

```

---

### Post by Betta on 2006-08-10
@kebes: I tried doing all that you said, it didn't install the strip program because it found programs that had strip in their name, is there anyway to force install it? BTW, here is what my console returned.

> 
betta@FAST:~/Desktop/hamachi-0.9.9.9-20-lnx$ $ which strip
bash: $: command not found
betta@FAST:~/Desktop/hamachi-0.9.9.9-20-lnx$ sudo aptitude install strip
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find package "strip". However, the following
packages contain "strip" in their name:
  v2strip libroxen-stripper stripclub pkgstriptranslations dailystrips
  libchart-strip-perl zope-stripogram
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
betta@FAST:~/Desktop/hamachi-0.9.9.9-20-lnx$ strip
bash: strip: command not found
betta@FAST:~/Desktop/hamachi-0.9.9.9-20-lnx$


@taurus: I tried different methods of getting to configure I tried typing './configure' cd /configure and various other things, all of them are saying there's no such directory, am I missing something?

-Betta

---

### Post by taurus on 2006-08-10
Is there a README or INSTALL at all?  If not, what is the output of this command then?

```
ls -la ~/Desktop/hamachi-0.9.9.9-20-lnx
```

---

### Post by kebes on 2006-08-10
Sorry about that. My mistake. "strip" is part of the GNU Binary Utils:
[http://sourceware.org/binutils/docs-2.17/binutils/index.html#Top](http://sourceware.org/binutils/docs-2.17/binutils/index.html#Top)

I think to install it you need the package "binutils". According to the debian list, "binutils" contains "usr/bin/strip", see here:
[http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=binutils&version=stable&arch=i386](http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=binutils&version=stable&arch=i386)

Installing "gcc" will install "binutils" in addition to a compilers and other useful things, so you may prefer to do that. So try:

$ sudo aptitude install binutils

or

$ sudo aptitude install gcc


Afterwards hopefully "strip" will be installed, and the compile will proceed.

---

### Post by Betta on 2006-08-10
Thank you so much kebes, I got it working, now to just install the GUI for it, heh. Thanks much, this can be closed or whatever you guys do with answered topics.

-Betta

---

