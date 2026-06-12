---
title: "[SOLVED] Where do I install stuff"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by mrgordonz on 2007-12-12
Hi Experts,

This is probably going to sound like a really dumb question.

I am used to a Windows environment where if I want to install a piece of software which I find on the Internet, I simply download an installer (eg: setup.exe) and save it in my  downloads folder.  To install I just execute the .exe and hey presto, it installs into the appropriate folder (usually under C:\Program Files\<product name>).

My question is what is the equivalent process in Linux?  For example, I have downloaded a file called install_flash_player_9_linux.tar.gz from the Adobe site, and saved it under a downloads folder I created.  I know I need to execute something like ```
tar -xvvzf install_flash_player_9_linux.tar.gz
```

But where does it get installed?  Does that tar command install or just extract?

Does Linux have an equivalent to C:\Program Files\?

Cheers,

Paul

---

### Post by fenian on 2007-12-12
You should read[ this.]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by LaRoza on 2007-12-12
Programs are installed in /usr/bin and /usr/sbin (usually). The second is for GUI programs.

---

### Post by t0p on 2007-12-12
You should install things via Synaptic/apt-get whenever possible, as this will automatically install packages into the right location.

When you download something like your install_flash_player_9_linux.tar.gz, you should generally download and extract it to your Desktop.  Then you go into the resulting directory and look for a README file.  This will tell you what to do: eg. execute an installer script in that directory
```
./ installer-script.sh
```
and that will generally put everything where it belongs.

If you install .debs, they will automatically end up where they need to go.

---

### Post by LaRoza on 2007-12-12
> **mrgordonz said:**
> 
But where does it get installed?  Does that tar command install or just extract?

Does Linux have an equivalent to C:\Program Files\?


That tar command does several things, to read up on each option: "man tar"

No, Linux doesn't use drive letters, and any directory named "bin" or "sbin" usually has programs in it.

---

### Post by aysiu on 2007-12-12
You don't need a .tar.gz to install Flash.

Follow [this tutorial](http://www.psychocats.net/ubuntu/flash).

---

### Post by Afkpuz on 2007-12-12
First off, you don't need the command line to extract this file.  Right click and select" Open with archive manager."  Then, just click "extract" because this folder doesn't need to go anywhere. If you open up the archive, you see an install file.  Becuase it has an install file, you don't need to put it anywhere specific.  The installer will take care of that.  Simply double click and choose "run in terminal".  That will walk you through the install process.  However....

There is an easier way to install this program.  

System>Administrator>Synaptec package manager

search for "adobe" 
Click the little check box next to "flashplugin-nonfree"
Click apply


That will install for ya automatically.  Then, just reopen firefox and you should have flash.

And for future reference, it's a great idea to create a folder in your home folder called "installs".  anytime a program calls for you to just copy it's entire folder somewhere or compile it, you can put it there for easy access.  But really, you can put it anywhere that you have permission to write to.

---

### Post by PeterJS on 2007-12-12
Here's a pretty compete layout of what goes where:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

---

### Post by Wiebelhaus on 2007-12-12
Great links in here , thanks folks.

---

### Post by mcduck on 2007-12-12
> **LaRoza said:**
> Programs are installed in /usr/bin and /usr/sbin (usually). The second is for GUI programs.

Well, this is basically true but not the whole truth.

Only the executable  file or script that is used to start the program goes to /usr/bin, but no other file belongs there. The rest is spread around the file system, based on the purpose of the files. All documentation files are put into /usr/share/doc, icons and images into /usr/share/pixmaps and /usr/share/icons, libraries end in /usr/lib, manual files in /usr/man and the rest ends in programs own directory inside /usr/share..

This way you'll always have same kind of files in same place, all documents for all your programs are in /usr/share/doc and all executable files in /usr/bin so you don't need to look for them in different directories like you'd have to do in Windows.

The downside is that installing programs by hand takes some work, but that's why we have excellent package manager to handle this for you. You should use it whenever possible. 

Programs that come in archives usually either have their own installers that put files into correct places, or in case of source code they can be installed using checkinstall (which turns the compiled program into a .deb package and installs it through the package management).

---

### Post by t0p on 2007-12-12
> **Afkpuz said:**
> 
There is an easier way to install this program.  

System>Administrator>Synaptec package manager

search for "adobe" 
Click the little check box next to "flashplugin-nonfree"
Click apply
.

Earlier today I installed the flash plugin.  First I went to do it through Synaptic, but the installation failed - the md5sum didn't match up!  So I ended up having to download install_flash_player_9_linux.tar.gz and installing with that.

---

### Post by mrgordonz on 2007-12-12
> **aysiu said:**
> You don't need a .tar.gz to install Flash.

Follow [this tutorial](http://www.psychocats.net/ubuntu/flash).

Worked a treat - thx heaps.

And many thanks to the others who provided a bunch of very useful links and tips.

I gotta say - there is something special about the Linux community.  It is quite humbling to get so much support from complete strangers - especially when that support comes at no cost to the one receiving it.

---

### Post by aysiu on 2007-12-12
For general installation stuff, this link may help:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

