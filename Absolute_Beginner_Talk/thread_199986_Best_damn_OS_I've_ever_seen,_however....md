---
title: "Best damn OS I've ever seen, however..."
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2006-06-19
I can't seem to find a program to turn .mpegs and .avis into DVDs that will play in dvd players.  NeroLinux sucks from what I've heard and can't even encode the files anyway.  Is there anything that can?

---

### Post by %hMa@?b&lt;C on 2006-06-19
crowell@ubuntu:~$ sudo apt-cache search dvd create
dvd-slideshow - tools to create dvd slideshow with menus
dvdrtools - DVD writing program
kmediafactory - template based DVD authoring tool for KDE.
ksubtitleripper - GUI for KDE to rip DVD subtitles
ripmake - an automatic command line ripping makefile generator for transcode
dfsbuild - Build Debian From Scratch CD/DVD images
dvdauthor - create DVD-Video file system
dvdisaster - data loss/scratch/aging protection for CD/DVD media
dvdisaster-doc - data loss/scratch/aging protection for CD/DVD media (documentation)
dvdtape - Create DVD master filesystems on DLT media
graveman - graphical tool to burn dvd and cd, gtk based
kipi-plugins - image manipulation/handling plugins for KIPI aware programs
koverartist - program for the fast creation of covers for CD/DVD cases and boxesdvd+rw-tools - DVD+-RW/R tools
mkisofs - Creates ISO-9660 CD-ROM filesystem images

try one

---

### Post by yarlson on 2006-06-19
The easiest way is to use [avidemux]("http://fixounet.free.fr/avidemux/") and [varsha]("http://varsha.sourceforge.net/")

There is nice [HOW-TO]("http://forum.videohelp.com/viewtopic.php?t=242455")

To install:
sudo apt-get install avidemux dvdauthor mkisofs dvd+rw-tools dvd-slideshow mjpegtools sun-java5-jre

and then download varsha (simple jar) from [sf.net]("http://prdownloads.sourceforge.net/varsha/varsha.jar?download")

---

### Post by rodrigo666 on 2006-06-19
[QUOTE=jeffc313]crowell@ubuntu:~$ sudo apt-cache search dvd create
dvd-slideshow - tools to create dvd slideshow with menus
dvdrtools - DVD writing program
kmediafactory - template based DVD authoring tool for KDE.
ksubtitleripper - GUI for KDE to rip DVD subtitles
ripmake - an automatic command line ripping makefile generator for transcode
dfsbuild - Build Debian From Scratch CD/DVD images
dvdauthor - create DVD-Video file system
dvdisaster - data loss/scratch/aging protection for CD/DVD media
dvdisaster-doc - data loss/scratch/aging protection for CD/DVD media (documentation)
dvdtape - Create DVD master filesystems on DLT media
graveman - graphical tool to burn dvd and cd, gtk based
kipi-plugins - image manipulation/handling plugins for KIPI aware programs
koverartist - program for the fast creation of covers for CD/DVD cases and boxesdvd+rw-tools - DVD+-RW/R tools
mkisofs - Creates ISO-9660 CD-ROM filesystem images

try one[/QUOTE]

I don't think any of those do what he wants (he wants to convert an avi or mpg file to vob).

It seems to me that all of the programs you quoted need a properly converted mpeg file and don't work with other ones, like a divx movie.

---

### Post by az on 2006-06-19
Tovid?

[http://tovid.wikia.com/wiki/About_tovid](http://tovid.wikia.com/wiki/About_tovid)

---

### Post by xboxbman on 2006-06-19
thanx for the help.  I have to say, this is without a doubt the friendliest community i have ever belonged to.   Everyone is so amazingly helpful.  If only the rest of the world could be like this forum and community.


[QUOTE=yarlson]The easiest way is to use [avidemux]("http://fixounet.free.fr/avidemux/") and [varsha]("http://varsha.sourceforge.net/")

There is nice [HOW-TO]("http://forum.videohelp.com/viewtopic.php?t=242455")

To install:
sudo apt-get install avidemux dvdauthor mkisofs dvd+rw-tools dvd-slideshow mjpegtools sun-java5-jre

and then download varsha (simple jar) from [sf.net]("http://prdownloads.sourceforge.net/varsha/varsha.jar?download")[/QUOTE]

---

### Post by xboxbman on 2006-06-19
[QUOTE=xboxbman]thanx for the help.  I have to say, this is without a doubt the friendliest community i have ever belonged to.   Everyone is so amazingly helpful.  If only the rest of the world could be like this forum and community.[/QUOTE]


But... I couldn't get the app you reffered me to.  Avidemux isn't there.  Simple jar for varsha....not so simple for me. Where do the i unjar it to? It starting to look rather compplicated to make dvds.  I think i may just nero in windows through vmware to do it.  Blasphemy I know, but I'm not quite ready to be making dvds this way.

---

### Post by nalmeth on 2006-06-19
avidemux is in the repositories, might need universe / multiverse enabled.

I've glanced at [devede ]("http://www.rastersoft.com/programas/devede.html")and it looks like it can do the job, + it has a GUI!

---

### Post by xboxbman on 2006-06-19
[QUOTE=nalmeth]avidemux is in the repositories, might need universe / multiverse enabled.

I've glanced at [devede ]("http://www.rastersoft.com/programas/devede.html")and it looks like it can do the job, + it has a GUI![/QUOTE]

looks good, but all the info is in non-english.  Is there any support anywhere?

---

### Post by nalmeth on 2006-06-19
I thought devede was in the repos, but I can't find it anywhere on packages.ubuntu.com/

You can download the tarball at the bottom of the page. You'll have to compile this app.

For directions on compiling from source:
[http://monkeyblog.org/ubuntu/installing/#source]("http://monkeyblog.org/ubuntu/installing/#source")

EDIT: Looks like I'm wrong again. This thread says there is an install.sh file. Check here:
[http://ubuntuforums.org/showthread.php?t=163173](http://ubuntuforums.org/showthread.php?t=163173)

---

### Post by nrayever on 2006-06-22
tovid it's easy to use, but with not so many option
devede is as easy as tovid, but it has more advanced options

nice programs!!:D :D

the first test was made with tovid, and you must follow this howto [tovid howto]("http://www.ubuntuforums.org/showthread.php?t=183936") to make it work
hope devede would be easier!

---

### Post by TheMono on 2006-06-22
Automatix will install Avidemux for you...?

---

### Post by nalmeth on 2006-06-22
Thats what you had to do in Breezy, but it's now in the repositories. 

So ignore that

---

### Post by yarlson on 2006-06-27
[QUOTE=xboxbman]But... I couldn't get the app you reffered me to.  Avidemux isn't there.  Simple jar for varsha....not so simple for me. Where do the i unjar it to? It starting to look rather compplicated to make dvds.  I think i may just nero in windows through vmware to do it.  Blasphemy I know, but I'm not quite ready to be making dvds this way.[/QUOTE]

[How to add extra repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

[How to install J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox]("http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

To run varsha
java -jar /path/to/varsha.jar

---

### Post by MaximB on 2006-06-27
tell me plz 
mkisofs - Creates ISO-9660 CD-ROM filesystem images
are thouse ISO-9660 images readable in windows too ?

---

### Post by Brunellus on 2006-06-27
[QUOTE=MAXDDARK]tell me plz 
mkisofs - Creates ISO-9660 CD-ROM filesystem images
are thouse ISO-9660 images readable in windows too ?[/QUOTE]
yes.

---

### Post by MaximB on 2006-06-27
thanks
and what good burner for dvd's is there ? (data and iso) (no command lines in the program , just GUI).

---

### Post by Kilz on 2006-06-27
[QUOTE=MAXDDARK]thanks
and what good burner for dvd's is there ? (data and iso) (no command lines in the program , just GUI).[/QUOTE]
k3b

---

