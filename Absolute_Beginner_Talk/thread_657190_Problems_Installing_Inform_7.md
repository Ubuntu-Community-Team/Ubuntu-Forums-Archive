---
title: "Problems Installing Inform 7"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by anvivapre on 2008-01-03
I'm having trouble installing both Inform 7 for interactive fiction and the Gargoyle interpreter.

Installing Inform 7 from the web site should be straightforward. It downloads fine as a .deb file. But when I try to install it with the GDebi package installer I get an Error: Dependency not satisfiable: libart-2.0-2.

So I browsed through synaptic package installer and made sure every libart-2.02 file is there, installed and updated; but to no avail.

Inform 7 simply does not wish to install.

So any help with this would be greatly appreciated. I'm pretty new to Linux and find trying to install 3rd party software that can't be found through synaptic pretty difficult. 

Thanks.

---

### Post by FactTech on 2008-02-08
To get Gargoyle installed, I needed at least the following packages installed before I ran the compile command:

build-essential
jam 2.5
freitype
libgtk-dev
libjpeg62-dev
libsdl1.2-dev
libsdl-mixer1.2-dev
libgtk1.2-dev

If the compile fails, look at the error message and see if you can determine which package is missing. The next time you try to compile, it will skip all the parts that are already finished.

Getting Inform 7 installed did not present a problem for me, using the instructions on the download site. It may be that one of the packages I installed for Gargoyle covered the issue you're experiencing. What you may need to get over your first hurdle is the "dev" version of that package, which contains the source code the jam compiler needs.

Be advised that the Inform 7 IDE for Linux isn't quite as full-featured as the ones that are out there for Windows or Macs; the skein and transcript functionalities are not yet implemented.

Good luck!

---

