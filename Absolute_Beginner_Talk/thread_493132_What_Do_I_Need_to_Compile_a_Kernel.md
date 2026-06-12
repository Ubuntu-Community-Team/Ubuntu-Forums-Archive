---
title: "What Do I Need to Compile a Kernel?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by skipkent on 2007-07-05
I recently installed a version (not sure which) of Ubuntu from a DVD in a book (Unleashed, I think) and then found that my little Belkin usb wireless device was not supported by default.

I tried 'modprob (drivername)' and some other things I found online while at work, but it always said that the given module was not available.

So I thought that maybe I could recompile the kernel and make these modules available somehow during the 'make config' process.  I played a lot with Linux a loooong time ago (Slackware, Suse) and am very much out of practice, but thought that this was the way to go about things.

make config / make xconfig and such didn't get off the ground because the 'make' package was not installed.  Fine.  I startup Synaptic and manage to find and load that from the DVD, after finding and loading the source as well.

Suffice to say, there are a TON of other dependencies I'm lacking, and the book is no help whatsoever.  It talks as though everything should be there out of the box, but it's not.  I'm at a loss as to all the little widgets and libraries and thingies I'm supposed to have to compile a kernel, but there doesn't seem to be a clear way to determine what is needed.  

In the past, these sorts of things were always accounted for and...just worked.

There's got to be some easy way to say 'load up all the stuff I need to recompile a kernel', instead of me having to guess...gcc?  gcc 3.this?  gcc 4.that?  g++?  thesetools?  thosetools?  I'll end up loading up tons of stuff I don't need and still be missing something.

What gives?   How do I get my installation into a state in which compiling a kernel is possible?

Thanks!

-skent

---

### Post by punx45 on 2007-07-05
well, i know that for compiling in general you need the build essential package, which you would get through the synaptic gui, or through the command line by:
```
sudo apt-get install build-essential
```

as for building a kernel, thats sorcery in my opinion, so i cant help ya there :)  but there are plenty of guides available around the nets.   it could be that there is a simpler solution to your problem, so just search the forum for the model of your device.

---

### Post by az on 2007-07-05
> **skipkent said:**
> 
In the past, these sorts of things were always accounted for and...just worked.

There's got to be some easy way to say 'load up all the stuff I need to recompile a kernel', instead of me having to guess...gcc?  gcc 3.this?  gcc 4.that?  g++?  thesetools?  thosetools?  I'll end up loading up tons of stuff I don't need and still be missing something.

What gives?   How do I get my installation into a state in which compiling a kernel is possible?

Thanks!

-skent

You don't need the toolchain on a desktop system.  You can install it easily, as stated, if you need.

To build an extra module for your kernel, you need to install the linux-headers package for your kernel as well as build-essential.  You don't need to rebuild the whole kernel.

sudo apt-get install linux-headers-generic

---

### Post by skipkent on 2007-07-06
Thanks on both replies.  I didn't know about 'build-essential'.  I'm hoping that's on the install cd and will check when I get home.

I also read just recently about only needing the header files to compile a module, so that's great advice as well.

Cheers,

-skent

---

### Post by LaRoza on 2007-07-06
> **skipkent said:**
> Thanks on both replies.  I didn't know about 'build-essential'.  I'm hoping that's on the install cd and will check when I get home.

I also read just recently about only needing the header files to compile a module, so that's great advice as well.

Cheers,

-skent

build-essential is on the cd, it should be in the distro by default.

---

### Post by kwacka on 2007-07-06
before you start compiling (unless you really want the experience) try ndiswrapper. It's a bodge that allows windows drivers to be used under linux. 

If you go to the ndiswrapper home page at:

[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) 

try the wiki and you'll see a list of cards known to work.

Its in the repositories so easy to install.

ndisgtk is a gui for setting up.

If you still need to compile take a look at [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by az on 2007-07-06
> **LaRoza said:**
> build-essential is on the cd, it should be in the distro by default.

On the desktop cd, it's apart from the live session.  So, once you installed and booted into your new system, pop the cd back in and the repository on it will be detected.  You will be offered to start the package manager and then you will be able to install the packages from the cd.

There is a 20-page discussion from about a year ago on the dev mailing list about whether or not build-essential should be installed by default.

---

