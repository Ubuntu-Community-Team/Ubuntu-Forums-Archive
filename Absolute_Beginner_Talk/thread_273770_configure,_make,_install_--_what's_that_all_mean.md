---
title: "configure, make, install -- what's that all mean ?"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-08
Hello,

Newbie here -- still learning the Linux ropes!  Need some help understanding what it means to ./configure, make, and install software.

I have been trying to mount my iDisk (from my .Mac service, which is a webdav protocol) in a folder on my desktop for ease of use.  I originally tried to use davfs2 ([couldn't get that to work]("http://www.ubuntuforums.org/showthread.php?t=233872")), and then fell back to using Nautilus's "Connect to Server" feature ... which is working okay (some apps have a hard time with the files).  

However, now I want to move to XFCE desktop, which doesn't seem to have Nautilus.  Am back to square one -- I can't get davfs to work.

Enter a new discovery!  Recently, [I learned how to setup a SSH connection with a remote host and mount that into a folder]("http://www.ubuntuforums.org/showthread.php?t=270806") (using sshfs); this works great!  Quick alias in bash and I am connected, fast and furious -- perfect integration.

The same system that runs the sshfs [(FUSE]("http://fuse.sourceforge.net")) has another branch off for webdav connections.  It requires me to download, ./configure, make, and install two packages I can't find in the repositories:

[http://0pointer.de/lennart/projects/fusedav/](http://0pointer.de/lennart/projects/fusedav/)
[http://www.webdav.org/neon/](http://www.webdav.org/neon/)

Since this doesn't come with point and click instructions, I need some help figuring out how to install these.  Is there any good resources that might help me ?

Thanks,
Damon

---

### Post by AndyCooll on 2006-10-08
This refers to compiling a program using the source file.

You compile the program from the command line. It usually follows a process along the lines of:

```
cd /to/file/to/be/compiled
./configure
make
sudo install
```

Please note you may need to install build-essential first.

:cool:

---

### Post by thornomad on 2006-10-08
Hello, thanks for that reply.  Install "build-essentials" ?  You mean, via a:

```
$ sudo aptitude install build-essentials
```

Also, does it matter where I have uncompressed the .tar.gz file I download?  I mean: will running that from the uncompressed folder on my Desktop load the file onto my Desktop ?  Or will it move itself where it needs to go ?

Thanks!

---

### Post by AndyCooll on 2006-10-08
Yes to the "aptitude install" bit, no to the "where it wants to go" bit.

You'll need to unzip the file (preferably) to your home directory and then "cd" to that relevent folder to begin the install process.

:cool:

---

### Post by thornomad on 2006-10-08
Sorry ... not sure I am understanding you quite right ... (I understand the "aptitude install" bit!).  

So I am going to download fusedav-0.2.tar.gz to my ~/Desktop.  Then I am going to run:

```
$ tar xzf fusedav-0.2.tar.gz
```

Then *which* directory do I navigate to ?  Inside the fusedav-0.2 directory ?  Or to the directory I want the program to install to (and if that is the case, how do I know where to put it?) ?

Thanks!

---

### Post by thornomad on 2006-10-08
So I trolled around a little in the last few minutes and found this explanation:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

These sounds like I need to put the uncompressed folder in a location that I am not going to delete after it has been installed.  Is that correct?  So, would make sense to create a folder called ~/downloads or something and put the uncompressed binary files there?

D

---

### Post by CatKiller on 2006-10-08
[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/") should answer a lot of your questions.

---

### Post by snakyjake on 2006-10-09
> **thornomad said:**
> Sorry ... not sure I am understanding you quite right ... (I understand the "aptitude install" bit!).  

So I am going to download fusedav-0.2.tar.gz to my ~/Desktop.  Then I am going to run:

```
$ tar xzf fusedav-0.2.tar.gz
```

Then *which* directory do I navigate to ?  Inside the fusedav-0.2 directory ?  Or to the directory I want the program to install to (and if that is the case, how do I know where to put it?) ?

Thanks!

1. Save your tar.gz file anywhere you'd like, perhaps /usr/src.
2. Change to the directory that you untarred to.
3. Run the installation as described in the Ubuntu documentation (please see the wiki links), or the readme that came from the tarball, or from the tarball's website.
4. No need to keep the file nor the untarred folder, delete if you wish to conserve drive space.

---

