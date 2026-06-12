---
title: "Installing a deb file: dpkg not found"
date: 2012-10-30
forum: Any Other OS
---

### Post by GiorgosK on 2012-10-30
Hi all,

I am new to linux, and trying to install a .deb application. I use fedora 17.
I found that i should use dpkg -i <namefile>.deb, but all I get is "bash: dpkg: command not found". On internet I find that I should type sudo in front, but when I try the same command as root, I get a similar error "sudo: dpkg: command not found".
I have also tried to install the application from the graphical interface (open the deb file with gdebi), but I don't find gdebi... Is it possible that I miss gdebi? How can I install it then?

Thanks,
Giorgos

---

### Post by wojox on 2012-10-30
You need to find a .rpm package. Deb's are for Debian. Rpm's are for Fedora. :P

---

### Post by sucksatcompiling on 2012-10-30
Fedora uses RPM packages instead of DEB packages.  Ubuntu is Debian based, hence why it is based around using dpkg and *.deb packages.  I recommend looking for the software you're trying to install in an RPM format which Fedora should have little issue installing.

---

### Post by ajgreeny on 2012-10-30
You are using **Fedora-17**, not Ubuntu, so why did you come here?

However, Fedora does not use .deb packages; it uses rpm packages, so you will need to search out what you want in Fedora's own repositories.

Sorry I can't help you more than that, but I tried Fedora-17 for a short time, decided it was not for me, so gave up on it and came back to the comfort of ubuntu and its family of OSs.

You should join [http://www.fedoraforum.org/](http://www.fedoraforum.org/) for the help you want.

---

### Post by oldos2er on 2012-10-30
Moved to Other OS/Distro Talk.

---

### Post by GiorgosK on 2012-11-05
Thanks very much for the help!

---

### Post by northrup on 2012-11-05
You can use Alien to do this; Alien is a neat little tool that converts back and forth between RPM and Debian packages (plus SLPs and .tgz packages).  First, see if you can install it via yum:

```

su -c "yum install alien"

```

If that doesn't work, type this in the terminal emulator of your choice to install it manually:

```

cd /home/(your username)/Downloads/(whatever directory you want)
wget http://content.hccfl.edu/pollock/AUnix1/alien/deb-1.10.27-3.i586.rpm
su -c 'rpm -i deb-1.10.27-3.i586.rpm'
wget http://content.hccfl.edu/pollock/AUnix1/alien/html2text-1.3.2a-3.i586.rpm
su -c 'rpm -i html2text-1.3.2a-3.i586.rpm'
wget http://content.hccfl.edu/pollock/AUnix1/alien/alien_8.78.tar.gz
make PREFIX=/usr
su -c 'make PREFIX=/usr install'

```

Those steps are derived from [this page](http://content.hccfl.edu/pollock/AUnix1/alien/).  Assuming that's all successful, you can then install any .deb package via the following:

```

su
alien --to-rpm <name of package>.deb
rpm -i <name of package>.rpm

```

Hope that helps!  Let me know if anything doesn't work or if you have further questions.

---

