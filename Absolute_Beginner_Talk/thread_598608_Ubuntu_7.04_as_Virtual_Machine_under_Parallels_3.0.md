---
title: "Ubuntu 7.04 as Virtual Machine under Parallels 3.0 for MacOS X"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by shavital on 2007-10-31
Forty eight hours ago, I installed 7.04 as a virtual machine under Parallels 3.0 in MacOSX 10.4.10. I did not succeed to install 7.10, because *apparently* there is a problem with Parallels that their support team has promised to remedy. My previous experience with Parallels has been to install and run Windows XP Pro, quite satisfactorily.

This is my first post to this forum, it is quite long, for which I apologize, but I have to try and impart as much information as possible, if I expect to get forum assistance.

Although my basic system is MacOSX, I have decided to run Ubuntu, in order to learn about Linux. Therefore, your patience is appreciated, I am a total Linux newbie.
My main problem with 7.04 is starting the virtual machine. Not once I have succeed to get it working from the first attempt, and I have had to restart in recovery mode. 
After running 139 updates of all kinds, after the first installation, I have tried to install KDE, but have not succeeded yet. The CLI command 'apt-get install KDE' ends up in 'KDE package not found'. I am, though, running an application called KGpg, a tool for the administration of PGP Keys. For all I can understand, KGpg belongs to the KDE "suite".

Question: is there a KDE package available for Ubuntu 7.04, and if so, how and  where from can I get it? I have searched the kde.org web site, but only Kubuntu is mentioned. I do not yet grasp the difference between Ubuntu and Kubuntu. Thanks in advance.
Charly.

---

### Post by S.G. on 2007-11-13
I would try this to install Ubuntu 7.10:
[http://www.simplehelp.net/2007/11/01/how-to-install-ubuntu-710-gutsy-gibbon-in-parallels-desktop-for-os-x/]("http://www.simplehelp.net/2007/11/01/how-to-install-ubuntu-710-gutsy-gibbon-in-parallels-desktop-for-os-x/")

I'm now exactly trying to do the same thing as you. I need kdevelop and I installed Ubuntu...

It seems the commands:
**sudo aptitude update**
**sudo aptitude install kde** [or **sudo aptitude install kubuntu-desktop**, depending on what packages you are interested in] should be enough.

Maybe you didn't connect to the Internet (using a little PC icon on the right top of the screen). 

I can't assure this will work for you, because, after all the installation I haven't managed to see any change whatsoever. I still don't know what I did wrong. Nevertheless, the installation did start.

---

