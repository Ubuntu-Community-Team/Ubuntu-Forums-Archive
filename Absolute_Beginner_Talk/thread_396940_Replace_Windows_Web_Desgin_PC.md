---
title: "Replace Windows Web Desgin PC"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by vatso on 2007-03-30
Hi There

I was wondering if I could us Ubuntu & open source software to replace Windows.

I do web development & use Flash - Will I be able to use Ubuntu to do this work?

If so what applications can I use - thanks I am really wanting to go open source.

---

### Post by nixclusive on 2007-03-30
I don't think Flash is open source!! They might have something to develop on Linux platform as well. ..urrm yeah everything else works fine. ;-)

---

### Post by vatso on 2007-03-30
Will this work on Ubuntu?

[http://linux.softpedia.com/progDownload/Flash-for-Linux-Download-407.html](http://linux.softpedia.com/progDownload/Flash-for-Linux-Download-407.html)

---

### Post by Nolander on 2007-03-30
There is a few flash ripoffs on linux. i suggest trying wine to run macromedia. its a little iffy but still works. the alternative is running window in ubuntu. i personaly do a little of both and i suggest both. and a good alternative to dreamweaver or crimson or notepad is... gEdit the ultimate text editor.

hope you give ubuntu a chance,
Nolander.

---

### Post by octoberdan on 2007-03-30
> **vatso said:**
> Hi There

I was wondering if I could us Ubuntu & open source software to replace Windows.

I do web development & use Flash - Will I be able to use Ubuntu to do this work?

If so what applications can I use - thanks I am really wanting to go open source.

Take a look at some of the google results:
[http://www.google.com/search?hl=en&q=%22flash+development%22+linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=%22flash+development%22+linux&btnG=Google+Search)

---

### Post by vatso on 2007-03-30
I am worried it will not work on Ubuntu, not all linux is the same right - that is what worries me - how do I know it will work?

---

### Post by Gina on 2007-03-30
I use NVu to design and update websites (in Windoze before and now in Ubuntu but I don't use Flash so don't know about that).  Flash is available for Firefox and may be for use with NVu.

Why not try the link posted above for Flash and see?
[B]
A bit later...[/B]  Ah... I've downloaded from that Flash link and see it's in the development stages.  The download will need compiling and installing.  It's not an app that's directly ready to install.  OTOH if you **compile** and **make** in the Ubuntu environment you will make a Ubuntu compatible application.  Not something for a beginner in Linux and not something I'd feel like tackling as new to Ubuntu/Linux myself.

---

### Post by vatso on 2007-03-30
My question then is will that install on Ubuntu is what I want to know, Not all Linux Libs are the same right - that what I need to know??

Is it made for Fedora, Madrake, Slackware.

I am very new to this so need to know if it will install & run on Ubuntu

---

### Post by Burning Bronx on 2007-03-30
It really doesn´t matter as it is just source. Mostly the difference is between the versions of the libs included in the distro so it should compile against what you have. I will try compile it after I get home later on, perhaps make an ubuntu package. 
Keep on rockin´.
Burn.

---

### Post by deuchar1 on 2007-03-30
Do what I did - play it safe and dual-boot. That way you can run Ubuntu for the programming/development side of things and if needs be you can either Wine Flash or jump into Windows if needs be.

---

### Post by gardara on 2007-03-30
Flash MX is supposed to run with CrossOver...

---

### Post by 3rdalbum on 2007-03-30
I congratulate the original poster's knowledge of Linux. It is true that distributions aren't all the same, and that binary packages for one might not install on another.

However, F4L (Flash For Linux) is available only in source code. You can compile source code on pretty much any distribution, and I know from experience that it compiles on Ubuntu.

However, F4L is no longer developed, and it never reached the stage where it could actually be used for anything. I suggest running Flash in Crossover Office or a Windows Virtual Machine.

---

### Post by ieee488 on 2007-03-30
Are you using Flash because you don't know how to code in HTML?

If so, this may be a good time to learn some  HTML/XHTML instead of being held hostage and forced to use software like Flash and Dreamweaver.

---

### Post by deuchar1 on 2007-03-30
> **ieee488 said:**
> Are you using Flash because you don't know how to code in HTML?

If so, this may be a good time to learn some  HTML/XHTML instead of being held hostage and forced to use software like Flash and Dreamweaver.


Flash has its uses, lest we forget. Although it has been widely misused - aesthetic over functionality being the case in point - it still has very good uses in modern design.

---

### Post by vatso on 2007-03-30
Guys thank you so much for all the help - I will use a dual boot - I tried once to do it but my drive went bad - I was told it was because I resized the partition using Ubuntu - I will creat a blank partition & try that?

Flash is very good for some effects you can't do with HTML

---

### Post by Burning Bronx on 2007-03-30
That´s why I always loved how good flash and html can blend. Anyway, I´ve tried Crossover Office and to tell you the truth dual-boot works better for apps of Macromedia calibre. About the Ubuntu drive partitioning/resizing it has never given me problems. However when it comes to dual-boot I always preferred to do it booted from windows (thought that was years ago when I was still using windows... doh).

---

### Post by trent dillman on 2007-03-30
...

---

### Post by octoberdan on 2007-04-06
> **vatso said:**
> Will this work on Ubuntu?

[http://linux.softpedia.com/progDownload/Flash-for-Linux-Download-407.html](http://linux.softpedia.com/progDownload/Flash-for-Linux-Download-407.html)

If it works on one distribution of linux, it *can* generally work on others... some times it just takes a little -f ;-). You'll start running into problems when something is built/packaged for a specific distrib, but in that case they'll probably let you know.

If you want to be a tool you can install Flash 8
[http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)

But if you love freedom as much as I and still want quality, install f4l by following this short hackish tutorial:

**Prepare your system:**
$sudo apt-get install libqt3-compat-headers libqt3-headers libqt3-mt-dev
$sudo ln -s /usr/share/qt3/mkspecs /usr/lib/qt3

**Download and unpack:**
$wget "http://downloads.sourceforge.net/f4l/f4l-0.2.1.tar.bz2?modtime=1135144794&big_mirror=0"
$tar -xvjf f4l-0.2.1.tar.bz2 
$cd f4l-0.2.1

**Patch and make**
On line 140 of src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h change FSDefineSound::FSDefineSound to FSDefineSound
$make
$sudo make install
and you may then have to 
$sudo cp bin/f4l /usr/bin/

**Enjoy!**
$f4l

Good luck and happy geeking.

---

