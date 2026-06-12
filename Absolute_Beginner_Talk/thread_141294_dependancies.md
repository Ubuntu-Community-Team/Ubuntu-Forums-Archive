---
title: "dependancies?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by morguns on 2006-03-08
i'm making the full-time switch to ubuntu, and several times i've run into dependancy issues. eg. when installing from .deb files. for example, i want to install easytag. at their site it says "... [you] need to install the following libraries...." 

i'm cool with installing the necessary libraries, but how do i know if they're already installed or not? and if they're not installed, how do i know where to get them? how do i know whether i want/need the latest version or a prior version? at the easytag site there are no less than 16 entries for required library id3lib (and those 16 are only for version 3.8.3! there are a bunch of entries for earlier versions), and except for the ".tar.gz" entry (which i assume is the source), it's all .rpm's. don't i need a .deb?

i've used "sudo apt-get install blahblah" and it's worked fine (mostly). but how do i know what to fill in for "blahblah"? am i supposed to guess "id3lib-3.8.3", cause if i could guess stuff like that i'd be guessin me some lottery numbers and then pay a leetgeek to give me personal tutor time :)

i'd really appreciate someone pointing me to documentation that would clarify this stuff!

---

### Post by stuporglue on 2006-03-08
Well, first off, I'd try to let apt do it's job. :-) 
```

stuporglue@ubuntoo:~$ apt-cache search easytag
easytag - viewing, editing and writing ID3 tags

```

I'm using Dapper and have restricted, universe, and multiverse enabled. I'm not positive that it's available in Breezy, but it probably is. 

Now on to your next question, how to figgure out what a libraries name is... as far as I can tell it's largely a guessing game.  It seems that "lib" usually goes in the front of the name. "apt-cache search" is going to be your friend here. 

eg:
```
stuporglue@ubuntoo:~$ apt-cache search id3 lib
doodle - Desktop Search Engine (Client)
doodled - Desktop Search Engine (Daemon)
extract - displays meta-data from files of arbitrary type
gnomad2 - Manage a Creative Labs Nomad Jukebox
libdoodle-dev - Desktop Search Engine (Development)
libdoodle1 - Desktop Search Engine (Library)
libextractor1c2a - extracts meta-data from files of arbitrary type
libmp3info-ruby1.8 - a pure ruby library for access to mp3 files
libtag1-doc - TagLib Audio Meta-Data Library [documentation]
libtagc0 - TagLib Audio Meta-Data Library (C bindings)
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]
python2.3-id3lib - id3lib wrapper for Python - library
libid3-3.8.3-dev - ID3 Tag Library: Development Libraries and Header Files.
libid3-3.8.3c2a - Library for manipulating ID3v1 and ID3v2 tags.
libid3tag0 - ID3 tag reading library from the MAD project
libid3tag0-dev - ID3 tag reading library from the MAD project
libtag1-dev - TagLib Audio Meta-Data Library [development]
libtag1c2a - TagLib Audio Meta-Data Library
python-id3lib - id3lib wrapper for Python - dummy package
python2.4-id3lib - id3lib wrapper for Python - library
```

you can then read the descriptions and better see what it's name will probably be. You can do the same thing in Synaptic (GUI for apt-get) as well.

---

### Post by Madpilot on 2006-03-08
Short answer: apt-get resolves dependencies for you; if you tell it to install something it'll look at what that package needs and install anything it needs that isn't already installed.

---

### Post by morguns on 2006-03-08
boo yah! "apt-cache search " is new and cool to me (and has made it to my cheat sheet). looks like that will come in handy, thx. i ran it like you did (plus a couple of extra variations) and got similar results. i bet with a little knowledge and common sense i'll be able to put this to good use.

how about a way to find out what's already installed? this can probably be done using the synaptics gui, but it (the gui) has so much junk in it i can't find anything useful. is there some sort of command line like "find libname | grep id3"?

[quote=Madpilot]Short answer: apt-get resolves dependencies for you; if you tell it to install something it'll look at what that package needs and install anything it needs that isn't already installed.[/quote]i understand this, and i've used it successfully for some programs. but, correct me if i'm wrong, not everything i may want to install is going to be covered by apt-get. let's take easytag as an example again. when i go to the easytag site there's no reference to using apt-get to install, but there's a .deb file available and some references to dependancies. i guess i'm just looking for some knowledge that will help me to install software without being 100% dependent (no pun intended) on apt-get. i won't worry about compiling from source just yet. hopefully i'll get a grip on the easy stuff before that's necessary.

thx again.

---

### Post by Madpilot on 2006-03-08
Easytag is available through apt-get, it's in the Universe repository.

The Easytag site probably doesn't mention apt-get/Synaptic specifically because there are lots of Linux distros out there, and lots of methods of package installation - who's got time to document every single method?

Being "100% dependent on apt-get" is how Ubuntu is *meant* to work, and it's by far the easiest way to do things.

I almost always keep Synaptic running on it's own desktop, and when I hear about some interesting app, my first stop is the Search button in Synaptic. (apt-cache search is exactly the same thing)

There's something like 16,000+ packages in Ubuntu's repositories, so no matter how obscure the Linux app is, it could well be already there!

---

### Post by Jucato on 2006-03-08
Three ways to install a program: apt, dpkg, and compile.
By far the easiest will be apt. What it basically does is to look into the repository (which is a HUGE collection/database of debs), check what other packages are needed by the package you want to install (checking dependencies), install those that are not yet installed, and set it all up. Any package that can be found in any repository (main, universe, multiverse, or some other thing), can be installed by apt, whether or not their respective websites say so. Being in the Ubuntu repositories means that these packages have been tested and packaged to work in Ubuntu. 

Take note, however, that there will be some apps that will offer repositories to be used with apt. However, as these aren't included in the Ubuntu repositories, there is not guarantee that they will work flawlessly.

Btw, you could also use Synaptic, a wonderful app for apt. It can help you search for stuff you've already installed other stuff available in the repositories, like easytag. :D

EDIT: I forgot to add. For those packages not found in any repository, you would have to find the .deb file for it and install it through dpkg. More often than not, the website where you got it would say what its dependencies are, if there are any. Otherwise, I'm afraid you'd have to do it by trial or error. I'm not really sure if there's an easy way out. This is one of the biggest advantages of apt over dpkg.

---

### Post by morguns on 2006-03-08
holy repositories batman, easytag was indeed available via "sudo apt-get install easytag". thanks for all of the information and feedback, it's been very helpful. looks like ubuntu might not be as much work as i expected. in a way, it's kind of disappointing; i was looking forward to doing more stuff the hard way. guess i'll have to find another distro if i want life to be difficult, but that can wait a while :) thanks again everyone.

---

### Post by Klaidas on 2006-03-08
apt-get is the simpliest way (I guess) to satisfy dependencies :)

---

### Post by Angry penguin on 2006-03-08
I am having a problem when I issue the make command for building a program, here is the output:

[B]makedepend: warning:  access.c (reading /usr/include/bits/socket.h, line 29): cannot find include file "stddef.h"
        not in ./stddef.h
        not in ../include/stddef.h
        not in ../../include/stddef.h
        not in ../../usr.include/stddef.h
        not in /usr/X11R6/include/stddef.h
        not in /usr/include/stddef.h
[/B]

these look like c libraries,

EDIT: I found the library, it is in  /usr/include/linux/stddef.h how do i specify where it should look?
thanks

---

