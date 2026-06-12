---
title: "help installing autogen"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by doubl00 on 2007-12-12
Hello 
I am trying to refresh my programming skills and have installed Anjuta IDE.  LaRoza has a good wiki and I was able to compile the "first" program in the terminal. but  multiple file programs don't seem to be recognized.  So I ma trying the IDE.  

I have a simple two class and a main (5 file) program that compiled on VS2005 (not using the CLR) but it seems I need 'autogen' to use the project options.  Right now I just have the files loaded.  

Compile and Execute Program are the only selectable option in the 'build' menu.

When I <Build> <Compile> I get " make: *** No rule to make target "NTmain.o". Stop.

Looks like I am missing something.  I installed every plugin I could find.

'autogen' is needed to open a project.  I downloaded autogen but it is in an *.RPM file.  I don't know how to install that.  

I started to post in the programming forum, but I think I need help as a beginner first.  
thanks.

---

### Post by spiderbatdad on 2007-12-12
alien is in synaptic for rpm

---

### Post by doubl00 on 2007-12-12
Thanks
I installed Alien then tried to convert the  autogen-5.9.3-5.src.rpm to a deb package and got an error that the package was not compatible with i386.  It appears I had an amd64 package even thought it said platform independent.  I downloaded the file again ad tried to convert again but the said a file was already installed.  

I did try one of the other downloads.  This time, though it was a .gz which I downloaded to the desktop.  I tried to unpack for there.  

I thought it worked as I have an autogen folder in the root (/).  But I also have one in desktop.

I tried to uncompress using tar xfvz autogen-5.9.3.tar.gz but get errors like

"
autogen-5.9.3/pkg/pkg-env.in
tar: autogen-5.9.3/pkg/pkg-env.in: Cannot open: No such file or directory
autogen-5.9.3/pkg/lsm.tpl
tar: autogen-5.9.3/pkg/lsm.tpl: Cannot open: No such file or directory
autogen-5.9.3/pkg/spec.tpl
tar: autogen-5.9.3/pkg/spec.tpl: Cannot open: No such file or directory
autogen-5.9.3/pkg/gnudir.tpl
tar: autogen-5.9.3/pkg/gnudir.tpl: Cannot open: No such file or directory
autogen-5.9.3/pkg/gnudoc.tpl
tar: autogen-5.9.3/pkg/gnudoc.tpl: Cannot open: No such file or directory
autogen-5.9.3/pkg/mkpkg.linux
tar: autogen-5.9.3/pkg/mkpkg.linux: Cannot open: No such file or directory
autogen-5.9.3/pkg/mkpkg.sh
"

I don't know what i have now but I still can't make a project in Ajunta because 
"Could not find autogen version 5, please install the autogen package. "

Do i need clean these files out?  
thanks
/don

---

