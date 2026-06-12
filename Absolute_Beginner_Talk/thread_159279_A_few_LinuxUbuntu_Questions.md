---
title: "A few Linux/Ubuntu Questions"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by malcolmb on 2006-04-12
I've been using Linux for a few months, and just swtiched to ubuntu, but I have a few general and a few Ubuntu specific questions:

1. In the linux file structure, where should I/does it really matter where I install programs? Should they go in my home folder, or /usr/bin...  What's the best practice?  Also, do I want to make those ".folder" hidden folders in my home directory, or should only programs make those.

2.  For Ubuntu Repositories, how do they work?  Because I know you cant the newest versions of some programs like Firefox from them.   Do people update them every few months?

3.  Im using Gnome right now, is there any effect of using KDE Programs on a gnome desktop?

4.  When I'm tryign to compile programs in terminal, I enter "make"  then I get "bash: make: command not found"  any ideas?

Thanks a lot

---

### Post by darckhart on 2006-04-12
hi

1. i've got the same question
2. unlock all the repositories (via synaptic, settings, repositories, settings, show disabled software sources) to see if the package you want is there.
3. no, but it installs the dependent libraries
4. you need to install the package build-essentials

---

### Post by mscman on 2006-04-12
Hey malcolmb
1. I usually just install stuff to the default directory that the installer sticks it in, not sure if this is the best or not.  As far as the hidden folders, if you want to create the .folders or .files, it won't hurt your computer.  It can be nice if you want to store stuff in folders for programs to refer to, but you don't want them cluttering up your everyday space.

2. If you want the most recent (and sometimes unstable) programs, make sure to enable your backports repositories.  This can be done via synaptic, or you can edit your /etc/apt/sources.list file as root and uncomment the respective lines.

3. I haven't noticed many problems, but some users complain of the stability or speed of KDE programs running on Gnome.

4. Install the build-essentials package as suggested above

---

### Post by davebgimp on 2006-04-12
[LIST=1]
[*]The best advice is to put them where you'll be able to find them a couple years down the road once you've forgotten everything. Sure, making a bin in your home folder is cool. Some people use the /opt/ folder as well.
[*]See [here]("http://ubuntuforums.org/showthread.php?t=92672") for a list of recommended repos. For FF 1.5, check [here]("https://wiki.ubuntu.com/FirefoxNewVersion").
[*]You might have some issues with certain KDE programs, but for the most part you should be okay. Synaptic should handle any needed dependencies.
[/LIST]

---

### Post by malcolmb on 2006-04-12
Wow, such fast replies, wicked.

So the "build-essential" package fixed that problem and make works fine now

thanks davebgimp for that link, im going through updating my repositories right now.

Another question i remembered i wanted to ask:

What should i do if i want to install a program say for example Bluefish 1.0.5 from 1.0.1 and I want to wipe my system of all the old files before installing the new version.  Do I need to just delete the old Bluefish folder or would I use the package manager for that, is it still in the package manager if i built the program from the source?

thanks

---

### Post by az on 2006-04-12
[QUOTE=malcolmb]
What should i do if i want to install a program say for example Bluefish 1.0.5 from 1.0.1 and I want to wipe my system of all the old files before installing the new version.  Do I need to just delete the old Bluefish folder or would I use the package manager for that, is it still in the package manager if i built the program from the source?

thanks[/QUOTE]

Let the package manager take care of that.  In fact, everything outside your home directory should be handled by the package manager (with a few exceptions)

If you want to build something from source, either backport it (build it using Dapper source packages) and then install those packages, or use checkinstall.

The way repositories work is that each package is maintained by a developer.  The developer takes the code from the original author(s) - upstream - and packages it.  The source packages along with the changes from the original tarball are uploaded to the repositories and the autobuilders turn them into binary packages.

When a version of Ubuntu gets released, the packages in the repositories do not change.  There are updates and security-updates repositories which get fixed (updated) packages throughout the life of the release, but new version go into the next release.

Given that there is a six month release cycle, no, it's not that big of a hardship.  The code is better audited for security and bugs and everything works well together.  You are free to compile anything you want from source, at any time.  You just have to know what you are doing to not do anything that conflicts with the package manager.

---

