---
title: "'in the repos'"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by pwrstick on 2006-04-25
Hello,

When someone says "get it from the repo" what exactly do you do?  I'm relatively new to linux - I got XGL installed and am trying to install the transparency plugin (I'm doing it in Breezy).

In another [post]("http://www.ubuntuforums.org/showthread.php?t=133772&page=16") someone refers to a few .debs in the repos (transset and xbindkeys), but I don't know how to retrieve these.

Thanks!

---

### Post by Sef on 2006-04-25
> When someone says "get it from the repo" what exactly do you do? I'm relatively new to linux - I got XGL installed and am trying to install the transparency plugin (I'm doing it in Breezy).

In the repositories which is where more software to download is kept.

Read this by psychocats on installing more software.

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

> In another post someone refers to a few .debs in the repos (transset and xbindkeys), but I don't know how to retrieve these.

Through Synaptic Package Manager.  System > Administration > Synaptic Package Manager.

---

### Post by gingermark on 2006-04-25
Repositories of software exist that ubuntu can install from.
You can browse (and install) this available software using Synaptic Package Manager (or Adept in Kubuntu).

These programs are front-ends for a command called apt (so if you see someone say "sudo apt-get install" something then it's the same thing.

Your repositories are located in a file called 'sources.list' which is in the /etc/apt folder.

Assuming you are using ubuntu, you can enable extra repositories by running "Terminal", and typing
```
gksudo gedit /etc/apt/sources.list
```
This will open a text editor. Remove any '#'s before any lines that begin 'deb', then save the file, and in terminal type ```
sudo apt-get update
```

You will now have a lot more software easily accessible to you. Run Synaptic to browse it.

All the software in the repositories is in Ubuntu's native binary format .deb. This can be downloaded and installed (by typing "sudo dpkg -i packagename.deb".

Have a look at [http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php) for more info.

EDIT: Beaten to it, what a shock :)

---

### Post by az on 2006-04-25
Everything in main and universe are gpl-compatible which means that the source code has to be available.  Everyting in free-libre open source is done via the source code.  

When a developer works on a package, the make their changes and compile and test it, but they upload the source to the archive and the autobuilders make the package (binary) that you install through apt (synpatic, adept or any other package manager)

Since not just anyone can be a developer and upload to the archive, and the source is what is used, you know that what you get is the real deal and not some hacked package that spies on you or something.

---

