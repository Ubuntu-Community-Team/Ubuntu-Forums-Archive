---
title: "QEMU OpenMoko Make file error"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by webjames on 2007-05-02
hi there Ubuntuers,
i cannot find any [openmoko]("http://openmoko.org") forums so i thought maybe someone could recognize the error i'm having.

i have downloaded the openmoko mokomakefile from [here]("http://wiki.openmoko.org/wiki/MokoMakefile#QEMU") and installed these two packages as advised:
```
sudo apt-get install qemu lynx netpbm
```
then i run this command:
```
make qemu
```
and it downloads the stuff and then i get this error:
> james@james-ubuntu:~/Desktop$ make qemu
[ -e stamps/patches ] || \
        ( svn co [http://svn.nslu2-linux.org//svnroot/mokomakefile/trunk/patches](http://svn.nslu2-linux.org//svnroot/mokomakefile/trunk/patches) patches )
Checked out revision 93.
[ -e bitbake/patches ] && \
        ( cd bitbake ; quilt pop -a -f ) || true
( cd bitbake ; svn revert -R . )
cd: 1: can't cd to bitbake
svn: '.' is not a working copy
svn: Can't open file '.svn/entries': No such file or directory
make: *** [stamps/patches] Error 1


does anyone know if i have not installed the bitbake package, or what this error means?

any help would be most kind,

---

### Post by webjames on 2007-05-03
ANSWER:
if anyone is interested it turns out you have to do:
> make setup
before
> make qemu
and you have to have libsdl dev installed.

hope this helps anyone interested in the development of the openmoko open source phone project.

---

