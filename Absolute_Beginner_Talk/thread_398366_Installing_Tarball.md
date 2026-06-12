---
title: "Installing Tarball"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-03-31
Guys, what am I doing wrong?  I download Livious.tar.gz (an icon theme).  I open terminal and cd to the directory the file is in.  I do: 
tar xvzf Livious.tar.gz

and a folder named Livious is created.  I check in there and there is nothing in the readme about intalling it.  So I go on to cd into the Livious folder, and then:
./configure.

I get bash: /home/bruce/Livious$: No such file or directory

The website I am following says not to worry if this doen't work, ([http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html))

So I go on to:
bruce@bruce-desktop:~/downloads/Livious$ sudo checkinstall

and I get:
sudo: checkinstall: command not found

So I try:
bruce@bruce-desktop:~/downloads/Livious$ sudo make install

and get:
make: *** No rule to make target `install'.  Stop.

So I try:
bruce@bruce-desktop:~/downloads/Livious$ make

and get:
make: *** No targets specified and no makefile found.  Stop.


This shouldn't be that hard to do.  I must be missing something basic here, but as I am still new to linux, I cannot see it.  Help!

Thanks,
Ziffnabb

---

### Post by Maestro23 on 2007-03-31
Take a look at Section 4: Installing from source: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Will shed some light on things.  Good luck.

---

### Post by WW on 2007-04-01
A theme does not contain any programs that must be compiled, so those links are not relevant.  Just save the file somewhere, and then run System->Preference->Theme.  Then click on Install Theme, use Browse to find and select the file livious.tar.gz, and then click on Install.

To use the Livious icon theme, click on Theme Details, and then click on the Icons tab.  Livious should be one of the options in the list.

---

### Post by Maestro23 on 2007-04-01
> **WW said:**
> A theme does not contain any programs that must be compiled, so those links are not relevant.  Just save the file somewhere, and then run System->Preference->Theme.  Then click on Install Theme, use Browse to find and select the file livious.tar.gz, and then click on Install.

To use the Livious icon theme, click on Theme Details, and then click on the Icons tab.  Livious should be one of the options in the list.

Didn't notice it was a theme. Good catch.

Yeah, just save that link for future reference on other issues.

---

