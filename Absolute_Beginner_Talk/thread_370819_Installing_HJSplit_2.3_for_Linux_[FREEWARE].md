---
title: "Installing HJSplit 2.3 for Linux [FREEWARE]"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-02-26
I've used this program for years on WinDoze and would miss it if I could not use it with Ubuntu.

It's just one of those programs that is tiny and just works :)

I was using the GNOME desktop and have moved over to XFCE (Xbuntu) and wondered if this was still usable?

Some help would be appreciated .... btw they also have some other Freeware Linux applications available on their site.

Here's the info:

Freeware Linux file splitter with full graphical user-interface  on Gnome and KDE. 
Compatible with the other HJSplit versions.

[img]http://www.freebyte.com/images/hjsplit/hjsplitlx_screen1.png[/img]

**Please note that a Kylix library needs to be installed on your computer before running HJSplit for Linux. You can conveniently download the Kylix library below.**

Download HJSplit: hjsplitlx.tar.gz (337 Kb)

```


http://www.treepad.net/download/hjsplitlx.tar.gz


```

Download: Kylix library

```


http://www.freebyte.com/linux/libraries/


```


Download

The libraries needed to run Freebyte's software for Linux are contained inside kylixlibs3-borqt-3.0-2.tar.gz (2453 Kb).

```


http://prdownloads.sourceforge.net/kylixlibs/kylixlibs3-borqt-3.0-2.tar.gz?download


```


Alternative download location: kylixlibs.sourceforge.net.

```


http://kylixlibs.sourceforge.net/down.html


```

Installation

After unpacking the .tar.gz archive, run "./install.sh" and the necessary libraries will be installed into the directory /usr/lib/kylix3.

---

### Post by chrome307 on 2007-02-26
Found a workaround ............ just downloaded the WinDoze exe file and then used it with WINE.

Works well :)

---

### Post by tralala on 2007-07-23
were do i type the run command (I'm lost windows was easier)

---

### Post by RomeReactor on 2007-07-23
Hi. To run commands, open a terminal (Applications->Accessories->Terminal).

However, I find LXSplit much easier to install. Just a warning, though: LXSplit is **command line only**, as opposed to HJSplit which does provide a graphical interface. 

You'll need to compile it, so you need **build-essential** installed:
```
sudo apt-get install build-essential
```
after that, you have to get the [.tar.gz archive]("http://www.freebyte.com/download/lxsplit.tar.gz"):
```
wget http://www.freebyte.com/download/lxsplit.tar.gz
```
now to extract the contents:
```
tar -xvvzf lxsplit.tar.gz
```
go inside the extracted directory:
```
cd lxsplit-0.1.1
```
and
```
make
```
finally
```
sudo make install
```
----------------------------------------------
To split a file in files of 15 MB:
```
lxsplit -s FILENAME.EXT 15M
```

to join files:
```
lxsplit -j FILENAME.EXT.001
```
changing the FILENAME.EXT to the actual name of the file and its extension.

---

### Post by asmoore82 on 2007-07-23
the 'dd' command line utility can split files and 'cat' can put them back together again.

The BEST thing about this method is these commands will be available on every Linux, BSD, UNIX and Mac OS X machine so learning to use them might make your life a little easier instead of installing some splitter on every machine.

check out the manual page for 'dd'  ... In a terminal ...
```
~$ man dd
```

EDIT: I'm just curious but why do you need to split files??

---

### Post by RomeReactor on 2007-07-23
Most people use HJSplit and LXSplit not to split files, but to join them, particularly video files. In this case **cat** only works for mpg files.

---

### Post by rharris on 2007-07-23
For those among us with Java, there is a java version of HJSplit which works very well. I've used it with no probs what so ever.

[http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)

Cheers..........

Rob

---

### Post by palemmo on 2007-12-15
I quote RomeReactor, lxsplit is more easier, also because new version via wine crash and the new linux is impossible to install... command line for ever :guitar:

---

### Post by LetsLinux on 2008-01-03
Yes... I've recently jumped back on the linux wagon again - af I threw it out earlier this year... Commandlines are great!!!

---

