---
title: "How do I install programs NOT in a deb?, or How to make from a tar.gz?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by mike_m on 2007-09-05
ok I've searched & searched...
How do Install or "make" software from a tar.gz?

I have found some programs on  gnomefiles.org that are not in deb's but tar.gz (also not in Synaptic)
I can untar (unzip) them, but then what?

Please remember I'm an old windows user where you click an .exe & the program gets installed.

I will learn the term, but need help.

Lets start with "pysnippet-1.3.tar.gz" on my desktop (/home/mike/Desktop/pysnippet-1.3.tar.gz)
the "readme" file is no help.

A list of commands is what I'm looking for so I don't have to keep asking.

PS, what is make?
what is automake?
I installed "checkinstall" is that good?

PSS, I know Ubuntu has 3500 packages, but sometimes a new one can be found that is just "what your looking for"

=========
Thanks for helping -- Mike

---

### Post by splintercellguy on 2007-09-05
make is a utility that parses makefiles in order to build the tarball. A read from the README or INSTALL file in the tarball helps, but usually, you would do:

./configure
make
sudo make install

checkinstall is a utility that allows you to create a deb package from the tarball. If you want to be able to manage the application using Synaptic, you would do:

./configure
make
sudo checkinstall

---

### Post by deadgobby on 2007-09-05
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
 Some tar files or known as building from source. You may need to install depends before going on installing a tar or RPM. Just check in synaptic first before install from source or a RPM

Gobby

---

### Post by LaRoza on 2007-09-05
> **mike_m said:**
> ok I've searched & searched...

Please remember I'm an old windows user where you click an .exe & the program gets installed.

I will learn the term, but need help.

Lets start with "pysnippet-1.3.tar.gz" on my desktop (/home/mike/Desktop/pysnippet-1.3.tar.gz)
the "readme" file is no help.

A list of commands is what I'm looking for so I don't have to keep asking.


Windows uses .msi for installations usually, not .exe.

Usually, the command will be given for each app, but I will explain what "pysnippet-1.3.tar.gz" is.

It is a tar file that is gzipped ("gzip", is similar to zip from Windows). A tar file is an archive format.

To use whatever the contents are, you will have to gunzip (unzip) and untar. 

[http://www.gzip.org/](http://www.gzip.org/) may help, it has almost everything you asked in it.

---

### Post by Kingsley on 2007-09-05
First, install automake and build-essential from Synaptic.

The next step is to uncompress your tar.gz or whatever. Then use cd to move into the directory it creates. The usual steps for installation are
```

./configure
make
sudo make install

```

---

### Post by mike_m on 2007-09-05
Thanks all - I tried them but will have to retry.
the links from deadgobby were good, Kingsley's "install automake and build-essential" helped,   -- LaRoza > Windows uses .msi for installations usually, not .exe.
I understand what you are trying to say, but .msi begain with WinXP, or atleast I never saw a  .msi before XP, I always installed with "setup.exe, install.exe, youNameit.exe" in Win95, Win98, WinXp (*this not a flame, just my point of view, thanks for helping)

Thanks again, all, Mike

PS. clicking a .deb is so much easier!

---

### Post by _samba_ on 2007-09-05
To gunzip run this:
**gunzip < pysnippet-1.3.tar.gz | tar xvf -**
and you will find a folder with the name of your archive.


Before installing it you may need to setup your desktop for that:
**apt-get install python python-gtk2-dev python-gnome2 python-gnome2-dev**


This is from readme file:

3. Installing it
You need pygtk ([http://www.pygtk.org](http://www.pygtk.org)) and python ([http://www.python.org](http://www.python.org)) in
order to run PySnippet. After installing them, run:

python setup.py install

4. Using PySnippet
Run pysnippet.py:
  pysnippet.py
  or
  python pysnippet.py
----------------------------------



Oh BTW .msi(2000/xp/2003) and .exe(95/98/me/2000/xp/2003) they have the same purpose.

---

### Post by Majorix on 2007-09-05
You can't find packages? No wonder:
> **mike_m said:**
> 
PSS, I know Ubuntu has **3500 packages**,


Ubuntu has about 24k packages. I tend to think you don't have any additional repos enabled. Enable them please using this method:
-System > Admin > Software Sources and enable all the repos there. Also enable the update repos.
-Go to /etc/apt/sources.list and make sure there is no lines starting with deb left there as comments.

If you still can't find a package, go to [www.getdeb.net](www.getdeb.net) and you will most likely find what you are looking for.

---

### Post by mike_m on 2007-09-05
Majorix, I do have all repos enabled, I just missed spoke, thanks for the getdeb.net tip.

---

### Post by mike_m on 2007-09-06
Thanks again all, I'm so glad there's this forum!

---

### Post by mike_m on 2007-09-10
> **_samba_ said:**
> To gunzip run this:
**gunzip < pysnippet-1.3.tar.gz | tar xvf -**
and you will find a folder with the name of your archive.


Before installing it you may need to setup your desktop for that:
**apt-get install python python-gtk2-dev python-gnome2 python-gnome2-dev**


This is from readme file:

3. Installing it
You need pygtk ([http://www.pygtk.org](http://www.pygtk.org)) and python ([http://www.python.org](http://www.python.org)) in
order to run PySnippet. After installing them, run:

python setup.py install

4. Using PySnippet
Run pysnippet.py:
  pysnippet.py
  or
  python pysnippet.py
----------------------------------

:) Yay I got PySnippet installed! Thanks _Samba_ , & everyone else!

---

