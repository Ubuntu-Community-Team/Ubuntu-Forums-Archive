---
title: "New Begginer -- PLEASE HELP"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by smiley1213m on 2006-07-14
I'm a brand new Ubuntu user. I just succesfully installed Ubuntu onto a Pentium 2 computer. I am new to any type of Linux, so what should I do to get started? Can I use ANY of my old apps, games, or programs that I used to run on Windows?:confused:

---

### Post by aysiu on 2006-07-14
Your best bet is to search in Synaptic for native Linux programs. [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) will help you with that.

Otherwise, Wine may help you with some programs. Cedega may help you with games. Crossover Office should cover anything else.

---

### Post by smiley1213m on 2006-07-14
thanks, but i'm still not entirely sure what it all means, can you break it down for me?

---

### Post by aysiu on 2006-07-14
Well, there are native programs designed for each operating system. Mac OS X has its own programs. Windows XP has its own programs. Linux has its own programs. So if you want programs, the first thing you should be looking for are Linux programs.

The first *place* you should be looking for those programs is Synaptic Package Manager, and the link I gave before tells you in detail how to use that to install programs. Do not go to websites and download .tar.gz files unless you need to.

Depending on what programs you used in Windows, native Linux applications may not suit your needs. If that's the case, there are helper applications for running native Windows programs in Ubuntu. One of those programs is called Wine. Another is called Cedega. A third is called Crossover Office.

---

### Post by briguy on 2006-07-14
Find a program called "Synaptic" or "Install New Programs" and it will give you a list of (thousands) of programs to install.  Your old programs will not run on Linux out of the box, but using a program called Wine, you can run many Windows based programs.  Same with Cedega which is geared towards gamers, however you have to pay a monthly fee, I believe.

In general, most of the programs you used to use will have a quality analogue under Linux (for example, instead of MSN Messenger, I use a program called Kopete, OpenOffice replaces Microsoft Office).

You can find more about these programs on the wiki, there's a link at the top right of this screen.

---

### Post by aysiu on 2006-07-14
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by smiley1213m on 2006-07-17
My synaptic package manager only has about 900 things to install. The screenshot I saw on the page you linked me to has 18,000. Why don't I have all of these?

---

### Post by az on 2006-07-17
You need to enable the universe repository.  You may want multiverse and dapper-commercial, too.  See here:
[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by smiley1213m on 2006-07-17
To acces the universe repository, do I need an internet connection? At the moment I don't have one. I'm trying to install a wireless network card intended for windows, and having a lot of trouble doing so.

---

### Post by Bloch on 2006-07-17
You will also need to install multimedia codecs to be able to play mp3s, mpeg videos files, video DVDs (if you have a DVD drive)

Takes a look at this starter guide. It is quite technical, and you can use it as a reference when needed.
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Look up easyubuntu on it - this is a small program which wll install the propriteary multimedia codecs mentioned above. Scan through the starter guide for things that you need to know.

The desktop guide is a more general overview of ubuntu and the main programs that come with it. This document should be read from the beginning on.
[https://help.ubuntu.com/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html)

---

### Post by smiley1213m on 2006-07-17
> **azz said:**
> You need to enable the universe repository.  You may want multiverse and dapper-commercial, too.  See here:
[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Do I need an internet connection for this? If I do, then I won't be able to do ityet. I'm trying to use a wireless network card, but I haven't got it to work yet.

---

### Post by T700 on 2006-07-17
> **smiley1213m said:**
> Do I need an internet connection for this? If I do, then I won't be able to do ityet. I'm trying to use a wireless network card, but I haven't got it to work yet.

You don't need an internet connection to enable the repositories, but you do need one to use them.

Paul

---

### Post by smiley1213m on 2006-07-17
> **T700 said:**
> You don't need an internet connection to enable the repositories, but you do need one to use them.

Paul

So basically, I do need internet to get these repositories, which makes me have more packages in my synaptic package manager?

---

### Post by ProjectGod on 2006-07-17
theres a file on your ubuntu that has a list of urls. all you have to do is edit that file so that an internet capable ubuntu can connect to the http/ftp sites listed in that file and download the necessary packages / software. 

the file is located here>>> /etc/apt/sources.list

---

### Post by briguy on 2006-07-18
> **smiley1213m said:**
> So basically, I do need internet to get these repositories, which makes me have more packages in my synaptic package manager?

That is correct!

---

