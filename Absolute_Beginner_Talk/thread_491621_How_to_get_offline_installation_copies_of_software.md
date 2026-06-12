---
title: "How to get offline installation copies of softwares"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by chaosma on 2007-07-03
At the moment, the machine on which I have Ubuntu hasn't got an internet connection. I have been able to download source code for a few softwares but for most, it seems there is no way to get the source code  in order to perform a offline installation. Is there an alternative ??

---

### Post by blastus on 2007-07-03
That's a tough one. 

One solution is to use a machine that has Internet access and download (but don't install) all the packages you need. Then copy those packages to the machine that doesn't have Internet access. I believe you would put them in the /var/cache/apt/archives directory. But there's one problem with that solution. If you haven't run "aptitude update" on the other machine it won't know how to *stat* the packages.

Another solution is to use a machine that has Internet access and create a local repository, downloading all the packages you need. You could bundle the repository on a CD and then add the CD to /etc/apt/sources.list on the machine without Internet access. Then you would run "aptitude update" and then you could install the packages you need. Search the forums--there's lots of info about creating a local repository.

If it's just one or two packages, you should be able to manually install them (once you have copied them to the machine without Internet access) with the dpkg -i command.

---

### Post by Vajra Vrtti on 2007-07-03
In an Ubuntu machine that has access to the Internet, open Synaptic an mark the packages you want to install in the other machine. The use *File -> Generate package download script* to create an script to download the selected packages from the repositories. Close Synaptic discarding the changes. Execute the script and take the downloaded packages to the other machine. There, open Synaptic and use *File -> Add downloaded packages*.

---

### Post by chaosma on 2007-07-03
Thanks. Will do that.

---

### Post by flewis7777 on 2007-07-04
Ubuntu has all the repository programs on a set of CDs now. 
Go to On-Disk.com and you will find it. I think it is a 5 CD set.

---

### Post by orbishek on 2007-07-28
see i'm currently downloading via synaptic using a live cd .what do i do to save the downloaded files before logging out.where do i search for it? this problem is because my windows overwrote the prev installation of grub ,and attempts to recover it were of no avail .pls help immediately.:(

---

### Post by Vajra Vrtti on 2007-07-28
If you mean where the packages installed by Synaptic are stored, that is in */var/cache/apt/archives*.
Did you try [this]("http://ubuntuforums.org/showthread.php?t=224351") instructions to restore grub?

---

