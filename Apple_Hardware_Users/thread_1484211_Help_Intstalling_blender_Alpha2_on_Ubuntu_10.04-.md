---
title: "Help Intstalling blender Alpha2 on Ubuntu 10.04-"
date: 2010-05-15
forum: Apple Hardware Users
---

### Post by freesparks on 2010-05-15
Hello all,

      I am trying to install blender 3d animation software, and launch it from the terminal just like  the 2.49b version that I installed using Synaptic Package Manager.  This time, however I want to install it from source because the Blender 2.5 Alpha2 version is not available in the synaptic package manager.  So I downloaded the tar source file which reads :
>  blender-2.5-alpha2-linux-glibc27-i686.tar.bz2into my downloads folder.  And then, in the Terminal, went to the Downloads directory:

> cd ~/Downloadsthen typed:

> tar jxvf blender-2.5-alpha2-linux-glibc27-i686.tar.bz2 -C ~/source.Now, the instructions that I found in the source file after unpacking simply reads:

> **Linux, FreeBSD, Irix, Solaris: **Unpack the distribution, copy the  .blender directory from it to your home directory. Then run the Blender  executable.
Install scripts by putting them in the .blender/scripts inside your home  folder.I did not find the .blender file as stated in the above instructions that I found in the source folder after I unpacked the software into the source directory in my HOME directory.

Now, in the Ubuntu book that I'm reading it says that the instructions above should have stated how to compile and install the software and that typically, the procedure to compile source code is as follows:

> 
./configureand that this command runs a script to check whether all dependencies are met and the build environment is correct.  It then says to run:

> makein order to compile the software, and finally, run:

> sudo make install.My only question is in coming from a Mac background, On Mac OSX version 10.6 I have 2 different versions of blender installed on the same operating system naturally in 2 different directories so that they don't conflict.  I just want to the same in Ubuntu 10.04.

Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by KidShenck on 2010-05-16
I built it just a few minutes ago using a combination of these two pages:

[http://ubuntuforums.org/showthread.php?t=1243899](http://ubuntuforums.org/showthread.php?t=1243899)

[http://wiki.blender.org/index.php/Dev:2.5/Doc/Building_Blender/Linux/Ubuntu/Scons](http://wiki.blender.org/index.php/Dev:2.5/Doc/Building_Blender/Linux/Ubuntu/Scons)

Blender by default uses scons as it's build system, not autotools (./configure; make; make install).

You can use make if you have your heart set on it, but scons requires fewer steps and less customization.

**Edit:** Okay, I just realized that you downloaded the binary distribution. There is no need to build or install it. Just run the file ./blender in the main directory.

---

