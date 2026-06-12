---
title: "Checking Package Dependencies and Finding Out Updates Outside of Ubuntu"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by justinmiller87 on 2007-10-14
As I've said many times before, I currently have to use Sneakernet to update or install anything into Ubuntu thanks to my location. If I download a file or something from [GetDeb](http://www.getdeb.net) on the Windows XP Internet Café  computer and transfer it back to my laptop, I find there's x dependencies that I have to install for it. Then I have to come back, and find those packages in the [repository,](http://packages.ubuntu.com/feisty/allpackages) manually download them, and once again return to my laptop to install. My question is, is there either a Windows-based program or a place on the web that I can find out what, if any, dependencies exist for a package before I have to go back and forth multiple times to get things to work?

Also in a related note, is there any list in the Ubuntu world that says something along the lines of "since (date), the following files were updated."? In other words, is there way for me to manually download and install security and package updates for my distribution, short of waiting to download the Gutsy ISO and do a reinstall from scratch?

Thanks for your assistance.

---

### Post by wormser on 2007-10-14
You can find packages [here]("http://packages.ubuntu.com/") and it usually lists any dependencies.

---

### Post by justinmiller87 on 2007-10-14
> **wormser said:**
> You can find packages [here]("http://packages.ubuntu.com/") and it usually lists any dependencies.
I had already mentioned I was using the package repository in my link, thanks for trying though.

---

### Post by haldean on 2007-10-14
What exactly is the problem then? You can find the dependencies for every package in the repo at [http://packages.ubuntu.com](http://packages.ubuntu.com) or [http://packages.debian.org](http://packages.debian.org)

---

### Post by justinmiller87 on 2007-10-15
> **haldean said:**
> What exactly is the problem then? You can find the dependencies for every package in the repo at [http://packages.ubuntu.com](http://packages.ubuntu.com) or [http://packages.debian.org](http://packages.debian.org)
The issue never was with the repos. I know they list dependencies, the question was with downloading from a third party site such as GetDeb, who doesn't list the dependencies outright. I wondered if there was a way to find that out before I had to come back and download the required dependencies from the repos.

---

### Post by haldean on 2007-10-16
Oh right sorry ;)

On Linux you can use dpkg --info the_package_file.deb to see all of the dependencies. I've never heard of an equivalent for Windows, but you might be able to use dpkg in [Cygwin]("http://cygwin.com/").

---

### Post by justinmiller87 on 2007-10-20
Thanks for the help. I'll be home in a couple of weeks so there's no point in installing anything here. I appreciate it, but it might come in handy sometime down the road.

---

### Post by Dr Small on 2007-10-20
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

