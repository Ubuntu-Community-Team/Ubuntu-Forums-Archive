---
title: "Error installing tar"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Dagny on 2008-04-07
Hi,
I was facing some issues with the tar utility. The archives that I created and sent were damaged and I had some errors while extracting the .tar.bz2 files as well. So I completely removed the tar utility using the synaptic manager. But now when I am trying to install it afresh, I am unable to do so :(

Here is the error prompt that I get on Synaptic Package Manager:
E: /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb: subprocess dpkg-deb --control returned error exit status 2

When I try to "sudo apt-get install tar" on the command line it says:
dagny@dagnys-laptop:/opt$ sudo apt-get install tar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglade2-ruby1.8 libgconf2-ruby libatk1-ruby1.8 libglade2-ruby
  gnome-splashscreen-manager libgconf2-ruby1.8 libglib2-ruby1.8
  libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8 libgtk2-ruby1.8 libemeraldengine0
  mkisofs libpango1-ruby1.8
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


:confused:
I cant even install this update (which shows on my taskbar).

Please help!
:(

---

### Post by mrgnash on 2008-04-07
If you get an 11 error, it means you have some other package manager running: either Synaptic or the Update Manager. Close it, and try again.

---

### Post by Dagny on 2008-04-07
No. I closed all the package managers and tried from terminal. Here is what I get-
dagny@dagnys-laptop:~/Desktop$ sudo apt-get install tar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/340kB of archives.
After unpacking 2171kB of additional disk space will be used.
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So I thought perhaps there is some problem with the .deb and hence downloaded it from another repository explicitly. And when I try installing that. Here is what I see -

dagny@dagnys-laptop:~/Desktop$ sudo dpkg -i tar_1.18-2ubuntu1_i386.deb 
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing tar_1.18-2ubuntu1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 tar_1.18-2ubuntu1_i386.deb
dagny@dagnys-laptop:~/Desktop$ 
dagny@dagnys-laptop:~/Desktop$ sudo dpkg -i tar_1.18-2ubuntu1_i386.deb 
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing tar_1.18-2ubuntu1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 tar_1.18-2ubuntu1_i386.deb

Please HELP!

---

### Post by Dagny on 2008-04-07
And when I close all other managers and run the update, this is the error message I see-

E: /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb: subprocess dpkg-deb --control returned error exit status 2

---

### Post by InfinityCircuit on 2008-04-07
Bad call.  For me, tar is labeled as priority=ESSENTIAL

root@skynet:~# apt-get remove --purge tar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  tar*
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  tar
0 upgraded, 0 newly installed, 1 to remove and 47 not upgraded.
After this operation, 2150kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] n
Abort.

To recover from this you can try unpacking another copy of tar.  Boot up a LiveCD, mount the ubuntu partition, and run:
cp --parents $(dpkg -L tar | xargs) /mount-point-of-your-partition

---

### Post by braddcadd on 2008-07-14
Did this work?  Here is a thread where someone got out of this situation:
[http://ubuntuforums.org/showthread.php?t=758807&highlight=(subprocess)%3A+failed+exec+tar&page=2](http://ubuntuforums.org/showthread.php?t=758807&highlight=(subprocess)%3A+failed+exec+tar&page=2)

---

