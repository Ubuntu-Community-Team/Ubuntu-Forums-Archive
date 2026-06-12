---
title: "Add/Remove Applications - Some applications in the menu are old versions"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by burnfromwithin on 2007-08-20
I think the add/remove applications feature is great, but I'm having trouble getting the latest versions of the applications I want to download.  I'm using Feisty Fawn, 7.04

I have searched the help documents and this forum and haven't found much to help solve my problem, other than the fact that I may not have the right servers/repositories listed and that is why my list is out of date.

I have also ran: sudo apt-get udpate

More specifically:

1.  When I search for VMWare to get VMWare Player, the Add/Remove menu only gives me version 1.02-2, but I want to get Version 2.  (I did this manually using a .tar to install, but would still like to know why it is out of date on the menu).

2.  I would like to install the ntfs driver so that I can start writing files to my external hard drive again.  However, I am posed with a redundant problem in this case.  My Add/Remove applications only lists version 0.5.5, while [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) shows that the current version is obviously 1.810.  Unfortunately, when I click on the Ubuntu link looking for an install package/guide/whatever, it gives a detailed guide, telling me to use apt to install it.  (And it says for Feisty I don't need to add a repository).  My dilemma here is that I don't want to install an OLD version of the ntfs driver, I want the current one!

If anyone has any insights as to why these are out-of-date, please let me know.  Thanks in advance

---

### Post by jw5801 on 2007-08-20
They're not "out-of-date" they simply get updated a couple of months after the source code does. If you want to install bleeding-edge versions of things then you're going to need to compile them from source, or find a package from somewhere other than the repositories. You also have to take into consideration that Gutsy is due for release in a month or so, so most of the packages that are being updated will be included in the Gutsy repos and will be compiled for it.

---

### Post by tchoklat on 2007-08-20
Hi!
 
You can check a few things.
 
1. Make sure your repositories are all enabled
2. Run <sudo apt-get update> in a terminal
3. Then run <sudo apt-get upgrade> in the terminal
 
This will provide you access to the most up to date versions in the repos. To get even more up to date versions from here: [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)
 
tchoklat

---

### Post by igknighted on 2007-08-20
Ubuntu syncs the repositories with the latest version available from Debian every 6 months.  In the meantime, they do not upgrade the applications in them, only apply security fixes.  This is for stability purposes.  If staying up to date with the latest and greatest is important to you in a distro, Ubuntu is likely not your distro of choice.  Try out Sidux (basically debian sid) or Fedora for more up to date software, or if you really want a challenge try Arch Linux or Gentoo.

---

### Post by burnfromwithin on 2007-08-20
Thank you all for your help in answering my questions!

---

