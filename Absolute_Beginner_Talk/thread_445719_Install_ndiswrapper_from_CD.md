---
title: "Install ndiswrapper from CD"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-16
I lost my wireless internet connection - somehow, installation of MS Office via Crossover seems to have deleted or corrupted ndiswrapper - it no longer shows up.

I have no internet connection available for Ubuntu (and none for my home XP box at the moment).

Can I download ndiswrapper (whatever files I need) here at the office, create a CD to take home and use as the source to restore my ndiswrapper install?

Thanks.

Caruso

---

### Post by terdon on 2007-05-16
You can download the source package from[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=504757](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=504757)

then do:[CODE]
tar xvvzf ndiswrapper-1.43.tar.gz
cd ndiswrapper-1.43
./configure
make
make install[CODE]

---

### Post by aysiu on 2007-05-16
If you're using Ubuntu 6.10 or 6.06, *ndiswrapper-utils* is already on the CD. Just type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils
``` If you're using Ubuntu 7.04, you may be able to download the package from [here](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=ndiswrapper&sourceid=mozilla-search) and then copy it to your Ubuntu desktop and type ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by Pulka on 2007-05-16
> **carusoswi said:**
> I lost my wireless internet connection - somehow, installation of MS Office via Crossover seems to have deleted or corrupted ndiswrapper - it no longer shows up.

I have no internet connection available for Ubuntu (and none for my home XP box at the moment).

Can I download ndiswrapper (whatever files I need) here at the office, create a CD to take home and use as the source to restore my ndiswrapper install?

Thanks.

Caruso


My suggestion is to uninstall any previous ndiswrapper installed before, download the ndiswrapper version from the official site,

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

 and follow their instruccions for installation. It worked for me.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by carusoswi on 2007-05-16
> **Pulka said:**
> My suggestion is to uninstall any previous ndiswrapper installed before, download the ndiswrapper version from the official site,

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

 and follow their instruccions for installation. It worked for me.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

BUT . . . was your Ubuntu OS connected to the 'net when you installed, or do you think I would have success if I downloaded to a cd, copied the files from the CD to my Ubuntu machine and tried to install from there?

BTW, thanks to all for the replies.  I plan to copy this page onto a CD along with various copies of NDISwrapper and give it ago.  I have nothing to lose.  Worse case scenario is that I'll have to do without 'net until I can get my machine hooked up by wire.

Caruso

---

