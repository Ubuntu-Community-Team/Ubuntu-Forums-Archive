---
title: "ParaView"
date: 2006-09-19
forum: Apple PPC Users
---

### Post by pauljwells on 2006-09-19
I just got ParaView to compile. If anyone is interested in a howto on compiling ParaView on Ubuntu Dapper PPC I'll write one...

---

### Post by jimo on 2006-10-03
Can you send me your howto about compiling paraview in ubuntu? I have struggled for a week to compile it. Thanks.

---

### Post by pauljwells on 2006-10-05
You need to install a few packages from the repos:
        
build-essential, and cmake

and you need to make sure you have the following development packages too (installing these should install their respective libraries, but if not, then make sure you install those also):
        
        freeglut3-dev
        libgl1-mesa-dev
        libglu1-mesa-dev
        libx11-dev
        libxau-dev
        libxdmcp-dev
        libxext-dev
        libxi-dev
        mesa-common-dev
        x11proto-core-dev
        x11proto-input-dev
        x11proto-kb-dev
        x11proto-xext-dev
        
you unpack the ParaView sources tarball in a directory of your home account, say ~/ParaView-2.4.4 and you create a build directory , say         ~/ParaView-build 
then, in a terminal, cd to the build directory and type 

```

cmake -i ../ParaView-2.4.4

```

This is all just the standard cmake stuff...

this brings up the cmake question and answer session. You need to say        'yes' to view advanced options. You can accept the default for everything except 'build shared libraries', for which you need to select'ON'
After that it should chug away for about an hour and reward you with a
set of executables, and instructions as to how to install them
in /usr/local/bin

---

