---
title: "Tar BALLS"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Maccabee on 2006-01-15
Im a newbie in LInux and have heard abt packages distributed in say binaries like tar.gz 
Bz.tar.gz some thing similar to that stuff.
What the differecnce between tar.gz and this bz stuff?
Will it make any trouble by saving a tar bz file as tar.gz using ARK??

Also one more qtn.
Some people told me I could convert tar.gz files to .deb using ALIEN.And I did converted some files to deb in this way.But when i installed them (dpkg) I think all that was done is to merely copy the folder into my root directory.

Is it possible to install a file in bz format by saving it into tar.gz and then converting the stuff to .deb using ALIEN??

(Sorry for this innovative Idea)

---

### Post by 23meg on 2006-01-15
gz stands for gzip and bz for bzip; the difference in filenames reflects the compression method.

What's commonly referred to as tarballs, files with names ending with tar.gz and tar.bz usually carry sources, not binaries. To install an app from source, you'd first need to compile it, which means making a binary out of its source.

alien is used for converting between binary package formats used by different distros and AFAIK has nothing to do with source packages. One practical way you can make a deb file from sources is to use checkinstall (it's in the repositories); when you compile an app with checkinstall it's entered into the apt database and you can treat it as any other binary package installed via apt.

See [this]("http://www.psychocats.net/linux/installingsoftware.php") for more info on various ways of installing software.

---

### Post by hen3rz on 2006-01-15
> One practical way you can make a deb file from sources is to use checkinstall (it's in the repositories); when you compile an app with checkinstall it's entered into the apt database and you can treat it as any other binary package installed via apt.

Thank you. I always wonderd how on earth u were ment to uninstall something u made from source.

---

### Post by 23meg on 2006-01-15
Checkinstall really makes that easy, and also lets you keep track of what you've compiled from source.

To use it, first install it with ```
sudo apt-get install checkinstall
```make sure the required toolchain is installed with ```
sudo apt-get install build-essential
```and then while compiling, instead of the usual 
```
./configure
make 
sudo make install
```
do the following:```
./configure
make
sudo checkinstall
```

---

