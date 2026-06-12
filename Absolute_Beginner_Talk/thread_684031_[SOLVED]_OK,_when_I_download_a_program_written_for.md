---
title: "[SOLVED] OK, when I download a program written for Linux how do I install it?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-01-31
I downloaded something called "gutenprint" and I extracted it to my desktop but I don't know what to do now? I click on the folder and there isn't anything that obviously says "click me and I will install".

---

### Post by jan quark on 2008-01-31
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

read this :)

---

### Post by edm1 on 2008-01-31
gutenprint is already installed in later versions of ubuntu.

---

### Post by jan quark on 2008-01-31
ok that was too short

first try always to look in the synaptic package manager if your application is there
it is the most painless and the easiest method

secondly try to find a .deb package. this packages you can download and install by a simple double click

then try the add/remove application

the try the terminal code

```
sudo apt-get install bla bla
```

then but first then try to compile the application from the source

using the three step
```

./configure
make 
sudo make isntall
```

ask for more info

---

### Post by boriquajake on 2008-01-31
Wow, thank you all for the help. Without getting into too much detail then it appears to me that the two easiest ways to install programs in Ubuntu is by either the add/remove application or the synaptic manager, correct? If either one of those fail there is no simple and easy way to do it, right? I mean there is no double click on this and you are good thing, right?

That is fine because I really like the package manager.

---

### Post by Disparition on 2008-01-31
It is always easier to install software through the Add/Remove interface. You can search there too.

---

### Post by jan quark on 2008-01-31
the only doubleclick and good is the .deb file

but who needs deb when you have the whole synaptic to your service
and the whole community to help you:)

---

### Post by boriquajake on 2008-01-31
> **jan quark said:**
> the only doubleclick and good is the .deb file

but who needs deb when you have the whole synaptic to your service
and the whole community to help you:)

I agree about synaptic being better but is it really possible that all of the useful programs are there? What about when you find something that isn' t in synaptic?

Oh yeah, how do you find the .deb file? I have clicked all through (even though I know it is in synaptic I am taking the opportunity to learn here:)) the folder and I don' t see anything ending in ".deb".

---

### Post by AndyCooll on 2008-01-31
> **boriquajake said:**
> I agree about synaptic being better but is it really possible that all of the useful programs are there? What about when you find something that isn' t in synaptic?

Oh yeah, how do you find the .deb file? I have clicked all through (even though I know it is in synaptic I am taking the opportunity to learn here:)) the folder and I don' t see anything ending in ".deb".

Well, just about everything you should need will be in Synaptic, if you enable all the repositories you'll have access to around about 20,000 packages. You won't find anything in Synaptic or Add/Remove ending in .deb. Essentially what you are seeing is a listing and when you click on an app it will be downloaded and installed for you.

What they are saying is that if you find an app by yourself on the Internet then usually they will "package" that file as various binaries. You should choose the .deb version. An example of this is VirtualBox (a virtualisation program). In the repos there is a good workable version. However, since this version is the open-source version it lacks a couple of features. If you want the full bells and whistles version you'll have to download it from the web. When you get to the website you'll find they offer the same app but in different formats, you should choose the .deb version.

:cool:

---

### Post by PeterJS on 2008-01-31
For those rare things that you can't find in the repos you might try looking over at [http://www.getdeb.net/](http://www.getdeb.net/), they've got all kinds of good stuff. If all else fails you can always google for program name deb.

---

### Post by erfahren on 2008-01-31
if you need to compile a program becuase you can't get it (or the a current version of it) any other way I've found the most difficult thing is to get the correct buld tools and dependencies the developer calls for.

Often the README file in the source will have generic build instructions, but there will also be aanother file ("INSTALL" maybe) that the developer will list the tools needed to build it with and some common configuring options (all the configure options available for the program can be gotten with ./configure --help}.

The packages needed to compile the program often aren't listed the same way in Synaptic as the developer lists them. In other words - if the instructions say that you need the library and the development packages of *xyz*, they will be listed in Synaptic as *libxyz* and *libxyz-dev*. (You *should* be able to uninstall the dev packages afterwards.)

-- Sometimes it seems like developers make those lists for other developers who know what the packages are. I had one program where it said I'd need "libvorbisfile, libvorbis and family" - I had no idea what was meant by the *"and family"* part. I think dependencies of the two packages listed by name took care of it though.

There is also a tool named "apt-file" which helps with all that. Information on it is given on the [CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) page. There is also the [CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) help page.

I like to use Checkinstall to build a deb package to install. That way the package can be saved and there's no need to compile again if the OS is reinstalled (just use "checkinstall --install=no") - information here: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by powderhound99 on 2008-01-31
a

---

### Post by boriquajake on 2008-02-01
> **AndyCooll said:**
> Well, just about everything you should need will be in Synaptic, if you enable all the repositories you'll have access to around about 20,000 packages. You won't find anything in Synaptic or Add/Remove ending in .deb. Essentially what you are seeing is a listing and when you click on an app it will be downloaded and installed for you.

What they are saying is that if you find an app by yourself on the Internet then usually they will "package" that file as various binaries. You should choose the .deb version. An example of this is VirtualBox (a virtualisation program). In the repos there is a good workable version. However, since this version is the open-source version it lacks a couple of features. If you want the full bells and whistles version you'll have to download it from the web. When you get to the website you'll find they offer the same app but in different formats, you should choose the .deb version.

:cool:

Cool, that is very good information. Essentially just about any program of worth is going to be found using synaptic if I have all of the correct repositories enabled, right?

Just for my own info, though, I do have a question about a program (package?) I downloaded off of the gutenprint website. Once I extracted the files I ended up with a folder full of all kinds of crap. If I were to install this from what I downloaded I would need to find a .deb file and click on it, right? How does one find the .deb file. Incidentally, when I downloaded it I did select the debian version.

---

### Post by jan quark on 2008-02-01
for gutenprint check this
[http://ubuntuforums.org/showthread.php?t=119595](http://ubuntuforums.org/showthread.php?t=119595)

---

### Post by jan quark on 2008-02-01
and to search deb packages try this database
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

