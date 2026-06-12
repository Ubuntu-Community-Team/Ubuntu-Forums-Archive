---
title: "What's a package?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by lichking20 on 2006-08-19
Hello, i'm new to ubuntu. There's all this talk about 'packages' like 'kde-desktop-package', and I was wondering what are packages? Do they work like windows Setup.exe files? are they source or binary files? why do i have to run them in the command line sometimes?

Sorry i have so many question, i'm just a little confused. :confused:

---

### Post by Carbonfish on 2006-08-19
Hi, 

Read this:    [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)  ;) 

KC

---

### Post by sbassett on 2006-08-19
A package is one piece software, usually. The one that you mentioned "kde-desktop-package" or kubuntu-desktop is actually a meta-package which basically points to many different packages. You may think of them as related to the basic setup.exe files from windows. It has now become just as easy (if not easier) to install a package, or deb, as a setup.exe file. Merely clicking on the package will initiate the install package dialogue. As long as the deb in question doesn't require very vague dependencies, the package installer will fetch any needed dependencies from the apt sources automatically. But basically, all that you will see is a simple message stating that the installer needs to retrieve 2 packages (all of these extra packages are downloaded from the sources you already have configured), it will then ask you if this is ok, then off it goes.

---

### Post by secretlondon on 2006-08-19
> **lichking20 said:**
> Hello, i'm new to ubuntu. There's all this talk about 'packages' like 'kde-desktop-package', and I was wondering what are packages? Do they work like windows Setup.exe files? are they source or binary files? why do i have to run them in the command line sometimes?

Sorry i have so many question, i'm just a little confused. :confused:

Packages are like windows installers. They are binary files.

There are different ways of installing them but they amount to the same thing. Some people think it is easier to tell people to copy and paste into the command line rather than how to find using the gui. It's the same thing.

---

### Post by dasunst3r on 2006-08-19
As others have said, packages consist of binary files.  Additionally, they contain scripts used to set up the program.  Packages themselves are not executable (not even through the command line).  They are installed through your package manager (which is Synaptic in Ubuntu's case).

To me, there are several advantages to packages:
1. You can queue as many of them as you want to be installed.
2. No "Next" button to click on, so that means you can commit your changes and take a coffee break (if you're installing lots of packages).
3. The package installation process takes care of everything for you, including menu entries, file associations, etc.

Welcome to Linux!  Hope you enjoy it!

---

