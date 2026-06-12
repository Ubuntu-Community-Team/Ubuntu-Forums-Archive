---
title: "help with makefile configuration"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Padme on 2007-08-29
Hi, i'm new in linux and i'm installing a program called seismic unix, but i don't undestand the last step,  in short the first step is uncompress a tar file (xxxtar.z) and execute, but then i have to modify Makefile.config, and this is the part where i don't understand, next you can see the heading of the makefile. If i trythe next step (for example make install) i recibe this message:    

“Makefile:32: /src/Makefile.config: No such file or directory
make: *** No rule to make target `/src/Makefile.config'.  Stop.”

thanks!! 

 Makefile.config   				10 April 2007
#
#        Configuration file for the complete tree of Makefiles
#        in the CWP/SU Free Software distribution
#
#		-John Stockwell
#                Center for Wave Phenomena
#                Colorado School of Mines
#
# Instructions:
#   Read this file, thoroughly, and make changes where necessary
#   to reflect the needs of your system. Under most UNIX-like systems
#   the changes you make here will be transmitted to all the Makefiles
#   in the tree of CWP codes, because those Makefiles include this
#   configuration file. Many changes simply may be made by searching
#   on your operating system name, for example "Linux" or "Mac" and
#   following the instructions in that paragraph.
#
#   You need to have set the $(CWPROOT) path environment variable.
#     (Hint: the directory that this file is in is: $(CWPROOT)/src)
#   
#   Make any other changes that are necessary for your particular system.
#   Hints have been provided to aid the user in this task. 
#   
# Installation:      
#   When you are sure you have this file in agreement with your needs,
#     type:  make install    (to install the basic set of codes)  
#            make xtinstall  (to install the X-toolkit codes)  
#            make finstall   (to install the Fortran codes)
#            make mglinstall (to install the Mesa/ Open GL codes)**
#            make xminstall  (to install the X-Motif codes)*

---

### Post by nonewmsgs on 2007-08-29
i think it actually needs compiled with gcc/g++.  what you are doing is trying to execute a text file.  it would be nice if making were as easy as that though...maybe i should make a script or sometihng.

---

### Post by rsambuca on 2007-08-29
To run the make install command you need to do it as sudo.  Therefore, in the directory, enter```
sudo make install
```

---

### Post by Padme on 2007-08-30
thanks!! :KS

---

### Post by rsambuca on 2007-08-30
So did it work?!

---

### Post by Padme on 2007-08-31
hi,
 i don't now, i make the same question in ubuntu-es forum and they tell me that i have to modify Makefile.config before do make install, then i will do “sudo make install”. The problem is modify the file according to my system, but i will try  :)

---

### Post by ryan723 on 2007-09-02
Padme,

Seismic Unix compiles and installs a bit differently than many other programs.  'sudo make install' is not the solution.  The SU folks recommend that you never install as root.

I just installed SU on Ubuntu 7.04 tonight and posted instructions here:
[http://ryan.j.earley.googlepages.com/seismicunix_on_ubuntu](http://ryan.j.earley.googlepages.com/seismicunix_on_ubuntu)

your error
Makefile:32: /src/Makefile.config: No such file or directory
tells us that it cannot find the file Makefille.config (which you needed to edit before running 'make install').  Did you edit that file and save it with the same name?  

Did you set the CWPROOT environment variable?  That is my first guess as to your problem.

---

