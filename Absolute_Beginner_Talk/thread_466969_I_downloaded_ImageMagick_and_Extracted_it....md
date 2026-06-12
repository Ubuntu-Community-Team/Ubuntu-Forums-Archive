---
title: "I downloaded ImageMagick and Extracted it..."
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-06-07
But where did it go?

---

### Post by taurus on 2007-06-07
Probably in ~/Desktop.  Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

I assume you know that imagemagick is in the repos, right?  You can install it from synaptic.

---

### Post by bean77 on 2007-06-07
> **taurus said:**
> Probably in ~/Desktop.  Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

I assume you know that imagemagick is in the repos, right?  You can install it from synaptic.

Here is the output:
```
drwxr-xr-x  7 lydia lydia    4096 2007-06-07 09:52 .
drwxr-xr-x 59 lydia lydia    4096 2007-06-07 09:58 ..
drwxr-xr-x  4 lydia lydia    4096 2007-06-05 07:16 etc
-rw-------  1 lydia lydia     430 2007-06-04 16:56 Google-googleearth.desktop
drwxrwxrwx 17 lydia lydia    4096 2007-06-04 23:55 ImageMagick-6.3.4
-rw-rw-r--  1 lydia lydia 5784603 2007-06-07 09:44 ImageMagick-6.3.4.tar.bz2
drwxrwxrwx 14 lydia lydia    4096 2006-09-13 22:16 iscan-2.3.0
drwxrwxr-x 33 lydia lydia    4096 2007-05-25 15:55 MPlayer-1.0rc1
-rw-r--r--  1 lydia lydia   46346 2007-06-01 13:36 Pick a Winner
-rw-rw-rw-  1 lydia lydia   79492 1998-05-28 22:50 PORKH___.TTF
-rw-r--r--  1 lydia lydia   79752 1998-05-28 22:52 PORKYS_.TTF
-rw-r--r--  1 lydia lydia   33148 2007-05-31 10:58 Sallie2.jpg
-rw-r--r--  1 lydia lydia   37605 2007-05-31 11:01 Sallie3.jpg
-rw-r--r--  1 lydia lydia   10361 2007-05-29 21:21 Sallie.jpg
drwxr-xr-x  5 lydia lydia    4096 2007-06-05 07:16 usr

```

Please don't laugh but I have no idea what repos is or synaptic.

(hanging head in shame!)

---

### Post by meng on 2007-06-07
ImageMagick is there in the directory listing.

If you want to install it easily, do this:
sudo apt-get install imagemagick

(that's how you install from repositories - apt-get will automatically download the official Ubuntu-ized version and install it for you).

---

### Post by jfinkels on 2007-06-07
> **bean77 said:**
> Here is the output:
```
drwxr-xr-x  7 lydia lydia    4096 2007-06-07 09:52 .
drwxr-xr-x 59 lydia lydia    4096 2007-06-07 09:58 ..
drwxr-xr-x  4 lydia lydia    4096 2007-06-05 07:16 etc
-rw-------  1 lydia lydia     430 2007-06-04 16:56 Google-googleearth.desktop
drwxrwxrwx 17 lydia lydia    4096 2007-06-04 23:55 ImageMagick-6.3.4
-rw-rw-r--  1 lydia lydia 5784603 2007-06-07 09:44 ImageMagick-6.3.4.tar.bz2
drwxrwxrwx 14 lydia lydia    4096 2006-09-13 22:16 iscan-2.3.0
drwxrwxr-x 33 lydia lydia    4096 2007-05-25 15:55 MPlayer-1.0rc1
-rw-r--r--  1 lydia lydia   46346 2007-06-01 13:36 Pick a Winner
-rw-rw-rw-  1 lydia lydia   79492 1998-05-28 22:50 PORKH___.TTF
-rw-r--r--  1 lydia lydia   79752 1998-05-28 22:52 PORKYS_.TTF
-rw-r--r--  1 lydia lydia   33148 2007-05-31 10:58 Sallie2.jpg
-rw-r--r--  1 lydia lydia   37605 2007-05-31 11:01 Sallie3.jpg
-rw-r--r--  1 lydia lydia   10361 2007-05-29 21:21 Sallie.jpg
drwxr-xr-x  5 lydia lydia    4096 2007-06-05 07:16 usr

```

Please don't laugh but I have no idea what repos is or synaptic.

(hanging head in shame!)

Read this: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

The preferred method of installing software is through the package manager, called 'apt', and the graphical interface to apt, called 'Synaptic'. Look under "System > Administration > Synaptic Package Manager".

---

### Post by taurus on 2007-06-07
```
cd ~/Desktop/ImageMagick-6.3.4
ls -la
```

System -> Administration -> Synaptic Package Manager.  Then, in the Search field, type in imagemagick.  Highlight it and put a check mark in front of it to install it.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by eentonig on 2007-06-07
The added benefits of using apt-get (cli) or Synaptic (GUI), is that the software that you install is prepackaged and compiled for your distribution; So you don't have to worry about compability issues and stuff.

And to top it off. apt-get/Synaptic keep an eye on ALL software installed via them and upgrade them as soon as an update is present. So you wont have to chase/remember/download/reinstall all those packages individually.

AND, when you do a distribution or kernel upgrade, it keeps working. Which most likely wont be the case if you installed manually.

---

### Post by bean77 on 2007-06-07
> **taurus said:**
> ```
cd ~/Desktop/ImageMagick-6.3.4
ls -la
```

System -> Administration -> Synaptic Package Manager.  Then, in the Search field, type in imagemagick.  Highlight it and put a check mark in front of it to install it.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I got this:
```
total 2476
drwxrwxrwx 17 lydia lydia    4096 2007-06-04 23:55 .
drwxr-xr-x  7 lydia lydia    4096 2007-06-07 09:52 ..
-rw-rw-r--  1 lydia lydia   40670 2007-06-04 23:53 aclocal.m4
-rw-rw-r--  1 lydia lydia    4331 2006-02-04 18:24 AUTHORS
-rw-rw-r--  1 lydia lydia   92313 2007-06-04 19:08 ChangeLog
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:55 coders
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:55 config
-rwxrwxr-x  1 lydia lydia 1317513 2007-06-04 23:54 configure
-rwxrwxr-x  1 lydia lydia   96688 2007-05-13 14:33 configure.ac
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:55 filters
-rw-rw-r--  1 lydia lydia    7328 2007-06-04 22:56 ImageMagick.spec.in
drwxrwxrwx  3 lydia lydia    4096 2007-06-04 23:53 images
-rw-rw-r--  1 lydia lydia   12916 2007-06-01 12:44 index.html
-rw-rw-r--  1 lydia lydia    1568 2007-04-02 20:47 Install-mac.txt
-rw-rw-r--  1 lydia lydia   26296 2007-04-05 20:01 Install-unix.txt
-rw-rw-r--  1 lydia lydia    1299 2005-04-05 23:27 Install-vms.txt
-rw-rw-r--  1 lydia lydia   11128 2005-04-05 23:27 Install-windows.txt
-rw-rw-r--  1 lydia lydia   10841 2006-11-27 17:49 LICENSE
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:55 ltdl
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:55 m4
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:55 magick
drwxrwxrwx  6 lydia lydia    4096 2007-06-04 23:55 Magick++
-rw-rw-r--  1 lydia lydia    1407 2005-12-07 17:03 magick.sh.in
-rw-rw-r--  1 lydia lydia   10001 2006-11-04 19:41 Magickshr.opt
-rw-rw-r--  1 lydia lydia    7704 2006-03-30 16:07 Make.com
-rw-rw-r--  1 lydia lydia   11823 2007-04-02 21:59 Makefile.am
-rw-rw-r--  1 lydia lydia  687890 2007-06-04 23:54 Makefile.in
-rw-rw-r--  1 lydia lydia    3421 2005-04-05 23:27 mkinstalldirs
-rw-rw-r--  1 lydia lydia    2842 2007-05-19 11:01 NEWS
-rw-rw-r--  1 lydia lydia    6164 2007-05-19 20:48 NOTICE
drwxrwxrwx  4 lydia lydia    4096 2007-06-04 23:55 PerlMagick
-rw-rw-r--  1 lydia lydia    6521 2005-04-05 23:27 Platforms.txt
-rw-rw-r--  1 lydia lydia    4413 2007-04-01 21:09 QuickStart.txt
-rw-rw-r--  1 lydia lydia    2462 2007-05-19 20:44 README.txt
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:53 scenes
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:53 scripts
drwxrwxrwx  2 lydia lydia   36864 2007-06-04 23:55 tests
drwxrwxrwx  3 lydia lydia    4096 2007-06-04 23:55 utilities
-rw-rw-r--  1 lydia lydia    1833 2007-06-04 22:56 version.sh
drwxrwxrwx  2 lydia lydia    4096 2007-06-04 23:55 wand
-rwxrwxr-x  1 lydia lydia    1484 2005-04-05 23:27 winpath.sh
drwxrwxrwx  5 lydia lydia    4096 2007-06-04 23:53 www

```

---

### Post by meng on 2007-06-07
bean77:
Why are you insisting on doing it the hard way when everyone has told you how to do it the easy way?

---

### Post by bean77 on 2007-06-07
> **meng said:**
> bean77:
Why are you insisting on doing it the hard way when everyone has told you how to do it the easy way?

I'm sorry-I'm still learning.  Please be patient.

---

### Post by Warren Watts on 2007-06-10
I too downloaded ImageMagick and attempted to build it from source, which generated a multitude of errors beyond my Ubuntu Newbie level of understanding.  **BUT**, I had the foresight to look here in the Ubuntu forums, and whaddya know?  I find this thread right off that informs me that ImageMagick is in the repositories!
I used synaptic to Install it, and BOOM, it's up and running.

Thank you Taurus for your post, it saved me a lot of time and frustration!

Warren

---

### Post by sveinsen on 2007-06-18
Hello, I used apt-get install imagemagick, and it installed very nice and easily, but still I can't find it.
Where is it on the file system?

I'm running the feisty server-edition.

---

### Post by HotShotDJ on 2007-06-18
> **sveinsen said:**
> Hello, I used apt-get install imagemagick, and it installed very nice and easily, but still I can't find it.[ImageMagick]("http://www.imagemagick.org/script/index.php") is a suite of command line tools.  There are many GUI programs that use these tools, but you won't find "ImageMagick" in your menu.

---

### Post by sveinsen on 2007-06-19
How could I tell my web-photo program where to find it?

I am using coppermine, and during setup of this system it asks for the localisation of ImageMagick.

:confused:

---

### Post by hyper_ch on 2007-06-19
(1) Open a terminal
(2) Run
```

sudo updatedb

```
(3) Run
```

locate imagemagick > output.txt

```
(4) Run
```

nano output.txt

```
And look where the exec file is for imagemagick...
But then, you could also use GD2 - there you won't have to set a path...

---

