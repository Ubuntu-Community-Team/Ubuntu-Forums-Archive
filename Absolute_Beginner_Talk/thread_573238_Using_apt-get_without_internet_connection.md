---
title: "Using apt-get without internet connection?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by whein on 2007-10-11
I have a computer that for various reasons cannot have an internet connection.  However, I am able to download files elsewhere and copy them over using a USB flash drive.  I'm already familiar with making local repositories and manually installing .deb files, but the part that I have yet to discover is how to update the package list that Synaptic/apt-get uses when it decides what is available.  I know it has something to do with the Packages.gz file that gets downloaded from each repository, but is there a way to download those myself and then get Synaptic to recognize the local versions as if they had really come from the internet sites?  This would allow me to still use the trick of asking Synaptic to install them, dumping the error log into a file when it can't establish the connections to the repositories (no internet connection) and then turning that error log into a download list for the other computer to grab the files from the correct sites, including all dependencies.  Take these fresh files, stick them in the /var/cache/apt/archive directory, and then Synaptic thinks that it has already downloaded them and just goes ahead and installs them anyway.

So does anyone know how to fake an update to the package list that Synaptic/apt-get uses?
-Will


My evil plan:
1) Download the Packages.gz files from a bunch of internet repositories
2) * Merge the info from the Packages.gz files into apt-get/Synaptic
3) Ask Synaptic to download the .deb packages that I want to install
4) Capture the error log to determine the exact URLs that apt-get was trying to connect to for each package
5) Manually download the packages each URL points to and transfer to the unconnected computer
6) Place the packages in the /var/cache/apt/archives/ directory
7) Ask Synaptic to install the packages, which it now can do because they already exist locally
8) ????
9) Profit!!

I have already done everything except 2, 8, and 9 so I know it works.

---

### Post by phidia on 2007-10-11
[http://ubuntuforums.org/showthread.php?t=271225](http://ubuntuforums.org/showthread.php?t=271225)

[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

Hope that helps.

---

### Post by whein on 2007-10-11
Thanks for the links.  They're not exactly what I'm looking for though.  I don't want to create a local mirror of the internet repositories since that would take up WAY too much space.  Instead I want to take the information from the package list files (Packages.gz) and fake whatever happens behind the scenes when I press the reload button in Synaptic or run "apt-get update".  I still want Synaptic to think that it will download from the internet sites when I hit the apply button.  To further complicate things, the computer that will actually have the internet connection (which CANNOT be shared with the Ubuntu machine) will be Windows XP based...  So most scripts and Linux based programs will be non-starters.  I can manually download files and do some parsing/fineseing by hand.  Anything that Firefox and a nice text editor can handle.  Not much beyond that.
Any takers?
-Will

---

