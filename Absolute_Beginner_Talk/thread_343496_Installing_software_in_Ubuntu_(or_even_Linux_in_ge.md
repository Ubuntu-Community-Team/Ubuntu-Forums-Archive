---
title: "Installing software in Ubuntu (or even Linux in general)"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-01-21
Hello,

I have been using Ubuntu (Dapper) for several months now, but there is still an issue I don't quite understand:

What is the difference between installing something from the repository and downloading it from its own website and installing it manually?

Also, what is the difference between installing something using Automatix2 and doing it manually by downloading a file from its own website?

Let me see if I got this right:

If I install something through the repository or through Automatix2 then it will be integrated into the system i.e. I will find under Applications menu, is this correct? Any other benefits to using the repository or automatix?

Thanks in advance.

---

### Post by zerhacke on 2007-01-21
Your package manager of choice will auto-resolve any dependencies you may have when installing software.  A .deb package or a source tarball will not resolve dependencies for you.  With deb and tarballs you must install all required software manually.

Automatix is simply one of the many frontends to apt-get out there. Automatix(2) is simply handing off apt-get commands to your system.

And yes, most software you install with apt-get (or any frontend to it) and/or Automatix(2) will be installed to the Applications menu.  There are some things that will not be, but the majority does.

---

### Post by Shatrat on 2007-01-21
They're a lot easier than the alternative.  If you download a program from some project's website it will often come as source code in a .tar.gz archive with some scripts for the 'make' program that help you compile it.  There will be a README as well telling you what steps to take to compile it and you'll need the packages contained in the build-essential package.

Before repositories and after tarballs of source code there was .RPM files, which are still common because Fedora and SuSE use them.  Gentoo uses portage which is similar to the apt system but is mostly source code and everything gets compiled locally.

The people who maintain the repositories generally do the compiling for you, and then there are repositories for source code as well.  Ubuntu doesn't always put things in the same places as other so the repositories are a nice way to make sure that it finds the fonts and icons and so forth and settle any dependencies.

---

### Post by r4ik on 2007-01-21
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

good luck !

---

### Post by PartisanEntity on 2007-01-21
Thanks very much for the replies, I think I get it now.

---

### Post by dak-AD on 2007-01-21
to add a quick related question: am i right in thinking that stuff installed thru add/remove, synaptic, and apt-get (if it comes from the ubuntu repositories) will be kept up-to-date (ie, the updater will automatically look for upgrades to the packages and offer them to you via a popup), whereas .deb's, .rpm's, and stuff apt-gotten from a location outside of the main ubuntu repositories will not be auto-updated?

---

### Post by Shatrat on 2007-01-21
> stuff apt-gotten from a location outside of the main ubuntu repositories will not be auto-updated
Anything in a repository you have added to your /etc/apt/sources.list or add through Synaptic will be automatically updated when a new version becomes available in that repository.  The command apt-get update checks available packages and their versions, and apt-get upgrade installs anything that is of a higher version.  Things you install by downloading a single .deb or .rpm wont be, or source code you compile yourself obviously.

---

### Post by dak-AD on 2007-01-22
cheers :)

---

