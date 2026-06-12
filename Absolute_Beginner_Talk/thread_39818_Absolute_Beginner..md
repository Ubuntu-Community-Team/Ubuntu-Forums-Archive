---
title: "Absolute Beginner."
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by czambran on 2005-06-06
First of all I have to say I am amazed at what the people behind Ubuntu has done. I tried linux for a while but since I didn't have the time to learn it well, I couldn't really use the computer and I went back to Windows, but with Ubuntu, it's different. After I installed it I felt right at home, because the interface is very intuitive. I can now try to learn Linux, but at the same time have a functional PC. Thank u guys.

Now I have two questions:

-Ubuntu comes with an old version of Firefox(1.0.2) which I had to update, so I download the newer version, and I installed it, now the funny thing is that I installed in a folder on the desktop, because I did not know where else to put it, so my question is what is the equivalent folder in linux to the 'Program Files' folder in Windows?

-When I got firefox for linux, I got the installer so the instalation was a breeze, but most of other programs I have downloaded they didn't have a installer so I got the source code, now my question is how do I make functional, it always says I need to compile but how do I do that? and also usually a software offers different versions for different kind of 'linux', like for example TightVNC has the following options:
Red Hat 7.x RPM
Linux source RPM
Unix source code in Tar+Bzip2 archive

how would I know which one I need to download for Ubuntu?


I would appreciate a helping hand.

Christian

---

### Post by clb137 on 2005-06-06
[QUOTE=When I got firefox for linux, I got the installer so the instalation was a breeze, 

I would appreciate a helping hand.

Christian[/QUOTE]


Hi there 

have you followed the guide????  then you can install all the latest software that has been tried and tested for Ubuntu???

see the following
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

once you have this then follow the rest of the guide to install what you need.  To keep upto date you will need to the following in a terminal window or use 'synaptic'

sudo apt-get update
sudo apt-get upgrade

once finished

sudo apt-get clean
sudo apt-get auto-clean
sudo reboot

happy Ubuntu

clinton

---

### Post by GrumpySmurf on 2005-06-06
First of all just to clarify - Linux has directories, not folders :).  This is an important distinction because it can be confusing to new users.  Especially when file management software uses folder icons to represent directories.

>  my question is what is the equivalent folder in linux to the 'Program Files' folder in Windows?
There isn't one.  

The location where programs install is dependent on a few variables.

1.  Distribution's preference
2.  Package management defaults
3.  Developer's preference
4.  End user preference

The location where a program gets installed can be determined by any of these, or a combination of them. 

For example, on SuSE, gnome is installed in /opt/gnome.  However, on Red Hat (and Ubuntu, I believe), the gnome binaries are installed in /usr/bin, man pages in /usr/man, libraries in /usr/lib.  Don't worry too much about the difference between binaries, man pages or libraries for right now, this is just an illustration.

When you download Firefox from your favorite Firefox mirror, it may be in a tar archive that you uncompress.  This would appear as a folder on your desktop if that is where you uncompressed it.  A best practice for using Linux is to install the distribution specific package for a program, usually using the distribution's tools.

By using this method, you will be consistent with other users and they can help you if you run into problems.  Using your Firefox upgrade as an example, the method for Ubuntu is to run Synaptic package management, search for Firefox in the tool and install it.  

Re: TightVNC: > how would I know which one I need to download for Ubuntu?
Again use the Synaptic tool to search for tightvnc.  You may need to have more repositories set up.

[http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto/view](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto/view)

That will tell you how to add more repositories to search for software.  I also recommend that you checked out the Unofficial Ubuntu Guide.

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

Good luck.

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=czambran]First of all I have to say I am amazed at what the people behind Ubuntu has done. I tried linux for a while but since I didn't have the time to learn it well, I couldn't really use the computer and I went back to Windows, but with Ubuntu, it's different. After I installed it I felt right at home, because the interface is very intuitive. I can now try to learn Linux, but at the same time have a functional PC. Thank u guys.

Now I have two questions:

-Ubuntu comes with an old version of Firefox(1.0.2) which I had to update, so I download the newer version, and I installed it, now the funny thing is that I installed in a folder on the desktop, because I did not know where else to put it, so my question is what is the equivalent folder in linux to the 'Program Files' folder in Windows?

-When I got firefox for linux, I got the installer so the instalation was a breeze, but most of other programs I have downloaded they didn't have a installer so I got the source code, now my question is how do I make functional, it always says I need to compile but how do I do that? and also usually a software offers different versions for different kind of 'linux', like for example TightVNC has the following options:
Red Hat 7.x RPM
Linux source RPM
Unix source code in Tar+Bzip2 archive

how would I know which one I need to download for Ubuntu?


I would appreciate a helping hand.

Christian[/QUOTE]
 For an absolute beginner, the only apps you should install are those which are available as packages specifically for Ubuntu in one of the repositories listed in ubuntuguide.org. 

If some application is not available in these repositiories, your best course of action would be asking in these forums, e.g. "where can I get application XXX for Ubuntu". 

Compiling, or building from the source, is not recommended for new users.

---

### Post by czambran on 2005-06-06
I appreciate all your answers. But I need several programs which I know work on linux, but I did not find them in the Synaptic took, like for example:
Firefox 1.0.4
TightVNC
PHP5
etc.

I really can not wait until they appear on Synaptic tool, so if you can give me any helpful link where I can try to learn how to compile programs I would really appreciate it. You answers have been really helpful and I was able to use the Synaptic to get some additional software which I needed but I also need some more software.

Thanks

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=czambran]I appreciate all your answers. But I need several programs which I know work on linux, but I did not find them in the Synaptic took, like for example:
Firefox 1.0.4
TightVNC
PHP5
etc.

I really can not wait until they appear on Synaptic tool, so if you can give me any helpful link where I can try to learn how to compile programs I would really appreciate it. You answers have been really helpful and I was able to use the Synaptic to get some additional software which I needed but I also need some more software.

Thanks[/QUOTE]
 Have you enabled all the repositories listed in ubuntuguide.org? 
Firefox 1.0.4 is available in backports repository
tightvncserver and tightvnc-java are [avaialble](http://packages.ubuntu.com/hoary/web/tightvnc-java) in multiverse. 
As for PHP5, it does not seem to be available for Ubuntu, but there are some packages for Debian, which is the next best thing (Ubuntu is based on Debian): [http://people.debian.org/~dexter/dists/php5/sid/binary-i386/](http://people.debian.org/~dexter/dists/php5/sid/binary-i386/)

Disclaimer: I haven't tried these packages (except for Firefox1.0.4), so I do not know how well they will work.

---

### Post by lightcastle on 2005-06-07
Hi. OK, so I used the Ubuntu guide and accessed all the repositories (even though the file that got called up when I did that only partly resembled the one in the guide).

And I still can't find Firefox 1.04 anywhere. I, too, tried downloading it directly, but it's in tar.gz and I'm not sure what to do with it. 

Please assume my knowledge of computers is at the level where I think they are magic boxes that might work if I sacrifice goats to them. :)

I wonder whether or not the whole "I can't seem to make anything work in Ubuntu" has to do with the fact that the person who installed this got me to by AMD 64s and installed some version that only has these newer things that no one has written any software for yet.

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=lightcastle]Hi. OK, so I used the Ubuntu guide and accessed all the repositories (even though the file that got called up when I did that only partly resembled the one in the guide).

And I still can't find Firefox 1.04 anywhere. I, too, tried downloading it directly, but it's in tar.gz and I'm not sure what to do with it. 

Please assume my knowledge of computers is at the level where I think they are magic boxes that might work if I sacrifice goats to them. :)

I wonder whether or not the whole "I can't seem to make anything work in Ubuntu" has to do with the fact that the person who installed this got me to by AMD 64s and installed some version that only has these newer things that no one has written any software for yet.[/QUOTE]
 Oh - you are using AMD64? This changes things: choice of software for AMD 64 is more limited than for x86 (usual Intel processor). You might indeed have to install things by compiling from source.

Some quick tips: 
 - ask questions in [AMD64](http://ubuntuforums.org/forumdisplay.php?f=60) forum
 - you'll probably have to compile a lot of packages from source. To do this, you need to have development (-dev or -devel) packages for imporntat pieces of sofware: e.g., in addition to usual gnome packages, you will need to install gnome-core-devel (which in turn will require a lot of other libraries and devel packages). 

After this, if you download any software in hte form of a tar.gz file, open it in archive viewer (FileRoller). There usually is a README or INSTALL file in the archive. Read it.  

Some generic instructions - here: 
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

