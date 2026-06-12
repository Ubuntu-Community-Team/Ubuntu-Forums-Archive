---
title: "[SOLVED] Arch Build System"
date: 2008-03-23
forum: Arch and derivatives
---

### Post by rye_ on 2008-03-23
Hi,

I'm interested in using arch on a spare system I have laying around, as an excercise in learning more about linux and arch.  (I've installed it ok a couple of times in the past, but don't feel yet competent e enough to use as a main system)

What I don't quite understand yet is how the ABS works.  
[http://wiki.archlinux.org/index.php/ABS](http://wiki.archlinux.org/index.php/ABS) 
The wiki says to 
1) call 'abs' from the commandline to create the abs tree (why?, what for?)
2) copy the relevant package abs to a home directory (what if such an abs doesn't exit?)

What if its a package I donwloaded from source myself, why have I not had to edit a PKGBUILD?

thanks for your help.

Note: last time I installed xfce on arch, all the panel items were bunched together.  How do I make them behave more like in ubuntu gnome, i.e. stay where I put them.

Ryan

---

### Post by rye_ on 2008-03-23
+

the package that resulted from ABS, if I were to install it on another system would dependencied by dealt with?  i..e are they defined within the package?

Thanks again,

Ryan

---

### Post by MisfitI38 on 2008-03-23
> **rye_ said:**
> Hi,
The wiki says to 
1) call 'abs' from the commandline to create the abs tree (why?, what for?)
2) copy the relevant package abs to a home directory (what if such an abs doesn't exit?)

What if its a package I donwloaded from source myself, why have I not had to edit a PKGBUILD?
1.) The ABS tree, as the wiki article explains, is a directory tree residing under /var which does not exist until you run 'abs' as root.
When you run 'abs' for the first time, it syncs up with the Arch cvs system and creates ABS for all available official Arch packages. If you read further, you may notice it indicates that the ABS tree does not contain the packages themselves, merely the ABS themselves which contain PKGBUILD files with instructions on how to compile each into an installable pkg.tar.gz. 
This is for building an *official* Arch package from source, perhaps to add or remove support for a particular function. 
Maybe you want to build package x on your system to add support for *arts*, in which case you could edit the PKGBUILD, adding arts support, copy it to a build directory and then do makepkg. (Then install with pacman -U packagex.pkg.tar.gz) 
Or, you want to build Firefox according to your compiler flags in makpkg.conf, to compile a smaller binary with the -Os flag, for instance. Then you would edit makepkg.conf with your desired CFLAGS and do makepkg, etc.
2) If such an ABS doesn't exist, you have a few choices.
A. make your own PKGBUILD (see [here.)]("http://wiki.archlinux.org/index.php/The_Arch_package_making_HOW-TO_-_with_guidelines")
B. Search the AUR, (which has about 10,000 PKGBUILDS)
C. Ask someone to make an AUR PKGBUILD for you on the AUR package requests subforum.

---

### Post by MisfitI38 on 2008-03-23
> **rye_ said:**
> +

the package that resulted from ABS, if I were to install it on another system would dependencied by dealt with?  i..e are they defined within the package?

Thanks again,

Ryan

The resulting package is cleanly installable with pacman, on the system it was built on. The PKGBUILD defines all dependencies, which can be grabbed by makepkg at the time of the build (makepkg -s uses pacman to grab binary dependencies, makepkg -b will grab the sources and compile them).
If you take the resulting pkg.tar.gz that is built and put it on a pen drive, for instance, to install on another Arch box, it may or may not work, depending on whether the dependencies on that system are met. The PKGBUILD itself would be the more logical file to transfer, since you may build it anywhere and since it contains the url of the sources to be downloaded and the list of dependencies, both of which are handled by makepkg itself (makepkg -b) or by makepkg invoking pacman (makepkg -s)

---

### Post by rye_ on 2008-03-23
thanks for this (and the links).

I don't mean to be dense.

---

### Post by MisfitI38 on 2008-03-23
> **rye_ said:**
> thanks for this (and the links).

I don't mean to be dense.

No problem. I hope it helped.
If you do not completely understand, please say so.

---

