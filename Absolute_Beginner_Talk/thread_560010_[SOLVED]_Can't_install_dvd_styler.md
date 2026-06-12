---
title: "[SOLVED] Can't install dvd styler"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-09-25
I need help with installing dvdstyler. I have downloaded both the deb. files and the tar.gz files but can't seem to get either to work. I have extracted the tar.gz files but can't seem to use the correct commands. The deb file for dvdstyler tells me: Error. Dependency is not satisfiable.
Can someone please help with easy instructions, everything I read and think I have followed correctly, doesn't work.

---

### Post by Maestro23 on 2007-09-25
It tells you what you need before it can install. Is it  DvdAuthor?

To install it:

> sudo apt-get install dvdauthor

Once it is installed, try the deb package again.  If anymore dependency issues pop up, you will have to install them as well. 

Good luck.

---

### Post by bumanie on 2007-09-25
[QUOTE=Maestro23;3427172]It tells you what you need before it can install. Is it  DvdAuthor?

The program I wanted is definitely an open source program called dvdstyler - I liked the look of its GUI on the screenshots.
Most things I have not had trouble with, but there are some things I can never get to work.

---

### Post by Maestro23 on 2007-09-25
> **bumanie said:**
> [QUOTE=Maestro23;3427172]It tells you what you need before it can install. Is it  DvdAuthor?

The program I wanted is definitely an open source program called dvdstyler - I liked the look of its GUI on the screenshots.
Most things I have not had trouble with, but there are some things I can never get to work.

Sorry, didn't make myself clear.  What is the dependency its telling you it needs?  I know someone tried to install this program awhile back and it said it needed Dvdauthor installed first.

---

### Post by bumanie on 2007-09-25
> **Maestro23 said:**
> [QUOTE=bumanie;3427223]

I think you  missed my point.  What is the dependency its telling you it needs?  I know someone tried to install this program awhile back and it said it needed Dvdauthor installed first.
It doesn't say what depencies are "not satisfiable". It just states "Error. Dependencies not satisfiable." May be I will try Dvdauthor and see what happens. Thanks for the tip.

---

### Post by Maestro23 on 2007-09-25
> **bumanie said:**
> [QUOTE=Maestro23;3427245]
It doesn't say what depencies are "not satisfiable". It just states "Error. Dependencies not satisfiable." May be I will try Dvdauthor and see what happens. Thanks for the tip.

Do you have a link to the download?

---

### Post by bumanie on 2007-09-25
> **Maestro23 said:**
> [QUOTE=bumanie;3427285]

Do you have a link to the download?

the download link is:          [http://www.dvdstyler.de/downloads.html](http://www.dvdstyler.de/downloads.html)

---

### Post by bumanie on 2007-09-27
I solved the problem by going to getdeb and downloading the 1.4.1 version of dvdstyler. It works!!
Must have been something wrong with the files from dvdstyler 1.5.1 version which I was trying to install originally.

---

### Post by th0mas on 2007-10-01
indeed...
there loads of dependencies to resolve to have v1.5.1 working actually :

```
$ sudo dpkg --install dvdstyler_1.5.1_i386.deb 
Selecting previously deselected package dvdstyler.
(Reading database ... 194175 files and directories currently installed.)
Unpacking dvdstyler (from dvdstyler_1.5.1_i386.deb) ...
dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on dvdauthor (>= 0.6.14-1+b1); however:
  Version of dvdauthor on system is 0.6.11-5.
 dvdstyler depends on mjpegtools (>= 1:1.8.0-0.4); however:
  Version of mjpegtools on system is 1:1.8.0-0.2ubuntu3.
 dvdstyler depends on netpbm (>= 2:10.0-11); however:
  Package netpbm is not installed.
 dvdstyler depends on mpgtx (>= 1.3.1-3); however:
  Package mpgtx is not installed.
 dvdstyler depends on mkisofs (>= 9:1.1.6-1); however:
  Version of mkisofs on system is 9:1.1.2-1.
 dvdstyler depends on dvd+rw-tools (>= 7.0-7); however:
  Version of dvd+rw-tools on system is 7.0-6.
 dvdstyler depends on wxsvg (>= 1.0); however:
  Package wxsvg is not installed.
dpkg: error processing dvdstyler (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dvdstyler

```

do you know if it's planned that gutsy maintain a dvdstyler package ?
would help a lot since it's a good piece of software

---

### Post by robertmf on 2007-12-13
[COLOR="DarkRed"]dvdstyler "gutsy" gdebi install has dependency issue with mjpegtools.  I have mjpegtools installed and working 

Any solutions out there ?-:(

Thanks in advance!
[/COLOR]

---

### Post by McNee on 2007-12-16
[http://www.dvdstyler.de/downloads.html](http://www.dvdstyler.de/downloads.html)

The DVDStyler page has DEB files, install the second DEB file (wxsvg-1.0b7-i386.deb) first, then DVDStyler itself.

---

### Post by carib909 on 2008-06-09
> **bumanie said:**
> I solved the problem by going to getdeb and downloading the 1.4.1 version of dvdstyler. It works!!
Must have been something wrong with the files from dvdstyler 1.5.1 version which I was trying to install originally.



What do you mean you went to "getdeb"? What command(s) should one run in a terminal window?
When I run the sudo command verbatim as posted I get an error indicating that there is no such file or location.
[http://ubuntuforums.org/images/icons/icon9.gif](http://ubuntuforums.org/images/icons/icon9.gif)

---

