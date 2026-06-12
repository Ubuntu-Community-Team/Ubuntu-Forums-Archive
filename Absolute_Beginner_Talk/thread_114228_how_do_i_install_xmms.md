---
title: "how do i install xmms?"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by janey on 2006-01-08
i have an mp3 disc i want to play, i tried playing it in rhythmbox but it said 'this file is not an audio stream' and wouldn't import it into the media library. i copied the mp3 files to the desktop but that didn't make a difference. and when i tried to play it in totem movie player it said 'There were no decoders found to handle the stream, you might need to install the corresponding plugins'. i don't know what plugins or where to get them from, so i figured i'd just download another program and it would come with the plugins.

*reading all these threads makes me realise i am WAY less nerd-knowledgeable than anyone else here, so i probably don't know enough to use linux, but i'm going to stick at it as long as i can anyway. please forgive if my posts are numerous and stupid sounding. 

i downloaded the latest version from xmms.org, but there is no 'installer program' as i'm used to in windows. there is a text document with lots of stuff i don't understand, and in there i found these instructions:

[I]The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.[/I]

my boyf opened up the terminal and we tried typing in the commands, but we don't really know what we're doing, and nothing has worked so far. it's been years since i've used anything like terminal or dos, so i'm pretty rusty. 

any help is much appreciated. i'm going to try and get gaim working and find someone online to help me via chat, it would be a lot quicker. 

i'll love you long time if you do.

---

### Post by Mustard on 2006-01-08
xmms is installable via synaptic package manager or by using the apt-get command in terminal.  To install via terminal you would do this command...

```
sudo apt-get install xmms
```

To install via synaptic package manager you would need to open up the search tool and type in 'xmms' and search by name.  Here is a HOW TO on using Synaptic Package Manager..
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

I believe xmms works out of the box with mp3s but for other applications it would be necessary to go through some extra steps to get mp3 support working.

I would visit this wiki page for information on getting a lot of the codecs and other stuff that is necessary to get your system playing different media formats.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Here is another HOW TO on settings up movies and music:
[http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies)

Now if you want to still compile the version you downloaded you will need to install this package

```
sudo apt-get install build-essential
```

That will install the essential packages for compiling.

From there you would follow the steps given in the instrucions you have posted above.  The only difference in the way I would do it is that instead of doing the 'make install' step, I would do a 'checkinstall', as this creates an entry in Synaptic Package Manager that will allow for you to easily uninstall the compiled application.

To use checkinstall you would need to download it using this command

```
sudo apt-get install checkinstall
```

Checkinstall is in the universe repository, though, which is not enabled by default in ubuntu.  It is necessary to enable the Universe and also the Multiverse repositories to gain access to extra packages.  A HOW TO on doing that is at this link....
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)


This may all look like a bit of a daunting process, but its just part of the initial configuration of a linux system, due to licence restrictions on proprietary media formats.  After doing the initial setup, things will be much easier, and you will have learnt a bit about the way the system works, which will be helpful in the future.  Ask any questions you like no matter how silly you think they might be.  We were all new to linux and one stage and understand the learning the 'lingo' can be a difficult thing when moving from one operating system to another.

---

### Post by janey on 2006-01-08
awesome, thankyou mustard :)

---

