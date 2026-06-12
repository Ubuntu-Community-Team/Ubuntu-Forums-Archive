---
title: "How to install apps not in repositories?"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by sedination on 2005-06-14
Hello,

I am a complete newbie to Linux and have been playing around with Ubuntu 5.04 for the past week or so. Apt-get is wonderful and I've already used it extensively but I am wondering how to install software the traditional Windows/OS X way (opening up the web browser and finding *.exe or *.dmg files to download) because there's a lot of software that's not in the repositories.

For example, in the repositories there is Firefox 1.0.4 available but not the unstable version 1.1a. I can go to the mozilla website and download a file called deerpark-alpha1.installer.tar.gz but I am lost on what to do from here. Any help would be appreciated on how to install this.

One more example. Off the bittorrent site, I downloaded bittorrent-4.0.2.linux_i686-2_all.deb and am not sure what to do now either.

---

### Post by Xian on 2005-06-14
Understanding that packages out of the base Ubuntu repos are unsupported, you can install deb files by placing them in your /home directory, opening a terminal and then issuing this command:

```
$ sudo dpkg -i packagename.deb
```

As for those tarred files, it really depends on what they contain. They might have a bin installer file or even a source package that needs to be compiled. It can vary and there is no certain method save what the developer has provided. If it is a bin file then you just need to make it executable and run it (usually from the command line), and if it is a source package you will be required to do some different steps in order to get it running on your system. The link below is helpful in this regard.

[Installing Software in Linux](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by poofyhairguy on 2005-06-14
[QUOTE=sedination]Hello,

I am a complete newbie to Linux and have been playing around with Ubuntu 5.04 for the past week or so. Apt-get is wonderful and I've already used it extensively but I am wondering how to install software the traditional Windows/OS X way (opening up the web browser and finding *.exe or *.dmg files to download) because there's a lot of software that's not in the repositories.
[/QUOTE]

Um. The best answer is to find Apt-get repos that have the packages you need. For example, adding the backport repo will get you new Firefox (and tons of new programs). A few things have a nice and easy graphic install thing (XFCE, ATI drivers) but most require a little more work.

Here is the order (IMHO) of how to install programs in Ubuntu in order:

1. From Main
2. From Universe
3. From Multiverse
4. From Backports (newest stuff is there. help test please!!!!!)
 
(now we get into worse stuff)

5. Find Debian repos that have program you want (most unstable repos work, some might not)
6. Find a Debian package on the internet and install it using this command:

sudo dpkg -i packagename.deb

You must resolve your own dependancies. Can lead to "Deb Hell."

7. Compile the program from the source code. You must have build-essential package installed. Is the "true" universal Linux install system. Is also a big pain sometimes. I personally avoid this one like the plague.
8. Find an RPM of a package you want, and change it into a deb using alien. Read this thread for an example:

[http://www.ubuntuforums.org/showthread.php?t=38526&highlight=zsnes](http://www.ubuntuforums.org/showthread.php?t=38526&highlight=zsnes)

Has same problems as 6, but I think is better than 7.

By the way, you might want to try the "bittornado-gui" program that the backport repo has. I am a torrent nut, and I believe it works much better (the dsl/cable slow option is the greatest).

---

### Post by Xian on 2005-06-14
Let us know how that deerpark-alpha1.installer.tar.gz works out. :)

---

### Post by sedination on 2005-06-14
Thanks for the responses, Xian and poofyhairguy!

Xian, I won't be home until the evening but I'll let you know how the installation of Deer Park Alpha goes once I get the chance.

---

### Post by sedination on 2005-06-15
[QUOTE=Xian]Let us know how that deerpark-alpha1.installer.tar.gz works out. :)[/QUOTE]
 So I untarred (is that the correct term?) the file and there was a file called "firefox-installer" in the resulting folder. I ran that and it said that it was going to install Firefox into the /usr/local/firefox directory , but when I tried to install it an error message popped up saying that it can't make the destination directory. Which directory am I supposed to install it in? I tried installing into my Home folder but not icon appeared in the Applications menu for easy access.

---

### Post by desdinova on 2005-06-15
You have to run the installer as root

so

sudo firefox-installer

---

