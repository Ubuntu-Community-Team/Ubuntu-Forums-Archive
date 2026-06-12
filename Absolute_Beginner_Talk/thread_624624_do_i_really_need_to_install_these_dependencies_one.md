---
title: "do i really need to install these dependencies one by one?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by mikhsoj on 2007-11-27
im trying to install a few simple programs such as kplayer but there are so many dependencies! even dependencies have other depenedencies! ive tried to download them all but there has to be a simpler way, isnt there? cant i just have ubuntu download all know dependencies or download all the ones that are needed for that program? or do i have to find each an every dependency to get the programs to work?

---

### Post by Znort_Ubern00b on 2007-11-27
normally if you install using synaptic it will mark and install any dependencies...are you using synaptic???

---

### Post by erginemr on 2007-11-27
Hello,

No, you don't. The Debian package management system (apt-get, aptitude, synaptic) is perfect at everything, including the dependency handling. So, you will not run into any dependency hell as was before years ago, provided that you install your programs from the Debian software pool (which hosts some 20,000 packages), not from a source package.

The same is true for precompiled Debian (*.deb) packages that you can find on the Internet. When you double-click on it, it will seamlessly install including any dependent packages.

Even betterthan that, if you use "aptitude" with "sudo aptitude install package_name", and if you decide to uninstall it later on with "sudo aptitude remove package_name", all dependencies installed alongwith will also be removed from your system.

---

### Post by Anicka on 2007-11-27
There is no kplayer in the repos. Where are you getting it from?

---

### Post by erginemr on 2007-11-27
The following site:
[http://kplayer.sourceforge.net/#downloads](http://kplayer.sourceforge.net/#downloads)

has a Debian package and apparently it is a front end for mplayer. But it is for KDE and unless you are using K desktop environment, I believe there are better Gnome-only media players out there.

---

### Post by mikhsoj on 2007-11-27
okay so i downloaded the vlc player
i tried to type this in the terminal and it didnt do anything:
sudo aptitude intall vlc-8.0.6c.tar.gz

nothing, how am i supposed to install this?

---

### Post by OldGrey on 2007-11-27
If you use "synaptic" in the system / administration menu it will download and install the package and any necessary dependencies in a couple of clicks.

---

### Post by Anicka on 2007-11-27
There is something in the repos called kmplayer. It's an other KDE-frontend of mplayer. Since it's in the repos you can just type "sudo aptitude install kmplayer" in the terminal and everything should be installed automatically.

---

### Post by misfitpierce on 2007-11-27
> **mikhsoj said:**
> okay so i downloaded the vlc player
i tried to type this in the terminal and it didnt do anything:
sudo aptitude intall vlc-8.0.6c.tar.gz

nothing, how am i supposed to install this?

If you want vlc try sudo apt-get install vlc

---

### Post by drs305 on 2007-11-27
> **mikhsoj said:**
> okay so i downloaded the vlc player
i tried to type this in the terminal and it didnt do anything:
sudo aptitude intall vlc-8.0.6c.tar.gz

nothing, how am i supposed to install this?

A file with a tar.gz extension is a file containing compressed folders/files. These files have to be 'unzipped' and are run differently than a normal installation file. The 'sudo aptitude install' method won't work for these types of files. Sudo aptitude install works with just the name of the program (i.e. no extensions). Example: sudo aptitiude install gimp

The easiest way to install apps is via synaptic (or command line if you have the command ;) ) or via a .deb file (which you just have to click on). Stick with those methods for ease of use.

There are a lot of threads about how to install tar.gz apps. Here is one :
[http://ubuntuforums.org/showthread.php?t=118208](http://ubuntuforums.org/showthread.php?t=118208)

This link is to "How to Install Anything in Ubuntu":
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by mcduck on 2007-11-27
> **mikhsoj said:**
> okay so i downloaded the vlc player
i tried to type this in the terminal and it didnt do anything:
sudo aptitude intall vlc-8.0.6c.tar.gz

nothing, how am i supposed to install this?

Now, your problem is that you are trying to do this like you would do in Windows, browsing through different web pages and downloading stuff from them.

It's actually easier than that. just open Synaptic package manager, or the Add/Remove-thing. Select what you want to install, and these programs will download, install and configure everything for you.

You should also read this: [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by sourcemorph on 2007-11-27
ok how about this.. i have ubuntu 7.10 and i have downloaded and installed all the softwares i need. i have the .deb files stored in /var/cache/apt/archives... now when i reinstall ubuntu i do not want to download all the packages again (i have a rather slow net connection) ... is ther a way that i can install these softwares again without having to manually install all the dependencies.

aptoncd only makes an iso of all the .deb's u have and then at the time of restore it copies the .debs to the archives folder.... anyway way this can be done less painfully??

---

### Post by mcduck on 2007-11-27
> **sourcemorph said:**
> ok how about this.. i have ubuntu 7.10 and i have downloaded and installed all the softwares i need. i have the .deb files stored in /var/cache/apt/archives... now when i reinstall ubuntu i do not want to download all the packages again (i have a rather slow net connection) ... is ther a way that i can install these softwares again without having to manually install all the dependencies.

aptoncd only makes an iso of all the .deb's u have and then at the time of restore it copies the .debs to the archives folder.... anyway way this can be done less painfully??

Just copy all the .deb packages somewhere, and then to install them run 'sudo dpkg -i *.deb' in the directory where you have them. This will install them all.

---

### Post by philinux on 2007-11-27
How about to install a .deb just double click it.

---

