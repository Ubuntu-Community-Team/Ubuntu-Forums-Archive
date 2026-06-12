---
title: "bash: make: command not found"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by fordprefect on 2006-04-20
hey all,

I was installing Ndiswrapper from this site : 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

And everything went fine up to the point where it says "Compile and install Go to source-directory and run 'make distclean' and 'make'. As root run 'make install'." I am logged in as root but in my user profile OR root profile it just says "bash: make: command not found"

At the top of the guide it says that I should be running kernel version 2.6.6 or 2.4.26 with source. I am running version 2.6.12. Is 2.6.12 above 2.6.6? How come the "make" command is missing, this has been annoying me since.

Can anyone please help me get my Ndiswrapper installed and my wifi card. I have all of the files needed but I am stuck here at the moment..

Any suggestions would be welcome.

---

### Post by Jagot on 2006-04-20
As you are compiling from source, if you have not done so you will need to install the build-essential package:

sudo apt-get install build-essential

2.6.12 is indeed above 2.6.6.

You do realise that Ndiswrapper is available in the repositories though?

---

### Post by Randomskk on 2006-04-20
from the console:
sudo apt-get install build-essential


edit: Jagot, beat me to it :P

---

### Post by fordprefect on 2006-04-20
Is it called something like ndiswrapper-utils right? Well I wasn't sure and am a complete noob :P in linux so i was just following the guide..

Now there is a different problem it says can't find kernel build files in /lib/modules/2.6.12-9-386/build; give the path to kernel build directory with KBUILD=<path> argument to make


It seems that the build directory is missing so I tried "locate build" but I could not find a directory called build. Does anyone know where I can find or get it?"

I am confused :confused: :confused:

---

### Post by fordprefect on 2006-04-20
is it possible to download the kernel build files? Is there some sort of package in the repositry that can sort this out?

---

### Post by Jagot on 2006-04-20
I'm afraid I haven't come across that before so I'm not sure.  Somebody else should be able to help though.

---

### Post by fordprefect on 2006-04-20
I hope so as well. Well thanks for helping out. I need to go now so hopefully by tomorrow something will have turned up to help me. I really like the concepts and capabilities of Linux, but unfortunately we all have to start at the beginning...

---

