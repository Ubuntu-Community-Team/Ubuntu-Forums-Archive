---
title: "Where is my compiled kernel?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by CSMatt on 2008-02-14
I've been trying to recompile my kernel to add tuxonice support.  I've followed the instructions on the [Suspend2Kernel](https://help.ubuntu.com/community/Suspend2Kernel) documentation page, but when I get to the final command I get this:
```
$ sudo dpkg -i ../*.deb
dpkg: error processing ../*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ../*.deb
```
I've searched my while hard drive, but could not find any new Debian packages.  The image is not in /boot either.  I didn't have any problems up until this step.  So then, where is my kernel?

---

### Post by dstew on 2008-02-14
> I've searched my while hard drive, but could not find any new Debian packagesAfter the make-kpkg command, the .deb file should be in the parent directory of the kernel source, that is, in /usr/src

EDIT: By the way, that package will not be the compiled kernel, but just the source package, patched with the tuxonice code. You still need to compile it to create the kernel binary image.

---

### Post by CSMatt on 2008-02-14
How do I do that then?  The standard ./configure make make install routine, or something different?

---

### Post by dstew on 2008-02-15
I am sorry, I was mistaken, the make-kpkg program will also compile the source. You need to have the linux-kernel-devel, fakeroot, and build-essential packages installed for it to work properly.

If you are having trouble, I would suggest checking at every step to see if your procedure is working. That is, after downloading the starting source package, make sure it is in the directory. After you download the patch, make sure it is in your home directory. Before you run the patch command, make sure you are in the source directory (/etc/src/linux-source-2.6.*whatever*; you can use the pwd command to check which directory you are in.) After you apply the patch to the kernel source, make sure the source file has been changed (it should have a new date/time, and maybe a different size). After you run the make command, see if the sources were updated. Make sure you are in the /etc/src/inux-source-2.6.*whatever* directory when you do the make-kpkg command.

If you go step-by-step like this, you can probably see where you first went wrong, then maybe we can fix it.

---

### Post by CSMatt on 2008-02-15
Turns out I didn't have fakeroot installed.

Now I've got a new problem though.  While trying to compile a [custom l-r-m](https://help.ubuntu.com/community/CustomRestrictedModules), I get this error message:

```
$ fakeroot debian/rules binary-indep binary-arch
*[long list of successful compilations]*
Search for '/usr/X11R6/lib/modules/dri' in 'debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2', to replace with '/usr/lib/dri'...
debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2: No such device
make: *** [install] Error 1
```
I ran out of disk space in /home, so I installed the source code onto an external drive and launched the commands from the source directory on the external drive, if that matters.

---

