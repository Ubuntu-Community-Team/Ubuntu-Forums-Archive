---
title: "The command line [Resolved]"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-02-03
OK folks, here's a long story for a little problem.

I'm new to Linux, but I was pretty familiar with DOS' command line. A few commands seem to be the same.  That said I've read a previous post about installing programs and it makes no sense. I know I must change directory to the one the program resides in that I want to install, (just like DOS). In DOS it was just typing in the name of the executable that made it install. 

So in short, I'm just lost about the installation process:( 
Thanks

P.S. It is adobe flash player residing on my desktop
P.P.S. I completely wiped out Windblows and and I love it!

---

### Post by pseudonym on 2007-02-03
Installation instructions for Adobe Flash Player at the [Adobe Flash website]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash").

For installing other software that comes in the Ubuntu repositories, see [this wiki entry]("https://help.ubuntu.com/community/InstallingSoftware?highlight=%28install%29%7C%28software%29"). You will also find [this comprehensive Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") very useful.

HTH

---

### Post by Mba7eth on 2007-02-03
[try this one ]("http://www.unix-tutorials.com/tutorials.php?os=Ubuntu")
just use google and alot you'll find :)

---

### Post by lamego on 2007-02-03
> In DOS it was just typing in the name of the executable that made it install. 
The same applies to Linux, but you need to use ./executable so that the shell knows you want to run the executable from the current (.) directory.

---

### Post by xmastree on 2007-02-03
That's for running the program, I think the OP was talking about *installing* from the .exe file.
In Windows, running the .exe will basically put various files on your computer, in various directories. The exe is basically a self-extracting file.
With linux it's different. An application waiting to be installed will be different, depending on what distro it's meant for. The most popular ones are rpm and deb. Ubuntu uses the dsb format.

So, you download something.deb from the supplier's site, then to install it, you use the **dpkg** command to achieve the same thing.
Something like:
dpkg -x something.deb

---

### Post by lamego on 2007-02-03
> That's for running the program, I think the OP was talking about installing from the .exe file.
No, he was just talking about running a program, and yes, you can will also do the same thing for installers which are linux executables (binary or shell script).

To install .deb files, its better to use:
```
gdebi file.deb
```
Unlike dpkg gdebi handles package dependencies.

---

### Post by jvc26 on 2007-02-03
A few extra pointers for installing stuff:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Il

---

### Post by aysiu on 2007-02-03
If you want to install Adobe's Flash player, follow these instructions (the site also explains what each command does):
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by macruadhi on 2007-02-04
OK, thanks you all. I got that installed. 

Boy, this is a whole new learning curve.

---

