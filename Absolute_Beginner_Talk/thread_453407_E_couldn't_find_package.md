---
title: "E: couldn't find package"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by raker t on 2007-05-24
I'm attempting to manually insatll Inkscape. I'm in the right directory, typed: sudo apt-get install inkscape, then the error message appears. I've tried it with the whole name (some numbers after inkscape) and the word package, butonly the error message.

I was told on this forum that inkscape might not install on old version 5.04. Could that be the problem? I'm waiting for my (Fiesty?) CDs in the mail. I want to learn how to do these things without internet connection.

Thanks for the help.

---

### Post by Happy_Man on 2007-05-24
Uh.... have you tried checking your repos, to make sure all of them are active? If you want, though, you can download the Ubuntu .deb directly off the internet, from [http://packages.ubuntu.com/hoary/graphics/inkscape](http://packages.ubuntu.com/hoary/graphics/inkscape)

---

### Post by undertherift on 2007-05-24
Ok  wait, lets step back. 
There's a couple things that i noticed in your post.
1. Apt-get install check the repositories, and then installs by downloading the packages.

apt-get install inkscape (assuming thats the right name) will work only if inkscape is in the ubuntu repositories.  Since you're trying to do it from the command line, we'll walk through that way.  (You COULD go to system-> synaptic and search for it there).


2. Since it downloads (and you said you are doing this w/out internet), it will have no repositories to download from. 

3.  We can take a look at your repository listing.  
If you've verified that its in the repositories (basically, someone told you that), then you shouldn't have it timed out.  Open up /etc/apt/sources.list using your favorite text editor, and see which lines are commented.  There's an explanation in the file, i believe, so you should be able to read it just fine.

Semantic point:  Most people wouldn't really call installation from synaptic or aptitude (apt-get) a manual installation, becuase that downloads and installs for you.  Installing from source (downloading a .tar.gz) is a real manual installation.

I guess my point is, whats happening on your system?  Do you have internet connection?  If you've installed without internet connection, the only repository thats included right now is your install cd.  I doubt inkscape is on there (although i don't know for sure). 
According to the inkscape website "Debian Dependencies — everything is available in the unstable apt repositories."  The way you're doing it SHOULD work... just need to enable repos and have your internet connected. 

Cheers,
Vik

---

### Post by raker t on 2007-05-24
That's some great info. I'm really new to Linux, you might have just provided more pieces to the puzzle than you realize.

I've been concentrating on this install, not getting connected to the internet for two reasons, one, that would be a project unto itself, two, I want to put Linux and Inkscape on my laptop, so I'd like to learn how without the connection. I'm typnig now in MSwindows, on a seaprate hard drive.

From your reply, it sounds as though I can only install from a repository, either on the internet, or on the install Cd. Right now, the files are on a flash drive, and a directory on the hard drive. 

[COLOR="RoyalBlue"]Is it possible to put the package (&autopackage) in a directory on the Ubunto hard drive, then install from there?[/COLOR]

I realize I might be combining some impossibilities here, or ommiting vital steps. Thanks for you patience.:D

---

### Post by jfinkels on 2007-05-24
> **raker t said:**
> That's some great info. I'm really new to Linux, you might have just provided more pieces to the puzzle than you realize.

I've been concentrating on this install, not getting connected to the internet for two reasons, one, that would be a project unto itself, two, I want to put Linux and Inkscape on my laptop, so I'd like to learn how without the connection. I'm typnig now in MSwindows, on a seaprate hard drive.

From your reply, it sounds as though I can only install from a repository, either on the internet, or on the install Cd. Right now, the files are on a flash drive, and a directory on the hard drive. 

[COLOR="RoyalBlue"]Is it possible to put the package (&autopackage) in a directory on the Ubunto hard drive, then install from there?[/COLOR]

I realize I might be combining some impossibilities here, or ommiting vital steps. Thanks for you  patience.:D

If you're using the autopackage that Inkscape provides on it's website (the file ends in ".package"), read here for more info on installing an autopackage without an internet connection: [http://autopackage.org/faq.html#2_2](http://autopackage.org/faq.html#2_2)

This is sort of an unusual installation method: most programs for Ubuntu will be .deb files, which are much easier to install! Maybe you can search around for an inkscape .deb file.

ALSO: you may like this site [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by undertherift on 2007-05-24
"I can only install from a repository, either on the internet, or on the install Cd."

Correct.  There are some packages on the CDs (ndiswrapper, make, gcc), but for extended programs like Inkscape, i doubt they are there.
I would suggest getting the autopackage from inkscape and then following this tutorial to install it. 
[http://autopackage.org/docs/howto-install/?PHPSESSID=a50d4b41ac862cc81098faec55f14025](http://autopackage.org/docs/howto-install/?PHPSESSID=a50d4b41ac862cc81098faec55f14025)

Pay attention to the output; it'll tell you which libraries and packages you're missing (basically called dependencies).  Just as a precursor, i would 
```
aptitude install make gcc
```
just because alot of builds will need that. 

So yes, go ahead, download the package, put it on a flash drive or cd and transfer over to your ubuntu system.  then follow the tutorial.

---

### Post by jfinkels on 2007-05-25
> **undertherift said:**
> 
Pay attention to the output; it'll tell you which libraries and packages you're missing (basically called dependencies).  Just as a precursor, i would 
```
aptitude install make gcc
```
just because alot of builds will need that. 
These are mostly necessary for applications being compiled from source code. The aptitude system will take care of dependencies required by applications being installed with "sudo aptitude install *". Anyway, 'make', 'gcc', and other commonly required programs for building from source are contained in the metapackage 'build-essential', so all you have to do to get these programs is ```
sudo aptitude install build-essential
```

---

