---
title: "Copy Function and Codecs Help"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Kenjitamura on 2007-03-04
[SIZE="3"]So obviously I'm new to ubuntu, just installed it today.  I'm trying to get everything all set up and I downloaded an AVI file I'd like to play.  I want to install codecs so I am folowing the guide found at this link [http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml]("http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml")
Well I've downloaded the codec pack, used the sudo function to make the directories, but I can't copy the codecs into the file.  I've tried so many variations and I keep getting errors like no such file or directory.  An example of what I'm typing includes "cp all-20061022/* /usr/local/lib/codecs/" but that always brings up the error "cp: cannot stat `all-20061022/*': No such file or directory".  Please correct and help me![/SIZE]

---

### Post by toasterofirony on 2007-03-04
There is an easier way to do this using [Automatix2]("http://www.getautomatix.com/") for which there is a walk-through around here somewhere.

If you want to continue on the path you are on though a) make sure you're in the right folder for the path you are typing. Type "ls" and see if the folder you are looking for is shown. Also, make sure you are using the right case for all the characters in the folder/ file name. Linux cares about them, whereas windows doesn't.

---

### Post by annda on 2007-03-04
why not follow the ubuntu guides to install restricted codecs:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)
and here
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

