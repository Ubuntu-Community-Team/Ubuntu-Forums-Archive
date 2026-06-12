---
title: "Problem with winecfg - multiple errors"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Bif Powell on 2007-07-27
I'm using these instruction to try and install Wine (and ultimately WoW)

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Everything progressed normally until I got to the wincfg step where I get the following output:

johnm@jm:~$ winecfg
wine: creating configuration directory '/home/johnm/.wine'...
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/johnm/.wine'.
johnm@jm:~$ wineserver: could not save registry branch to /home/johnm/.wine-LONcYc/system.reg : No such file or directory
wineserver: could not save registry branch to /home/johnm/.wine-LONcYc/user.reg : No such file or directory


Any guidance or links to deal with this appreciated. Thanks!

---

### Post by Kralizec on 2007-08-08
You might try uninstalling the version you have ("sudo apt-get remove wine") and then going to the wine homepage ([www.winehq.org]("www.winehq.org")) and downloading the latest release there. The Ubuntu repositories have been notoriously out-dated for me, especially with wine. I think there is a good chance that it was trying to have you install an old version. Once you download the tarball for the latest release, do this to install:
```

cd <directory with wine-0.9.42.tar.bz2>
tar -xvf wine-0.9.42.tar.bz2
cd wine-0.9.42
./configure
make depend && make
sudo make install

```
then once wine installs, run winecfg and see if it works any better. Once you've done that you can continue where you left off in that how-to. If a manual install works no better, then I'm sorry but I can't help.

---

### Post by Kralizec on 2007-08-08
One more thing that suggests it might be a version issue is that if you are running a fully updated release of Ubuntu (i.e. Feisty Fawn 7.04) the file "~/.fonts.conf" doesn't exist, and this seems to be causing your error. All the error messages past the Fontconfig error are caused by the fact that the configuration didn't progress past that step; namely, the configuration failed at Fontconfig, halting any progress after it so your .wine directory was never created, thus the subdirectories of .wine couldn't be created either.

---

### Post by Rocket2DMn on 2007-08-08
Check out [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
You can download a .deb package to easily install, as well as add their source to your repositories list and get updates directly from them.

---

