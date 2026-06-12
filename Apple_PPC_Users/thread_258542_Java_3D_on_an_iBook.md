---
title: "Java 3D on an iBook"
date: 2006-09-16
forum: Apple PPC Users
---

### Post by blue_chili on 2006-09-16
Hi,

I am having trouble running a Java 3D application in Eclipse. It keeps coming  up with the following error:

Exception in thread "main" java.lang.UnsatisfiedLinkError: j3dcore-ogl (/usr/lib/j2sdk1.5-ibm/jre/bin/libj3dcore-ogl.so: ELF file data encoding not big-endian)

This post here ([http://lists.debian.org/debian-powerpc/2002/09/msg00307.htm](http://lists.debian.org/debian-powerpc/2002/09/msg00307.htm)) says to install libmotif3 which I have done but made no difference. I'm using the latest version of Eclipse with the latest version of Java. 

Has anyone had any success running Java 3D on a mac? It works with Tiger, I'm using the IBM Java (as the Sun version appears to only be available for x86 architecture). I'm about to attempt downloading the dmg from the Apple website to see if I can extract it somehow but if anyone can help it would be great (I've already wasted 2 days and need to get it running as its a uni project).

Thanks,
Olivia

---

### Post by blue_chili on 2006-09-16
Hi,

I figured out why its not working, the Java3D I downloaded is for an x86 processor. Appears to be a linux version for every processor except powerpcs. Looks to me that Apple are making it difficult for people using a different OS. And people think Microsoft is bad!

I've got access to a mac at uni so I've downloaded the java3d dmg file and after expecting not much success I did manage to extracted jars from it. 

However, I'm not sure how to get the libraries I need? I need files equivalent to libj3dcore-ogl.so and libj3dutils.so. In the apple dmg there is libj3d.jnilib and libj3dutils.jnilib which from my research appear to be the equivalent. I'm going to do some more googling and see if I can use or convert jnilib files for use with Ubuntu.

Any suggestions in the mean time would be handy - I'm really surprised there hasn't been any responses to this so far, maybe programing in Java3D isn't very common for mac users?

Cheers,
Olivia

---

### Post by blue_chili on 2006-09-16
I found this article ([http://www.azureuswiki.com/index.php/Intel_Macs](http://www.azureuswiki.com/index.php/Intel_Macs)) that has this command:
unzip ../swt.jar "*.jnilib"

I'm wondering if I can do that with the jar files I have except unzip them to .o files? I will report back with the results.

---

### Post by blue_chili on 2006-09-17
Hi,

Haven't got any further and its really starting to piss me off now. I don't know enough about the structure of java files to get this working, is there anyone out there who knows how I can either convert the jnilib to a .so (which I think is a shared library file or shared object or something). If I just rename the file to a so Eclipse says "invalid ELF header". The unzip option doesn't work, I can unzip the jar but I can't work out how to unzip to a new .so file.

I don't think converting the jnilib is going to work, I think what I need to do is somehow create the shared library from the jar files or something.

Please can someone help. It must be possible because it does run on a mac, just not with Ubuntu apparently. Going back to Tiger is not an option as its already corrupted various files and programs twice with two different harddisks.

Thanks,
Olivia

---

### Post by APU on 2006-09-17
Yo won´t be able to convert the .jnilib files because they are MacOS X executables for PowerPC (the format is called Mach O). Linux uses binaries in the ELF format and both are not compatible.

The Java3D you donwloaded will therefore only run on MacOS X. It seems that you have to use Tiger to program unsing Java3D on this Mac. Usually it does work very well and does _not_ corrupt files or harddrives on a regular basis. I do work with MacOS X since its first release and never had a comparable problem.

Unfortunately I´m relatively sure that tere isn´t any Java3D for Linux on PPC at the moment but I did not search very thouroughly because I dont need it myself.

APU

---

### Post by blue_chili on 2006-09-17
Thanks for the info, that's what I suspected anyway due to the lack of information from many hours of googling!

I do work the computer very hard, I'm always installing and uninstalling  programs, I think I'm just one of those people who will always break the computer eventually. Oh well. Life goes on. If nothing else I've learnt a few things along the way :D

---

