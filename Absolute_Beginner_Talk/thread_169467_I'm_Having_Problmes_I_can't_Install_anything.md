---
title: "I'm Having Problmes I can't Install anything"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Project_Titan on 2006-05-02
Every time I download somthing and try to Install it. It says Could not open "amsn_0.95-3.ubuntu.deb" Archive type not supported what is that :neutral: I need help I'm a Newbe too ](*,)

---

### Post by testube_babies on 2006-05-02
[QUOTE=Project_Titan]Every time I download somthing and try to Install it. It says Could not open "amsn_0.95-3.ubuntu.deb" Archive type not supported what is that :neutral: I need help I'm a Newbe too ](*,)[/QUOTE]

If the amsn package is on your desktop, open a terminal and type:
```
cd Desktop/
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```

---

### Post by aysiu on 2006-05-02
It's better to install through with a package manager using the repositories.

Graphical guide:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

Text guide:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Project_Titan on 2006-05-02
Lol I'm sorry for asking this but what how do I find where this terminal is Could you like take a snapshot :) or something =/

---

### Post by aysiu on 2006-05-02
[QUOTE=Project_Titan]Lol I'm sorry for asking this but what how do I find where this terminal is Could you like take a snapshot :) or something =/[/QUOTE] The point of the "graphical guide" I linked to is that you don't need the terminal to use a package manager.

If you prefer to use the terminal, see my signature.

---

### Post by sophtpaw on 2006-05-02
[QUOTE=aysiu]It's better to install through with a package manager using the repositories.

[/url][/QUOTE]


But amsn in repos is 0.94 and not the latest 0.95 version, although someone said you can fix the repos, that the amsn site's version was cleaner though?

--
sophtpaw

---

### Post by aysiu on 2006-05-02
[QUOTE=sophtpaw]But amsn in repos is 0.94 and not the latest 0.95 version, although someone said you can fix the repos, that the amsn site's version was cleaner though?

--
sophtpaw[/QUOTE] The title of this thread is "I'm having problems--I can't install anything," not "How do I install the latest version of aMSN?"

The original post doesn't indicate any knowledge of how to use Synaptic, Adept, apt-get, or aptitude. It indicates an end-goal: getting aMSN installed.

It's helpful for new users to get to know the package manager, even if it doesn't have the most up-to-date software (incidentally, Dapper, which gets released next month, does have aMSN 0.95 in the repositories).

That said, it does sound as if 0.95 is worth installing manually: > New features include webcam support, tabbed chat windows, improved skin and plugin support, new file transfer protocol, many new plugins (like Ink and Nudge support), an improved bug report system, as well as LOTS of bugfixes! We hope it was worth all this wait! :)

---

### Post by Project_Titan on 2006-05-02
](*,) still not working it opens up to some text =[ Game over for me =[

---

### Post by aysiu on 2006-05-02
[QUOTE=Project_Titan]](*,) still not working it opens up to some text =[ Game over for me =[[/QUOTE] Please read the two links I posted in the second post of this thread. They will explain everything to you about installing software in Ubuntu.

---

### Post by Project_Titan on 2006-05-02
Yet another stupid problem :twisted:  You Can't Load TkCximage, this is now needed to run amsn. :confused:

---

### Post by Project_Titan on 2006-05-02
:mad:  I really thought this thing was cool all that reading for nothing =/ sorry I have to say this guys but I might as well go Back to Windows Xp =[ I Mean I gave that up just to Install this :mad:  I guess this is goodbye =[

---

### Post by aysiu on 2006-05-02
If you want to give up, give up.

This is what I just tried on my test Ubuntu computer, and it worked. First I downloaded the aMSN Ubuntu .deb from the aMSN website to my desktop: ```
user@ubuntu:~$ **cd Desktop**
user@ubuntu:~/Desktop$ **ls**
amsn_0.95-3.ubuntu.deb
user@ubuntu:~/Desktop$ **sudo dpkg -i amsn*.deb**
Selecting previously deselected package amsn.
(Reading database ... 78065 files and directories currently installed.)
Unpacking amsn (from amsn_0.95-3.ubuntu.deb) ...
dpkg: dependency problems prevent configuration of amsn:
 amsn depends on tcltls; however:
  Package tcltls is not installed.
dpkg: error processing amsn (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amsn
user@ubuntu:~/Desktop$ **sudo apt-get install tcltls**
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  tcltls
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 66.3kB of archives.
After unpacking 287kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com breezy/universe tcltls 1.5.0-2 [66.3kB]
Fetched 66.3kB in 1s (38.9kB/s)

Preconfiguring packages ...
Selecting previously deselected package tcltls.
(Reading database ... 79006 files and directories currently installed.)
Unpacking tcltls (from .../tcltls_1.5.0-2_i386.deb) ...
Setting up tcltls (1.5.0-2) ...

Setting up amsn (0.95-3) ...
``` The bold type is the stuff I had to type in.

It's even easier if you don't need version 0.95. As long as you [have extra repositories enabled](http://www.psychocats.net/ubuntu/sources), just type: ```
sudo apt-get update && sudo apt-get install amsn
``` Note that the first method (for version 0.95) needs the command-line. The second method (for version 0.94) can be done easily via the command-line (as demonstrated) but can also be done through point-and-click (including the part about enabling extra repositories).

Well, if you're really gone, bye. Otherwise, maybe this will help. Good luck with whatever you use.

---

