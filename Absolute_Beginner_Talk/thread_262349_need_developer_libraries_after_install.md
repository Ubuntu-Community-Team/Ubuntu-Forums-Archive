---
title: "need developer libraries after install"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by bigmeow on 2006-09-21
I know unix (20+ years), but I don't know ubuntu, debian, or linux package management well.

I have a ubuntu 6.06 newly installed system.  Someone else did the install for me because it is at a remote location.  The problem is that they apparently selected something during the install that prevented "development" version of packages being installed.  For example, all the installed libraries like zlib, gd, png, ssl, etc are installed, but there are no include files.  I can't compile anything against those libraries without the header files.

I'd like to believe that everything I might ever need already exists as a deb.  But that isn't the case.  There are already a handful of packages I need to install that I need to compile against these libraries.  I also frequently twiddle code and install things from source.

So is there a way I can fix this without giving up and re-installing from scratch?  Obviously I want to avoid that because it is non-trivial remotely.  And I've already put the system into production!  I could just cp the header files in, but I'd rather not backdoor dpkg.

For really simple libraries I have installed the -dev package while the not -dev package is installed (e.g., libz1g).  That seems to work.  The not -dev package is listed as "deinstall" but I can't remove it because a gazillion packages depend on it.  But I hesitate at doing this for things like libgd that is so intertwined with everythingn from x11 to python.  Besides, the -dev packages are not listed as available through dselect, so it's more than a bit tedious to click find them on packages.ubuntu.com, download the deb, install, oops dependencies, repeat.

Any help would be greatly appreciated.

Barb

---

### Post by muep on 2006-09-21
There are a lot of packages that end in -dev, which means it has those header files. You need to install those for the packages that you want to compile against. They aren't installed in a default install because they wouldn't fit on the cd and usually a basic user doesn't need them. An advanced user can easily install the ones he needs.

Are you familiar with the package management in Ubuntu?

---

### Post by andypaxo on 2006-09-21
You shouldn't need to 'backdoor' the package management. This is exactly what apt (or synaptic or aptitide) are for.
Use apt-cache to search for packages (as you state, the ones with the headers have -dev on the end)
The -dev packages will not conflict with the runtime packages, you can happily have both installed at once.

Hope this helps, don't hesitate to ask for more information if this didn't answer your question

---

### Post by Brunellus on 2006-09-21
> **bigmeow said:**
> I know unix (20+ years), but I don't know ubuntu, debian, or linux package management well.

I have a ubuntu 6.06 newly installed system.  Someone else did the install for me because it is at a remote location.  The problem is that they apparently selected something during the install that prevented "development" version of packages being installed.  For example, all the installed libraries like zlib, gd, png, ssl, etc are installed, but there are no include files.  I can't compile anything against those libraries without the header files.

I'd like to believe that everything I might ever need already exists as a deb.  But that isn't the case.  There are already a handful of packages I need to install that I need to compile against these libraries.  I also frequently twiddle code and install things from source.

So is there a way I can fix this without giving up and re-installing from scratch?  Obviously I want to avoid that because it is non-trivial remotely.  And I've already put the system into production!  I could just cp the header files in, but I'd rather not backdoor dpkg.

For really simple libraries I have installed the -dev package while the not -dev package is installed (e.g., libz1g).  That seems to work.  The not -dev package is listed as "deinstall" but I can't remove it because a gazillion packages depend on it.  But I hesitate at doing this for things like libgd that is so intertwined with everythingn from x11 to python.  Besides, the -dev packages are not listed as available through dselect, so it's more than a bit tedious to click find them on packages.ubuntu.com, download the deb, install, oops dependencies, repeat.

Any help would be greatly appreciated.

Barb
I'm not all that familiar with development, but your first port of call will probably be to install the build-essential package, which contains many basic development tools and utilities (gcc and make and more)

```
sudo aptitude install build-essential
```

As far as the other development libraries go:  if you need specific headers and so forth, you can check to see what packages exist for those by searching the apt cache

```
sudo apt-cache search $packagename
```

will return everything with $packagename in the package name or description.  I'm not 1337 enough, but I am assured that the apt-cache search also takes regexes, if you're cool like that.

Hope that helps.  

Also, off-topic as an old UNIX admin, why Ubuntu and not, say, OpenBSD?

---

### Post by PabloH on 2006-09-29
I don't know much about Ubuntu, but have used Debian for years. So why are all the -dev packages mismatched with the binaries in this distro? 

Each dev package does not have an installation canidate-- as the binary packages are a version newer than the dev is (take libgtk2.0 for example, and I ran into 3 others I had to force before this... while trying to compile gnucash). I am having to force packages back a version or find dev deb's from pool and elsewhere that match the new binary version because the repository is missing them. What is going on here? Is it always like this? Maybe this is what some of the original poster's problems are-- the dev libraries have missing dependencies because they are out of date. When is this going to be fixed?

---

### Post by bigmeow on 2006-10-06
To answer Brunellus' question.  I chose ubuntu rather than openbsd because this is a production system and I didn't want to have to kept everything up to date on my own.  I like that as long as I keep doing updates, the packages I use will never be more than 6 months old.  I don't have the time to manually update all my essentials all the time.

But being the only ubuntu system I have, I need to diddle things so I need dev packages.

I seem to be able to install the -dev packages without uninstalling the non-dev package.  But dselect now claims the non-dev package is "broken."

---

