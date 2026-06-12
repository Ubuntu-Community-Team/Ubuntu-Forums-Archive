---
title: "Errors in installing Mathematica 9 on Linux Mint 13"
date: 2013-03-28
forum: Any Other OS
---

### Post by mszegedy on 2013-03-28
Hi, I'm running Linux Mint 13 Maya MATE Edition 64 bit. I downloaded the latest Mathematica installer off of the Wolfram website, and it's giving me a very inscrutable error that nobody seems to have had before. I use "sudo bash ./Mathematica_9.0.1_LINUX.sh", and I hit the following roadblock:

```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                                  Wolfram Mathematica 9 Installer 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


Copyright (c) 1988-2013 Wolfram Research, Inc. All rights reserved.


WARNING: Wolfram Mathematica is protected by copyright law and international treaties. Unauthorized reproduction or distribution may result in severe civil and criminal penalties and
will be prosecuted to the maximum extent possible under law.


Enter the installation directory, or press ENTER to select /usr/local/Wolfram/Mathematica/9.0:
> 


Now installing...


[CRITICAL ERROR: dfresults not defined.                                                                                                                                                            ]






Installation failed. See /tmp/InstallErrors-4749.

```

/tmp/InstallErrors-4749 looks like this:

```
Critical Failure in CheckSpace_()
Unix/Installer/MathInstaller: line 3311: [: =: unary operator expected
Unix/Installer/MathInstaller: line 3315: [: =: unary operator expected
Unix/Installer/MathInstaller: line 3311: [: =: unary operator expected
Unix/Installer/MathInstaller: line 3315: [: =: unary operator expected

```

I've tried using both sh and bash, I've tried changing the hashbang in the front to read bash instead of sh, and I've even moved sh to sh.hidden, deleted sh, and copied bash to sh. (It took very little to undo.) I still get the same error. What the heck?

---

### Post by Dosenpfand on 2013-04-13
I'm having exactly the same problem as you. Did you resolve it or does anybode else have an idea?
Thanks in advance!

---

### Post by rewyllys on 2013-04-14
Dosenpfand, are you using Linux Mint Maya with MATE?  

The reason I ask this is that, as I reported in the Education & Science Forum ([http://ubuntuforums.org/showthread.php?t=2094436](http://ubuntuforums.org/showthread.php?t=2094436)), my installation of Mathematica 9 went absolutely smoothly in Linux Mint Maya under Cinnamon.

If both you and the OP are having this installation problem under MATE, then the problem might be linked with that desktop environment.

It could be worth trying the following: Install Cinnamon; and, under Cinnamon, try installing Mathematica 9.  If that goes well, then switch back to MATE and see if Mathematica 9 will work under MATE.  It might be the case that there's just some problem with installing Mathematica 9 under MATE but not with running it under MATE.

---

### Post by searke on 2013-04-25
The Mathematica installer has some expectations about what the desktop environment is and will give this error message in some server installations.

Most errors like this are annoying, but usually don't prevent Mathematica from actually installing. If you haven't tried already, try running Mathematica after running the installer even if you see this error message. These error messages usually happens when the installer tries to do something like put a launcher for Mathematica in a menu, so it's likely failing on something not very important. 

If that doesn't work, please try running the installer like this:

sudo ./the-Mathematica-installer.sh --keep -- -nodesktop

---

