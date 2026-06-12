---
title: "need help with source and installation"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by notld223 on 2006-08-14
ok, so I installed linux yesterday or the day before and am still getting used to it. When i tried to install cdrdao i got THIS error.
(see transcript below)


nate@nate-desktop:~/Desktop/sources$ sudo dpkg cdrdao-1.2.1.tar.gz
dpkg: unknown option -v

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
nate@nate-desktop:~/Desktop/sources$ sudo dpkg -vcdimager-0.7.21.tar.gz
dpkg: unknown option -v

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
nate@nate-desktop:~/Desktop/sources$ sudo dpkg -i vcdimager-0.7.21.tar.gz
[color="#3399FF"]dpkg-deb: `vcdimager-0.7.21.tar.gz' is not a debian format archive
dpkg: error processing vcdimager-0.7.21.tar.gz (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 cdrdao-1.2.1.tar.gz[/COLOR]

My guess is that I should use ALIEN. Only problem is I have it installed but I can't figure out where to findthe launch icon. If someone could give me some help it would be appreciated, 

Thanks

---

### Post by meng on 2006-08-14
You don't use dpkg with .tar.gz files, only with .deb files.
Look here for .tar.gz installation.
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)
(section 4)

---

### Post by catlett on 2006-08-14
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

To extract a tar, right click on it and select "extract here". Always select synaptic package manger first. Any application listed there will install and work. Not all source packages wil install.

P.S. alien is for converting rpm's into deb's/ You don't launch it, you use it as a command i.e. ```
sudo alien -i widget.rpm
```

---

