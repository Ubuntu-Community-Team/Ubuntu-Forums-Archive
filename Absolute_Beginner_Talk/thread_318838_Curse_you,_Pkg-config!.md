---
title: "Curse you, Pkg-config!"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by CelticWhisper on 2006-12-14
I'm trying to install metacity in the most recent release of xubuntu, and am having a few difficulties.  

It's important to note that this system has NO internet connectivity, so Synaptic, apt-get, et al are not viable solutions.  I AM, however, able to obtain files from the internet manually and transfer them via CD/USB flash drive/floppy/etc.  

I was able to get gcc installed from the Xubuntu installer CD via the "sudo aptitude install build-essential" method, so I think that's taken care of.

The problem I'm having right now is that I'm seeing an error that states:
> checking for ALL... configure: error: The pkg-config script could not be found or is too old.  Make sure it is in your PATH or set the PKG_CONFIG environment variable to the full path to pkg-config.

It gave me the alternative to specify ALL_LIBS and ALL_CFLAGS, but I tried 
> ./configure VAR=ALL_LIBS VAR=ALL_CFLAGS and it did not work.

Is there an environment variable I need to set, or a file I need to download and copy over in order to make this work?

Thanks very much.

---

### Post by mcduck on 2006-12-14
you shouldn't need to compile anything to get metacity..

Even though you don't have internet connection on that machine, you could run 'sudo apt-get --print-uris install metacity' to get a list of all packages needed with URI's to the files. Then you can use those to get all needed packages, or just the names and download packages from [http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by CelticWhisper on 2006-12-15
I just tried the command you posted, and the results are as follows:
> user@LinTest:~$ sudo apt-get --print-uris install metacity
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package metacity
user@LinTest:~$_

Is there another package (an apt-get package directory maybe?) I have to copy over from the install CD?

Thanks again for bearing with this n00b.

---

### Post by CelticWhisper on 2006-12-15
Okay, I did some digging and I found this link:

[http://www.svbug.com/administrator/packages&ports/m/metacity-2.6.1.html](http://www.svbug.com/administrator/packages&ports/m/metacity-2.6.1.html)

I see at the bottom a list of required and dependent packages, and also that it installs to /usr/X11R6.

Does this mean that I need to download the packages in that list and then copy them into the X11R6 directory?  Will any of them need un-archiving?  If so, is there a directory structure that must be maintained or established, or should they all be unarchived (again, assuming it is necessary to do so) directly to the /usr/X11R6 directory?

Thanks.

---

