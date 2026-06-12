---
title: "Minor Issues with Ubuntu"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Protostar on 2006-02-19
Hello all. I"ve completely switched to Ubuntu (as I've screwed up Windows and don't feel like reinstalling it) and have never been happier with my computing experience.
There are some minor issues I want to resolve though. 


-I managed to get my wireless up and running using ndiswrapper, but when I boot up, it takes forever to get to the desktop. It will usually hang on "Waiting for network interface to come up" for five or more minutes. Is there anything I can do to reduce the boot time. Also, is it possible to configure Ubuntu in such a way that is only enables the wireless interface and does not connect to any network?

-I remember in Suse, there was an option in Yast that allowed you to configure the OS in such a way that it would disable the wireless interface when a cable (ethernet) connection was detected. I have access to a T1 connection in my dorm room, and would like to use my ethernet connection when there. However, I sometimes will go out and want to be able to connect to the campus wireless network as well. Anyone know how to set this up?

-Recently, when I have used the Eye of Gnome image viewer, when I load a large number of images ( a couple hundred) is will simply load one which is usually the last one in the list. Anyone know why this is?

-I'm using Firefox, but am really an Opera fan. I've tried installing Opera, and I got it working but there are a few problems. First, it keeps complaining about the "openmotif" and that it needed it. So I dl'ed it off Opera's website and tried installing.  The outout from the dpkg command was this:

[i]Selecting previously deselected package openmotif.
(Reading database ... 77998 files and directories currently installed.)
Unpacking openmotif (from openmotif_2.1.30-5_i386.deb) ...
dpkg: dependency problems prevent configuration of openmotif:
 openmotif depends on xlib6g (>= 3.3.6-10); however:
  Package xlib6g is not installed.
dpkg: error processing openmotif (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openmotif[/i]

I tried the sudo apt-get install command and got this output:

[i]Reading package lists... Done
Building dependency tree... Done
Package xlib6g is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlib6g has no installation candidate[/i]

Anyone know the solution to this? Another problem in Opera has to do with the color (for lack of a better term). I changed themes so now I have a black theme. Firefox looks like this:

[[img]http://xs69.xs.to/pics/06081/Firefox.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs69&d=06081&f=Firefox.png)


Here is what Opera looks like:

[[img]http://xs69.xs.to/pics/06081/Opera.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs69&d=06081&f=Opera.png)

Notice in the Opera screenshot how all the menus are white and and how the text in Google is highlighted (without the highlight the text is black and invisible). Has anyone had any problems like this?

-I have Microsoft Office 2003. I tried installing it using Crossover Office, and the installation program hung. I then tried it with Wine and the installation program failed as well. Has anyone succuessfully installed Msft Office '03 in linux? If so, how?

---

