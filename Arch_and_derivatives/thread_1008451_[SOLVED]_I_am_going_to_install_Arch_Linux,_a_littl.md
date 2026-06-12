---
title: "[SOLVED] I am going to install Arch Linux, a little help please!"
date: 2008-12-11
forum: Arch and derivatives
---

### Post by gjoellee on 2008-12-11
Hi, I have been walking in circles around Arch Linux because of all the good comments I have heard about i. I am willing to use time on learning how to use a new distro, but there are some things I would like to know...

1. Can anyone give me a howto (with screenshots) showing how to install Arch Linux 2008.6
2. When I am finished installing I would like to install XFCE how?
3. Can anyone give me a quick tour of Pacman package manager
4. Is there something else I should know about?

---

### Post by smartboyathome on 2008-12-11
> **gjoellee said:**
> Hi, I have been walking in circles around Arch Linux because of all the good comments I have heard about i. I am willing to use time on learning how to use a new distro, but there are some things I would like to know...

1. Can anyone give me a howto (with screenshots) showing how to install Arch Linux 2008.6
2. When I am finished installing I would like to install XFCE how?
3. Can anyone give me a quick tour of Pacman package manager
4. Is there something else I should know about?

1. Theres no screenshots (the installer is text-based), but theres a beginners guide included on the CD in /arch/beginnersguide.txt.
2. See the beginners guide, it will tell you how.
3. Here's my pacman aliases (which are a basic tour in itself):
```
alias install='pacman -S'
alias update='pacman -Sy'
alias upgrade='pacman -Syu'
alias remove='pacman -R'
alias search='pacman -Ss'
alias pkg-info='pacman -Si'
alias list-files='pacman -Ql'
alias install-local='pacman -U'
```
4. It may seem hard at first, but the hardest thing that I found with it was wireless (and that is because my wireless doesn't work that well with it :p). Its quite simple really.

---

### Post by markp1989 on 2008-12-11
i would have a look here, 
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by sub2007 on 2008-12-11
The answer to all your questions are in the Wiki, it's well worth becoming familiar with it - you will be referring to it constantly whilst you use Arch.

wiki.archlinux.org

Start with the Beginners guide, then everything else you need will be elsewhere on the Wiki. Always make sure you read the wiki, read the forums and search Google if you get stuck on something.

---

### Post by smartboyathome on 2008-12-11
> **sub2007 said:**
> The answer to all your questions are in the Wiki, it's well worth becoming familiar with it - you will be referring to it constantly whilst you use Arch.

Or, if you're like me, you will be referring to it constantly even when *not* on Arch! :p

---

### Post by chucky chuckaluck on 2008-12-11
+1 for the wiki. [http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)
i got useful info out of both the official guide *and* the beginner guide. the only thing i found a little puzzling was installing X.

---

### Post by gjoellee on 2008-12-11
packages could not be installed because one package was corrupted the name was something as "libusb", may it be a defect on the DVD causing this corruption, as well there where something wring with md5sums.

---

### Post by sub2007 on 2008-12-11
Are you following the beginner's guide? What stage of the install are you stuck at and what exact error messages are you getting? Also are you doing FTP (network) install or core install?

---

### Post by bapoumba on 2008-12-11
Moved to Arch.

---

### Post by handy on 2008-12-11
Here is a movie on the installation:

***_[http://video.google.co.uk/videoplay?docid=6213347420565640601](http://video.google.co.uk/videoplay?docid=6213347420565640601)_***

---

### Post by OutOfReach on 2008-12-11
Please look and follow the Beginner's Guide and Installation Guide.
It answers pretty much all of your questions, and will make installing Arch much easier.

---

### Post by Rumor on 2008-12-11
> **gjoellee said:**
> Hi, I have been walking in circles around Arch Linux because of all the good comments I have heard about i. I am willing to use time on learning how to use a new distro, but there are some things I would like to know...

1. Can anyone give me a howto (with screenshots) showing how to install Arch Linux 2008.6
2. When I am finished installing I would like to install XFCE how?
3. Can anyone give me a quick tour of Pacman package manager
4. Is there something else I should know about?

1. There are a few "reviews" of Arch that will show you some of the installation screenshots. Miggol's website has a video of the installation process: [http://archux.com/](http://archux.com/)

2. pacman -S xfce - wiki for it is here: [http://wiki.archlinux.org/index.php/Xfce](http://wiki.archlinux.org/index.php/Xfce)

3. Wiki for pacman is here: [http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)

4. Yes, the wiki is here: [http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page) :p

The documentation at the wiki is excellent. It will answer most of your questions. Have fun building your Arch!

---

### Post by crimesaucer on 2008-12-12
> **gjoellee said:**
> Hi, I have been walking in circles around Arch Linux because of all the good comments I have heard about i. I am willing to use time on learning how to use a new distro, but there are some things I would like to know...

1. Can anyone give me a howto (with screenshots) showing how to install Arch Linux 2008.6
2. When I am finished installing I would like to install XFCE how?
3. Can anyone give me a quick tour of Pacman package manager
4. Is there something else I should know about?


1.) This is an old guide with screenshots (10 pages): [http://www.raiden.net/?cat=2&aid=276&pid=2](http://www.raiden.net/?cat=2&aid=276&pid=2) 

The main thing that has changed in the Arch install since that guide was written was the part on this page: [http://www.raiden.net/?cat=2&aid=276&pid=7](http://www.raiden.net/?cat=2&aid=276&pid=7) 

The section talking about editing the "community current extra release unstable" files found in /etc/pacman.d  is not needed anymore..... so all you have to do is edit the "mirrorslist" located in /etc/pacman.d....

Just read through this guide to see how an install looks with no gui and only nano for a text editor.


2.) You can install Arch using only xfce4 or have it with gnome or whatever. Read this xfce4 page: [http://wiki.archlinux.org/index.php/Xfce4#How_to_Install_Xfce](http://wiki.archlinux.org/index.php/Xfce4#How_to_Install_Xfce)


3.) Pacman is very simple to use. Check the man pages with man pacman or read this wiki: [http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)


4.) Maybe try the FTP install to save time: [http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Pre-Installation](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Pre-Installation)

[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Configure_Network_.28FTP_Install_only.29](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Configure_Network_.28FTP_Install_only.29)

---

### Post by chucky chuckaluck on 2008-12-12
if you haven't found out already, as an end user, i was nervous about installing arch because of all the warnings about it being hard and not for beginners, but i found those warnings to be mostly not true. it's more detailed, but not harder. in fact, i think the documentation makes it almost idiot proof (i was pretty drunk the first time i installed arch).

---

### Post by gjoellee on 2008-12-12
Thanks...

---

