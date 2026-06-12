---
title: "Is it possible to 'add' additional compile flag into a debian package"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-10
Assuming the Apache2 debian package available in the depositaries is not compiled with a flag I require. Is there a way to add the required compile flag into the deb package without compiling from tar(.gz) source and install without the benefit of debian's package management system?

Thanks !

---

### Post by BoyOfDestiny on 2006-03-10
I've never tried, you might want to google dpkg-buildpackage and source packages :) Since ubuntu does provide source repos...

After googling:

[http://www.linux.ie/old-list/52483.html](http://www.linux.ie/old-list/52483.html)

This seems like it addresses it, I guess if you have the repos enabled, start with something like

sudo apt-get source Apache2

...

Best of luck!

---

### Post by az on 2006-03-10
Once you unpack the source deb, you can go into the source directory and edit the 
debian/rules
file.  It's just a makefile.  Usuallym the additional compiler options are there but commented out.  What you describe is supposed to be easy.

---

### Post by Akhran on 2006-03-10
Thanks for the info guys :)

If I have been using aptitude to install all my packages, will installing the newly compiled deb package with dpkg affect aptitude's ability to manage this package in terms removal/dependencies?

Read that using apt-get and aptitude interchangably will affect aptitude's ability to manage those packages installed by apt-get... not sure if this is the case for dpkg and aptitude too. Would appreciate if anyone can elaborate on this and correct me if I'm wrong :)

Thanks !

---

### Post by 5-HT on 2006-03-10
[quote=Akhran] If I have been using aptitude to install all my packages, will installing the newly compiled deb package with dpkg affect aptitude's ability to manage this package in terms removal/dependencies? [/quote] 
If you use checkinstall to make a .deb and install with dpkg, you can then use aptitude to uninstall. 
In terms of dependencies though...since it was a manual dpgk install, aptitude will not mark any dependencies as automatically installed (as they weren't). So when it comes to uninstalling, no, aptitude will not uninstall any of its dependencies if they are no longer used.

There is a way around this though. Simply check what the dependencies are that you do not have installed already. Then download the dependencies and mark them as "automatically installed" (you can do this through the menu if using aptitude's GUI). That way if you uninstall it, they should go with it as well if no other package is using them.

[quote=Akhran]
Read that using apt-get and aptitude interchangably will affect aptitude's ability to manage those packages installed by apt-get... not sure if this is the case for dpkg and aptitude too. Would appreciate if anyone can elaborate on this and correct me if I'm wrong :) [/quote] 
Yup, it's basically the same idea. The "mark as automatically installed" is a great feature that can compensate for this though.

HTH

---

### Post by Akhran on 2006-03-10
How do I check what are the dependencies of the newly compiled deb package? 

Thanks for the info :)

[QUOTE=5-HT]There is a way around this though. Simply check what the dependencies are that you do not have installed already. Then download the dependencies and mark them as "automatically installed" (you can do this through the menu if using aptitude's GUI). That way if you uninstall it, they should go with it as well if no other package is using them.

 
Yup, it's basically the same idea. The "mark as automatically installed" is a great feature that can compensate for this though.

HTH[/QUOTE]

---

### Post by az on 2006-03-10
[QUOTE=Akhran]Thanks for the info guys :)

If I have been using aptitude to install all my packages, will installing the newly compiled deb package with dpkg affect aptitude's ability to manage this package in terms removal/dependencies?

Read that using apt-get and aptitude interchangably will affect aptitude's ability to manage those packages installed by apt-get... not sure if this is the case for dpkg and aptitude too. Would appreciate if anyone can elaborate on this and correct me if I'm wrong :)

Thanks ![/QUOTE]

Apt-get, aptitude, dselect, synaptic, adept, they are all frontends to dpkg.  There is only one database.

If you install a package with dpkg, you can see it in synaptic or any other package manager you have installed in ubuntu.

As for building from source, there is a control file that determines the dependancies.  If you have gotten your source package from the repo, don't worry about it.  If you are building it from scratch (a tarball) they you have to work it out.

So don't worry.

---

### Post by Akhran on 2006-03-10
Comparing between (a) and (b),

a) The squid package in the depositaries depends on libc6, netbase, adduser, logrorate, etc. So, in the process of installing squid, if any of the dependencies are not found in the system, they will be automatically downloaded, installed and marked as automatically installed. (Correct me if I'm wrong, please)

b) Download the squid source from depositaries, edit debian/rules for additional compile flags, and rebuild the deb package with dpkg-buildpackage and install the resultant squid package with dpkg.

1) For (b), are the dependencies for this new package the same as in (a) ?
2) For (b), do I have to manually download and install the dependencies (like netbase, adduser, etc) before installing the new squid package via dpkg?

Thanks :)

[QUOTE=azz]Apt-get, aptitude, dselect, synaptic, adept, they are all frontends to dpkg.  There is only one database.

If you install a package with dpkg, you can see it in synaptic or any other package manager you have installed in ubuntu.

As for building from source, there is a control file that determines the dependancies.  If you have gotten your source package from the repo, don't worry about it.  If you are building it from scratch (a tarball) they you have to work it out.

So don't worry.[/QUOTE]

---

### Post by az on 2006-03-10
[QUOTE=Akhran]Comparing between (a) and (b),

a) The squid package in the depositaries depends on libc6, netbase, adduser, logrorate, etc. So, in the process of installing squid, if any of the dependencies are not found in the system, they will be automatically downloaded, installed and marked as automatically installed. (Correct me if I'm wrong, please)

b) Download the squid source from depositaries, edit debian/rules for additional compile flags, and rebuild the deb package with dpkg-buildpackage and install the resultant squid package with dpkg.

1) For (b), are the dependencies for this new package the same as in (a) ?
2) For (b), do I have to manually download and install the dependencies (like netbase, adduser, etc) before installing the new squid package via dpkg?

Thanks :)[/QUOTE]

1 - They will be the same unless you change them by editing the control file before you build it into a binary package. (No need to do that, really.  One example where you would need to do that is if you take, say, the tovid application which has an improperly built (unofficial) deb which has no dependencies in it and put the appropriate ones in.  Somebody's gonna do that any day now and submit it to universe...)
2- No.  You would only have to do that if you stated from scratch with an empty control file.  If you run
apt-get source squid
and cd into the directory it unpacks for you, you will see the proper control file with all ten fingers and toes....  It was written by the maintainer of the package.


Ubuntu developers upload their packages iin source form.  The autobuilders (deamons) build them into binaries which then hit the repositories.  If you download the deb-src for a package and build it with the current toolchain, the binary packages will be identical except for the date and signature.

---

