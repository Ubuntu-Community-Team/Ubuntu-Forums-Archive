---
title: "Issues with Java install"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-09-07
Hi,
    I just installed Ubuntu on a friends computer and I was following the Enable Mulitmedia thread; I hit some issues when installing Java. A box popped up that told me to read the license and check the box if I accept. I notied that I could not scroll through the license and that if I tried to check the box, the program would freeze. I have tried this 3 times now and I decided to give up on it because I was about to install Xubuntu on the computer anyway because of its low resources. I went to the package manager and noticed that I had to fix the Java package before I could install any other packages. I can not remove the packages because I am told that the packages are too unstable and I can not upgrade them or reinstall because the installer freezes at the same point. How can I get these packages taken care of? I don't care if Java doesn't get installed because this computer wont keep regular Ubuntu and I assume that there is a different way to enable multimedia on Xbuntu anyway. Thanks for the help!

---

### Post by jnorthr on 2007-09-07
You may need to read the man pages for apt-get like: man apt-get
there you will see several options to clean or autoclean partiallly loaded pkgs. Often this requires you to act as super user (sudo) so you might try:
sudo apt-get clean
or
sudo apt-get autoclean
or 
sudo apt-get autoremove

but read the doc.s first.

---

### Post by kevindubrow on 2007-09-07
I ran a few and am getting some results. The last command you gave me is downloading and reinstalling the packages, hopefully they won't freeze this time. Where can I find these pages you are talking about? In case this doesn't work. Thanks!

---

### Post by jnorthr on 2007-09-07
All documentation is available in the form of manual pages of instructions. From a terminal command line, for example type:
man apt-get
man ls
man ps
to get the feel of what is on offer in the way of documentation. You can also try system>help and support   to bring up the ubuntu help and welcome panels. Walk thru there to gain an intro to what's available. It really is useful going thru 'new to ubuntu' topics. When you've exhausted that, you can use synaptic or apt-get to grab sets of documentation about specific languages, tools, compilers, actually pretty much anything you want is available in greater detail. Of course, you also have the forums and planet ubuntu here: [http://planet.ubuntu.com/](http://planet.ubuntu.com/).
Make sure you're java jdk is installed correctly then install an IDE like eclipse if you need better development tools.

Enjoy -:D

---

### Post by kevindubrow on 2007-09-07
Thank you so much, I successfully got Java reinstalled through the terminal. Now if only Xubuntu installed correctly :biggrin:...but thats another thread! Thanks very much!

---

