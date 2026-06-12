---
title: "Install software via its SVN (ffmpeg)?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-22
Hi,

I am trying to convert a streaming video I captured via mimms using ffmpeg (from .wmv to any file type my Mac can view).  I have the file captured, I just have to use ffmpeg.  

However, I wanted to install ffmpeg from its SVN because its website recommends doing so ... and also, because I know they added new .wmv codec functionality recently and am afraid I will get the errors I get on my mac without the latest version.

So my question is, how do I install it?  [On the website]("http://ffmpeg.mplayerhq.hu/download.html") it gives me this code:

```
  svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
```

Any ideas what I do to download it and compile/install it ?  Thanks!

---

### Post by David_T on 2006-10-22
sudo apt-get install subversion

Then that command will work to download the source code.  This will just get you the latest development version, but you would have to read the README or INSTALL file probably in order to determine what to do to compile after that.

---

### Post by thornomad on 2006-10-22
> **David_T said:**
> sudo apt-get install subversion

Okay, let me give that a try and see where I can go from that ... do I just type, after installing subversion, into the termial: svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg

??  Thanks!

---

### Post by christhemonkey on 2006-10-22
Yes.

Then have a look for a file called README or INSTALL.

---

### Post by thornomad on 2006-10-22
Do I need to install anything special before I run (For the first time ever !!  Hold my hand!!) a:

```
./configure
make
make install
```

???

---

### Post by David_T on 2006-10-22
If you do, ./configure will complain to you about it, but that's what ./configure is there for.

---

### Post by thornomad on 2006-10-22
> **David_T said:**
> If you do, ./configure will complain to you about it, but that's what ./configure is there for.

Oh ... it went and complained!  Maybe I need to install the compilers first ?  I haven't done that yet ... this is the error I got:

```
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
Only do this if you know what cross compiling means.
C compiler test failed.
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-devel@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

```

---

### Post by David_T on 2006-10-22
OK, try
sudo apt-get install build-essential
and then run ./configure again.

---

### Post by qamelian on 2006-10-22
Have you installed the build-essential metapackage? This should provide you with the most common tools needed for compiling from source.

```
sudo aptitude install build-essential
```

---

### Post by thornomad on 2006-10-22
Got it! That took me through the ./configure file without a problem ... now am running the make command.  That is throwing hundreds of "Warnings" and such.  A little scary. Hopefully that is okay ... extremely verbose output.

---

### Post by thornomad on 2006-10-22
THanks so much for your help everyone!  One last question though ... supposing in a few months ffmpeg comes out with some updates or something ... I know I can't do an aptitude update ... so, would I just run the same process over again and let it overwrite everything ?  Or do I have to remove something first ?  

How do I upgrade with this ./configure, make, make install mumbo jumbo ?

---

