---
title: "configure glib error with gnucash"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by danshumaker on 2008-01-08
Hi,
Totally new to ubuntu.  Not sure what to do with this error from the configure script from gnucash (which I'm trying to install on gusty).  I'm trying to install gnucash.2.2.3.
```

checking for GLIB - version >= 2.6.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB >= 2.6 is required to build Gnucash; please make sure you have the
*** development headers installed. The latest version of GLIB is
*** always available at ftp://ftp.gnome.org/pub/gnome/sources/glib/.

```
[-o<
However when I do a "find . -name "glib*" from root I get all sorts of versions of glib laying around and most of them are later than 2.6.   

If I downgrade my glib to 2.6 (which I'm not sure how to do), couldn't that break a bunch of other stuff?

I'd love to get gnucash to work.  Quicken is one of my last reasons to stay dual boot with windows....  goal= no windows ever again!

Thanks so much for any help/suggestions.

---

### Post by Nano Geek on 2008-01-08
I think it's looking for this. > sudo apt-get install libglib1.2-dev

---

### Post by mikeyphi on 2008-01-08
I had a similar problem some time ago - it seems that Gnucash is somewhat behind as fas as Ubuntu is concerned!
I had to add the previous Ubuntu version repos and install the previous version of Gnucash (there were no issues) in order to get all the appropriate packages!!
All I did was open the sources.list in an editor and copy the repo's - replacing the current name with the previous name. After the install - you can remove (or #) the added lines.

---

### Post by danshumaker on 2008-01-09
Thanks for the replies.  I tried the 

sudo apt-get install libglib1.2-dev

the apt-get worked but the gnucash configure afterwords got the same error as before.

Then I tried downloading the glib2.6.0 tarball from the [ftp://ftp.gnome.org/pub/gnome/sources/glib](ftp://ftp.gnome.org/pub/gnome/sources/glib) 
site and installed that.  Even though the configure for glib2.6.0 worked the make failed with these errors:

```

about a thousand of these galias.h errors:
galias.h:3544: error: 'g_vfprintf' aliased to undefined symbol 'IA__g_vfprintf'
galias.h:3548: error: 'g_vprintf' aliased to undefined symbol 'IA__g_vprintf'
galias.h:3552: error: 'g_vsnprintf' aliased to undefined symbol 'IA__g_vsnprintf'
galias.h:3556: error: 'g_vsprintf' aliased to undefined symbol 'IA__g_vsprintf'
make[4]: *** [garray.lo] Error 1
make[4]: Leaving directory `/home/dan/downloads/glib-2.6.0/glib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/dan/downloads/glib-2.6.0/glib'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/dan/downloads/glib-2.6.0/glib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dan/downloads/glib-2.6.0'
make: *** [all] Error 2

```

I feel like such a rookie.

Stay tuned next time, when our fearless rookie attempts to install what mikeyphi calls "previous Ubuntu version repos" and "previous version of gnucasH".

:popcorn:

---

### Post by Nano Geek on 2008-01-09
Sounds exciting. :)

But before you do that, you could try making sure you have all of the dependencies for GNUCash.```
sudo apt-get build-dep gnucash
```If that doesn't work though, you can find all the Ubuntu packages at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Just find the newest one that works for you.

---

### Post by danshumaker on 2008-01-10
And the angel corus sings  "Alllelujah!!!!!!!!!!!"

sudo apt-get is a God sent.

 sudo apt-get build-dep gnucash
 sudo apt-get install gnucash

solved my problems!  Thanks all.   Being a windows dude I thought I had to goto a webpage and click on a link and download a package and untar it and then make config etc...

I should write those gnucash people and tell they should tell us ubuntu users to use apt-get  instead.  Of course before I do that I should read through the whole installation instructions..   

Don't you just hate rookies who don't read instructions.. :opps

Stay tuned next time when our crack-head rookie fills in gnucash's "configuration data" that is apparently in a "non-standard location" (according to some update gconf window).

:biggrin:

---

### Post by andi5 on 2008-01-30
Actually, you do not need to run `apt-get build-dep ${pkg}` to install ${pkg} which is usually done by `apt-get install ${pkg}` when sticking with the ubuntu repositories.

The build-dep command simply installs all _build dependencies_, i.e. development packages you need when you want to compile from source by running ./configure ${flags} && make && [sudo] make install. Only few people need that.

---

### Post by caller9 on 2008-04-20
andi5 is correct. 

But to solve the problem of people wanting to have the latest gnucash (Ubuntu package repository version is 2.2.1 from October 2007). You should do the following. **NOTE: Unless you have an issue with the repository version that is resolved by the latest stable version, you're just wasting your time with the following steps. Most people can just "sudo apt-get install gnucash." ** The majority of fixes are related to importing .QIF(Quicken) and various locale/printing/errors. It was enough of a list to make me want to update manually. Their list can be found here: [http://www.gnucash.org/](http://www.gnucash.org/)


Might not need the first line but I did it first, so I know this works. 
```
sudo apt-get install build-essential
sudo apt-get build-dep gnucash
```

After extracting gnucash 2.2.4 tarball and entering that directory

```
./configure
make
sudo make install
```

---

