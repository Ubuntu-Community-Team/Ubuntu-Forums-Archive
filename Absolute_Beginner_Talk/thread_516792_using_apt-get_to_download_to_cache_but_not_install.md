---
title: "using apt-get to download to cache but not install?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by prettypebble on 2007-08-03
I would like to download many files at once to cache without installing them, but it doesn't work for already installed files when I try:

apt-get -d install package-name

or

apt-get install -d package-name

It says the application is already installed as a newest version but I don't want to install it, my intention is to download the file to cache! I could go to packages.ubuntu.com and manually download each file but I have hundreds I am wanting to download to cache, many being packages already installed.

The article at [http://www.linux.com/feature/115226](http://www.linux.com/feature/115226) says:

"If a package you're interested in backing up to CD is already installed on your system, you can use apt-get's -d option to download the package file and add it to your cache without installing it:

apt-get -d install package-name"

But it doesn't work when I try it for applications already installed, it won't just download to cache it tells me it's already installed.

Like, for example, if one of the files is xmms-crossfade, when I try to download it to cache when it's already installed with the above command, it says:

xmms-crossfade is already the newest version

why is it saying that when all I want to do is download it to cache? When I check /var/cache/apt/archives the file is not listed nor is any progress indicator, but it tells me it's the newest version. Why doesn't it download to cache? Is this a bug in apt?

Does someone have a clue why it's doing this and how I can download to cache a program that's already installed?

---

### Post by annda on 2007-08-03
if a package is installed, it's in your apt-cache already. or have you cleaned it?

---

### Post by prettypebble on 2007-08-03
> **annda said:**
> if a package is installed, it's in your apt-cache already. or have you cleaned it?

my updater program is set to remove the files from the cache once they've been downloaded/installed. Now that I need to go back and download packages, many of them which have already been installed, it won't let me download them to cache, it gives the message that they're the latest version, but I don't want to install them again, only use the -d option to cache them as the article I linked to instructed I could do:

"If a package you're interested in backing up to CD is already installed on your system, you can use apt-get's -d option to download the package file and add it to your cache without installing it:

apt-get -d install package-name"

Except that it's not working out as the article described, I cannot download packages to cache of programs already installed, it doesn't attempt to download them it says the package is already newest version and returns to prompt. Why isn't it working as I've been told it should, by just downloading the packages to cache even if they are already installed, isn't that what the -d option is for? I am using the sudo command with the above, but it doesn't work! Try it yourself, try to download one package already installed on your system but you want downloaded to cache only, not to install, try it with the above command, using sudo with it, and see for yourself, it doesn't want to download to cache packages which are already installed! Why not?

---

### Post by annda on 2007-08-03
apt is a great tool but from my experience it's difficult to control from CLI. just an idea: use synaptic to choose packages for reinstall and then mark the download only option. i hope it works for you.

---

### Post by prettypebble on 2007-08-03
> **annda said:**
> apt is a great tool but from my experience it's difficult to control from CLI. just an idea: use synaptic to choose packages for reinstall and then mark the download only option. i hope it works for you.

Thank you for this advice, I'll give it a try. Do you see what I mean with apt not wanting to download+cache a file already installed with the -d option when it should? Got me wondering if this was a bug with apt?

---

