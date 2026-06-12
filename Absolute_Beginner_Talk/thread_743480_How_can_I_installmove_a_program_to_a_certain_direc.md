---
title: "How can I install/move a program to a certain directory?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by pagis on 2008-04-02
Hi,

I want to choose where (which partition or better yet which partition and directory) a program will be installed (by either apt-get or through the Synaptic Package Manager). I also want to find out where are programs I already have are at (which dir) and maybe move some. How do I do that?

Thanks a bunch

---

### Post by zvacet on 2008-04-02
To find out where installed programs are you can use this commands

```
locate package_name
```

```
whereis package_name
```

```
sudo find / -name *package_name*
```

** package_name**=exact name of package you are looking for

If you install with synaptic or apt-get by default packages goes where they supose to be so I don´t see point moving them.

---

### Post by philinux on 2008-04-02
> **pagis said:**
> Hi,

I want to choose where (which partition or better yet which partition and directory) a program will be installed (by either apt-get or through the Synaptic Package Manager). I also want to find out where are programs I already have are at (which dir) and maybe move some. How do I do that?

Thanks a bunch

Why?

---

### Post by pagis on 2008-04-03
I have 2 ex3 partitions on my hdd, one, about 30GB is the root, where I want to have my linux OS, another one, a logical partition is about 200GB and that's where I want programs to be installed.
At the moment all the programs are installed to /home/pagis which is on the root partition and I want to change that so that when I install VLC or Eclipse it will go to the big partition and only linux kernel stuff and other OS stuff will go on the small partition.

Thanks :)

---

### Post by Delkster on 2008-04-03
> **pagis said:**
> I want to choose where (which partition or better yet which partition and directory) a program will be installed (by either apt-get or through the Synaptic Package Manager).
Most applications consist of several parts. In Linux things are usually divided into different folders based on that rather than having each application dump all its files in one place.

Generally, all executables (program launch files) are in a "bin" directory. Most are in /usr/bin, but some executables needed for very basic system functionality are in /bin, and some system executables such as daemons and some system tools are in /sbin or /usr/sbin.

Library files (the ones that are usually called DLLs in Windows) are correspondingly in /usr/lib, or possibly somewhere else. Some data that can be shared between different applications is in /usr/share, documentation goes to /usr/share/doc, and system-wide configuration is in /etc. And so on...

So basically there's no single place each application would be installed. If you install third-party applications that have their own installer scripts, they may place the files in a single directory in /opt or /usr/local, but usually Debian packages are made so that they follow the division between different directories. For more information about various locations and directories, check out the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/pub/fhs-2.3.html).

> I also want to find out where are programs I already have are at (which dir) and maybe move some. How do I do that?
You probably can't move the files to a different path very easily, but to see where they are you can go to Synaptic, select an installed package, open its properties and go to the "Installed files" tab.

Most of the files installed by Debian/Ubuntu packages are probably somewhere under the /usr directory, so one possibility might be to copy the entire contents of /usr onto a separate partition and then mount that partition as /usr. That might make sense if your root partition is quite small but you have more space on another device where you could create a new partition.

I don't know exactly what kind of a partitioning scheme you have right now or what you're trying to achieve, but if you can describe that in more detail, maybe we can figure out the best way to get the result you want. In any case it probably isn't just moving files around.

---

### Post by hyper_ch on 2008-04-03
> **pagis said:**
> At the moment all the programs are installed to /home/pagis

I think you are confusing the actual program installs and the user based config files...

---

