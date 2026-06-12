---
title: "What happens when you install software in ubuntu?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by flowevd on 2008-03-05
Hi,

I used to be a windows user, now i'm an ex-windows user. I want to learn some more about how ubuntu works. 

question 1: when I install something with aptitude, what actually happens? do the application's files get put somewhere under my home directory or into one of those many 3-letter folders at the top of the filesystem? or many of them? what are all those mysterious folders for? what about dependencies?

question 2: i recently got the kubuntu-desktop package out of curiosity, found i didn't like KDE, and want to get rid of those many many apps that now clog up my beloved GNOME-menus. HOWEVER, I use amarok and Ktorrent on a regular basis. I know that these apps downloaded some kde-files as dependencies when first I apt-got them and I don't want to cripple them. Can i conduct a 'selective purge'?

thanks kind people
flowevd

---

### Post by Cypher on 2008-03-05
1) Packages that you install using APT will end up in various directories like /bin, /sbin, /usr/bin and /usr/sbin. Man pages will end up /usr/share/man and so on. So they're scattered around, but ALWAYS kept track of.

Once a package "FOO" is installed, you can see what files that package contains by doing
```

dpkg -L FOO

```
Obviously, FOO is not a real package name, but you get the idea. When you choose to remove package FOO, all the files that belonged to it will be removed as well, so there aren't going to be any leftover files you've gotta bother with.

2) You can attempt a
```

sudo apt-get remove kubuntu-desktop

```
and this will remove a lot of packages. Now if the kubuntu-desktop metapackage included Amarok and Ktorrent, they will be deleted (along with the libs) as well. You will then have to re-install those 2 applications and the necessary KDE libs will be installed without cluttering up the menu..

---

### Post by flowevd on 2008-03-05
fantastic, thanks... especially for dpkg -L

---

### Post by amyst on 2008-03-05
When software are uninstalled through Add/Remove or Synaptic Package Manager, are the files in /bin, /sbin, /user etc...  put into place during the installation thoroughly deleted?

---

### Post by Cypher on 2008-03-05
All files except configuration files are definitely removed when you uninstall a package through Add/Remove or Synaptic/APT. However, with you remove the package with DPKG, it leaves the configuration file (if there are any) and you have to the "purge" option to remove those.

You can check on these by doing
```

dpkg -l | less

```
For each package installed, it will be preceeded with "ii" indicating that it's installed and OK. If a package was removed, but left it's config files behind, you will "rc" instead..

---

### Post by aysiu on 2008-03-05
*sudo apt-get remove kubuntu-desktop* won't remove anything except the empty metapackage *kubuntu-desktop*. All its dependencies will remain installed.

If you want to remove KDE, I suggest you try [the pure Gnome](http://www.psychocats.net/ubuntu/puregnome) or [the pure Xfce](http://www.psychocats.net/ubuntu/purexfce) tutorial. Yes, both tutorials will remove KTorrent and AmaroK, but you can then ```
sudo apt-get install ktorrent amarok
``` and they will be reinstalled, along with all the necessary dependencies. Your settings for both programs will remain untouched.

---

### Post by bodhi.zazen on 2008-03-05
This is a nice link for some basics :

[http://www.debianadmin.com/debianubuntu-package-management-using-dpkg.html](http://www.debianadmin.com/debianubuntu-package-management-using-dpkg.html)

In a nut shell a "package" contains the binary application and additional information such as documentation (man pages) or configuration information.

The Linux file system is different. binary programs go in /bin
Configuration goes in /etc

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

Different vesrions of Linux use different methods to manage (install and track) packages. Debian/Ubuntu (and their derivatives) use .deb and apt. apt-get, synaptic, etc are "front ends"

When you use a deb several things happen:

1. Dependencies are checked / installed. 

2. The binary is installed.

3. Post install configuration.

I am not aware of a more simplified overview, but somehow it all makes sense after a while :)

[http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html)

[http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/)

[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

==============

To remove KDE:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

==============

Yes, linux is modular. So you can install and run single KDE applications without installing all of KDE. For example I like K3b ;)

You may also want to look at the difference between a window manager and desktop environment :

[http://www.tuxfiles.org/linuxhelp/xwtf.html](http://www.tuxfiles.org/linuxhelp/xwtf.html)

[http://xwinman.org/intro.php](http://xwinman.org/intro.php)

[http://xwinman.org/](http://xwinman.org/)

---

### Post by oldos2er on 2008-03-05
If you want to see where all the files in a package "go" when installed, open Synaptic, click Status, Installed, right-click on a package and choose Properties, Installed files.

---

### Post by amyst on 2008-03-05
Thanks for the links!!

---

