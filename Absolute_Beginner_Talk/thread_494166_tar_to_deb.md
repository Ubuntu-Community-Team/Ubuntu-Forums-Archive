---
title: "tar to deb"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-06
how do u convert tar to deb

---

### Post by Bachstelze on 2007-07-06
You don't.

[img]http://fkraiem.no-ip.org/stuff/why.jpg[/img]

---

### Post by twiceasworn on 2007-07-06
Just like i replied in your previous thread, you can't.  You must untar and unzip "tar -xjf filename.tar.bz2" and then compile the program.  make compile  make install.

Though I like Hymntolife's response more.

---

### Post by zerobinary on 2007-07-06
lol response but i can't find make
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-1-2.png[/IMG]

---

### Post by twiceasworn on 2007-07-06
Within the files that you unpackaged there should be a compile script with it.  run that.

---

### Post by Raineer on 2007-07-06
I've had install files end in .pl,  you could try that one, or just see if tuxrip will run there.  Also look in that directory, it looks like a document directory, could have a hint there

---

### Post by shrift on 2007-07-06
There is not a way to simply convert a .tar to a .deb, they are completely different types of files. A .tar is an archive format, a .deb is a package format, that is something that your OS understands do be an application ready for it to install.

Most applications that are not already packaged some from a .tar, if your question is how can you make an application source that is in a .tar file into a package instead of simply "make install"-ing it, then you can use checkinstall.

So when your compiling the program do whatever the maintainers say to compile, but when you get to "sudo make install" use "sudo checkinstall" instead. Make sure that checkinstall is installed. "sudo aptitude install checkinstall".

Checkinstall is fairly straightforward. It will usually work, it has the benefits of packaging your programs so that you can manage them with aptitude. 

Other than that, I believe you would have to get into rather complex debian packaging.

---

### Post by avik on 2007-07-06
EDIT: I should have refreshed before posting!  Ignore me for now, remember this post if you find yourself needing to compile something. :p

The standard procedure for compiling a program in GNU/Linux (and other UNIX/UNIX-like systems) is as follows (in the extracted directory):

```

./configure
make
sudo make install

```

---

### Post by zerobinary on 2007-07-06
how do u install python files that ends with pl

---

### Post by p_quarles on 2007-07-06
Also, there and English and French language pages that give detailed instructions on installing Tuxrip from source. There's also a link to a Debian package, but alas the link is broken. Try googling it, and you'll find step-by-step instructions.

---

### Post by twiceasworn on 2007-07-06
Ah, I couldnt remember the exact syntax for Linux (I work on FreeBSD machines all day long :) ).

edit: also, a file ending in .pl is typically a perl script.

---

### Post by zerobinary on 2007-07-06
i basically need the dependency for python files but i don't know which one
err i thought is python so is perl but i need the dependency in order to install it which i don't have 
where can i find it
zerobinary@zerobinary-desktop:~/Desktop$ cd /home/zerobinary/Desktop/tuxrip/zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ python tuxrip install  File "tuxrip", line 5
SyntaxError: Non-ASCII character '\xe0' in file tuxrip on line 5, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details
zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ python trasperl.pl install
python: can't open file 'trasperl.pl': [Errno 2] No such file or directory
zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ python transperl.pl install  File "transperl.pl", line 7
SyntaxError: Non-ASCII character '\xe9' in file transperl.pl on line 7, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details

---

### Post by dylan623 on 2007-07-06
This is why everyone should distribute their sofware as deb and rpm. It's much more newbie-friendly...

---

### Post by zerobinary on 2007-07-06
lol
but i still needed the dependence and is not in getdeb.net
zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ perl tuxrip install
+------------------+
| TUXRIP v0.98     |
+------------------+

Language file not detected, which language do you want to use (en/fr/sp) ?
en
Unknown option : install, will be ignored...
Missing program(s) : 
 mplayer
 mencoder
 transcode
 tcprobe
 avimerge
 tccat
 tcextract
 tcdecode
 tcscan
 oggenc
 dvdxchap
do u do this when u want to install it all the same time sudo apt-get install mencoder transcode tcprode avimerge tccat tcextract tcdecode tcscan oggenc dvdxchap
Make sure you have the 'universe' component enabled
how do u enable universe component

---

### Post by p_quarles on 2007-07-06
> **dylan623 said:**
> This is why everyone should distribute their sofware as deb and rpm. It's much more newbie-friendly...
You got it backwards. That's why newbies shouldn't install unpackaged software.

Debian and Red Hat packages are a lot of additional work that has to occur after the development of the software itself. Developers make it available when the source code (which is usually in a high-level language that can't communicate directly with any computer) is finished so that you can compile it if you want to; no one's forcing you.

---

### Post by zerobinary on 2007-07-06
come one deb and rpm makes life is easier

---

### Post by shrift on 2007-07-06
Zerobinary, have you ever compiled anything before?

---

### Post by zerobinary on 2007-07-06
yeah a long time ago
more like an century ago
Unknown option : install, will be ignored...
Missing program(s) : 
 oggenc
 dvdxchap

zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ sudo apt-get install oggenc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package oggenc
zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ sudo apt-get install dvdxchap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dvdxchap

---

### Post by shrift on 2007-07-06
Ok, first of all install build-essential. "sudo aptitude install build-essential". When compiling program from source dependencies usually mean you need the development libraries for the listed dependencies whenever available. So for tuxrip I see that they say you need to have libogg installed. So in ubuntu you run "sudo aptitude install libogg-dev" that is the development library. 

Search aptitude for packaged files of the dependencies they list. Something like this: "aptitude search libogg libvorbis libdvdread transcode ogmtools ffmpeg mplayer"

Then look at the results install the development libraries where available, in the other places install the program. Like for mplayer, it doesn't need the dev files, it needs to have mplayer installed. So just install the mplayer package.

Does that help?

---

### Post by zerobinary on 2007-07-06
err but i don't really get what is aptitude search libogg libvorbis libdvdread transcode ogmtools ffmpeg mplayer" do again and why is it useful
Unknown option : install, will be ignored...
Missing program(s) : 
 oggenc
 dvdxchap
zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ sudo aptitude search dvdxchap
zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ sudo aptitude search dvdxchap
zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ aptitude search dvdxchap
zerobinary@zerobinary-desktop:~/Desktop/tuxrip$ sudo aptitude search oggenc zerobinary@zerobinary-desktop:~/Desktop/tuxrip$

---

### Post by shrift on 2007-07-06
I see. The tux rip files are already compiled. You just need to type ./tuxrip form a terminal when your in the directory you extracted it to.

aptitude is a package management program. Ubuntu uses packages called .debs to manage software that is installed, + the installation of new software. The command "aptitude search" searches your current repositories for available software packages. Everything after "aptitude search" is what your searching for. So "aptitude search packagex" searches your repositories for packages called "packagex"

However you do not need to compile your program so my last post is irrelevant.

I looked at the website for tuxrip and downloaded it. Look at this page for how to use it now that you have extracted it.

[http://tuxrip.free.fr/configuration_en.html]("http://tuxrip.free.fr/configuration_en.html")

---

### Post by zerobinary on 2007-07-06
still missing the package
Missing program(s) : 
 oggenc
 dvdxchap

---

### Post by p_quarles on 2007-07-06
> **zerobinary said:**
> come one deb and rpm makes life is easier
Absolutely, but that's not the point. No one could ever make distro-specific packages if the developers didn't release the source code.

---

### Post by zerobinary on 2007-07-06
yeah which is y it is kind of sux 
 	still missing the package

-->All tuxrip options are void.
-->Config mode : The preference file will be generated...
-------> Working directory [default : /space] ? >
what do i do next
what do they mean by working directory
and what if my dir is like this  /media/84/Documents and Settings/Administrator/Desktop/[a4e]Witch_Hunter_Robin_01-26/[a4e]Witch_Hunter_Robin_01[Divx5.2].mkv
aka in window xp

---

### Post by shrift on 2007-07-06
zerobinary, you need to be more specific. Repeatedly posting ```
Missing program(s) :
oggenc
dvdxchap
``` does not help. What are you trying to do when you get that error? Please copy all the lines leading up to that error as well as the error, just like you see them in your terminal.

---

### Post by zerobinary on 2007-07-06
k that problem is solved 
->All tuxrip options are void.
-->Config mode : The preference file will be generated...
-------> Working directory [default : /space] ? >
what do i do next
what do they mean by working directory
and what if my dir is like this /media/84/Documents and Settings/Administrator/Desktop/[a4e]Witch_Hunter_Robin_01-26/[a4e]Witch_Hunter_Robin_01[Divx5.2].mkv
aka in window xp but i have ntfs thing installed which i can edited it

---

### Post by shrift on 2007-07-06
> **zerobinary said:**
> yeah which is y it is kind of sux 
 	still missing the package

-->All tuxrip options are void.
-->Config mode : The preference file will be generated...
-------> Working directory [default : /space] ? >
what do i do next
what do they mean by working directory
and what if my dir is like this  /media/84/Documents and Settings/Administrator/Desktop/[a4e]Witch_Hunter_Robin_01-26/[a4e]Witch_Hunter_Robin_01[Divx5.2].mkv
aka in window xp

Look at this page [http://tuxrip.free.fr/configuration_en.html]("http://tuxrip.free.fr/configuration_en.html")

It has info on the configuration.

---

### Post by zerobinary on 2007-07-06
not tell me this a a terminal app
and how do i know this 
DVD device
	Enter the device path /dev/ corresponding to your DVD drive.
/dev/what

---

### Post by shrift on 2007-07-06
zerobinary I do not think this app is for you. If you are interested in ripping DVDs to your hard drive I would recommend an alternative with a gui. Like thoggen. enter this command in a terminal to install it:
```
sudo aptitude install thoggen
```

To help find what device your dvd drive is try typing this command in a terminal:
```
ls -l /dev/ | grep dvd
``` you should get something similar to this in return:
```
bmartens@ender:~$ ls -l /dev/ | grep dvd
lrwxrwxrwx 1 root     root             4 2007-07-06 11:35 dvd -> scd1
lrwxrwxrwx 1 root     root             4 2007-07-06 11:35 dvd1 -> scd0
lrwxrwxrwx 1 root     root             4 2007-07-06 11:35 dvdrw -> scd1
bmartens@ender:~$ 

```

The item that is "dvd ->" is probably your device. so for me it would be /dev/scd1. You can also simply try "/dev/dvd"

---

### Post by zerobinary on 2007-07-09
zerobinary@zerobinary-desktop:~$ ls -l /dev/ | grep dvd
lrwxrwxrwx 1 root root           4 2007-07-09 10:59 dvd -> scd1
lrwxrwxrwx 1 root root           4 2007-07-09 10:59 dvdrw -> scd1
is this similar and can this app burn ogm and mkv

---

### Post by shrift on 2007-07-09
> **zerobinary said:**
> zerobinary@zerobinary-desktop:~$ ls -l /dev/ | grep dvd
lrwxrwxrwx 1 root root           4 2007-07-09 10:59 dvd -> scd1
lrwxrwxrwx 1 root root           4 2007-07-09 10:59 dvdrw -> scd1
is this similar and can this app burn ogm and mkv

I'm not sure what application you are referring to. As for the output that you gave me, you'll want to use /dev/scd1 for the configuration of the applicatio you were trying to get working earlier.

---

### Post by zerobinary on 2007-07-09
i mean the app u tell  me to install the output code thingie thoggen

---

### Post by shrift on 2007-07-11
Thoggen is an entire application of it's own, not output code.... It only RIPS DVDs, meaning it copies them to your hard drive. It does not "make" DVDs.

---

### Post by zerobinary on 2007-07-30
don't make dvd but i need to make dvd

---

### Post by shane2peru on 2007-08-03
```

sudo aptitude install devede

``` 
That is your DVD making program.  Easy to use too.

Shane

---

