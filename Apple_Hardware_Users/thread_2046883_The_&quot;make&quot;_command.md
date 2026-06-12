---
title: "The &quot;make&quot; command"
date: 2012-08-23
forum: Apple Hardware Users
---

### Post by paulazizeh on 2012-08-23
Hey guys, glad to be on the forums.  I'm very new to the whole linux world and I just started the CEH training through CBT nuggets and I currently have ubuntu installed on my mac running VMware Fusion so I hope I'm in the right category for submitting this forum.  I've been trying to get hands on training on linux and I'm watching my instructor using the ./configure command and I can get that far but when I tried to apply the make, I get an error stating "make: *** No targets specified and no makefile fount.  Stop."  I'm not sure what to do next.  I've tried to find resources online about how to fix this issue and again, I'm new to linux so I need a little bit of assistance.  I throw up some images about the issue I'm having.  I'm currently running the latest version of ubuntu, I just downloaded it yesterday and using it today.

Thanks guys

Paul

Here's my command prompt trying to run the "make" command

[http://i1250.photobucket.com/albums/hh523/paulazizeh/ScreenShot2012-08-23at23655PM.png](http://i1250.photobucket.com/albums/hh523/paulazizeh/ScreenShot2012-08-23at23655PM.png)

And here's the instructor's command prompt running the same "make" command and the beginning of what the command starting to do when I paused the video

[http://i1250.photobucket.com/albums/hh523/paulazizeh/ScreenShot2012-08-23at23614PM.png](http://i1250.photobucket.com/albums/hh523/paulazizeh/ScreenShot2012-08-23at23614PM.png)

Thanks again, I do appreciate it

---

### Post by drmrgd on 2012-08-23
Do you have to use that source of libcap, or can you use others?  There is a libcap2 package in the repositories that looks to be newer, and you won't have to go through the trouble of compiling from source.  Here is the package information on libcap2:

[http://packages.ubuntu.com/source/precise/libcap2](http://packages.ubuntu.com/source/precise/libcap2)

If you can't use the other package, have a look through the uncompress folder for a README or INSTALL or something.  That should tell you how to compile the source code.  I noticed that your prof is using v1.1.1 and you have v1.3.0.  It could be that the compilation is different and there is no makefile now?  With a super quick Google search, I couldn't find either package.

EDIT:  Total misread of the package name!  The package is lib_p_cap2, and that is in the repositories.  It also seems to be the same version that your prof has:

[http://packages.ubuntu.com/source/precise/libpcap](http://packages.ubuntu.com/source/precise/libpcap)

I'd recommend skipping the manual compilation and installing from the repos unless you absolutely have to.  To do that, from the terminal, just run:

```
sudo apt-get install libpcap0.8
```

---

