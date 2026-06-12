---
title: "How can I install updates/new apps without an internet connection?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by jerseyboy91 on 2007-03-09
I have finally gotten Xubuntu 6.06 to install on a spare computer, but now I have a new problem: I have no internet connection. So how can I install new applications/games on my Xubuntu PC without using the Internet? Are there any CDs out there that I can burn and use? Thanks in advance.

---

### Post by Bachstelze on 2007-03-09
If you have no internet connection, Ubuntu might be the wrong choice for you as it has only a very minimal set of applications on the CD. You might want to try Debian, which has more than 20 CDs of apt-gettable packages.

---

### Post by luke411 on 2007-03-09
I suppose you could manually search for any linux program you want by name and do a manual install by CD. ie. download the newest version of Firefox from their web site for Debian installations and then transfer it over.
  Keep in mind though that one of the strengths of Debian and Ubuntu is the easy updates and the software repositories that can be searched for programs, simply based on descriptions or partial package name. And of course there's the real joy of Debian, the "apt-get install" command that will download and install any program along with whatever libraries and dependencies it needs.

I would recommend if you are really worried about updates, find a way to get the pc online or simply upgrade it every 6 months with the newest Ubuntu release. But think of it as trying to update your windows pc without an internet connection. It won't be any easier with Linux.

---

### Post by luke411 on 2007-03-09
Hymn is right. There are other distros out there like Debian or Suse that come with a larger set of installation cds and thus give you more choices of programs to install from the cd. But again, the update situation would be the same.

---

### Post by jgamio on 2007-03-13
It is a DVD or you can go to the packages page and donwload what you need and modify teh source list and that&#347; it

---

### Post by bluntu on 2007-03-30
Is there a way to install ntfs-3g without an internet connection?

I'm running Ubuntu with VMWare and the internet in it is very very slow... Isn't there a way to manually download the ntfs-3g files and put them somewhere inside ubuntu that it can understand without going through the apt-get?

---

### Post by dstew on 2007-03-30
Why don't you have an internet connection?

---

### Post by bluntu on 2007-03-30
I do and am running Ubuntu with VMWARE (on xp) and the speed is 200 bits (not byte) per sec. On XP speed is very fast.

Anyway, I remember that
Linux updates stuff (apt-get, synaptic ect..)
/var/cache/apt/archives

is in there. Is there anyway to manually install by putting stuff there?

---

### Post by dstew on 2007-03-30
You can download debian packages on your XP, then copy them over to Ubuntu. In Ubuntu you can install the package by using **sudo dpkg -i *name_of_package***

see [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

