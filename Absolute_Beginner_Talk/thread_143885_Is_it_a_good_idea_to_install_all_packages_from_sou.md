---
title: "Is it a good idea to install all packages from source with checkinstall?"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-13
Advantages: 

1) latest version since we are using the latest source code.
2) still manageable by debian/ubuntu package system since it is installed with dpkg.

Any disadvantages?

So, should we just download all the latest source code and install with checkinstall for the latest version and yet manageable by the package system?

Thanks :)

---

### Post by az on 2006-03-13
[QUOTE=Akhran]Advantages: 

1) latest version since we are using the latest source code.
2) still manageable by debian/ubuntu package system since it is installed with dpkg.

Any disadvantages?

So, should we just download all the latest source code and install with checkinstall for the latest version and yet manageable by the package system?

Thanks :)[/QUOTE]
If you want your package to have proper dependancies, you have to hack that yourself.  If you want your package to use the configuration database and proper pre-install, post-install preremovel and post removal scripts, you will have to hack the makefoe yourself.  You should just build it into a proper deb package if you are going to do all that work anyway.

So, checkinstall builds rudimentary packages that install and remove themselves - that's it.  If you need to do other stuff to properly integrate with other packages, you are on your own.  You may eventually bork your system, I guess.

---

