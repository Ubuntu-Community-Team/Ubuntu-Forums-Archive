---
title: "Help with .exe"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by admrly06 on 2006-05-05
I'm trying to install my wireless card drivers. I need to get the files out of the exe file. Is that even possible? If so how do I do it?

---

### Post by skippy81 on 2006-05-05
EXE is a windows executable.  It won't work with linux.  However you may have luck with the ndiswrapper option.  Basically you can install your .EXE file onto a windows computer, and extract the .inf driver file.  This can then (sometimes) sucessfully be used to make your card work on linux.  I posted a brief guide for someone else earlier:
[http://www.ubuntuforums.org/showthread.php?t=170631]("http://www.ubuntuforums.org/showthread.php?t=170631")

If you have wired access to the net from your linux machine, then your task will be a lot easier.  You can simply download ndiswrapper-utils and ndisgkt from the Synaptic package manager.

Let us know whether you can access the net from your linux machine.  If you can't then we need to know if your on a 64bit or i386 PC and also ideally the model of your wireless card.

---

### Post by joshrobinson on 2006-05-05
[QUOTE=skippy81]EXE is a windows executable.  It won't work with linux.  However you may have luck with the ndiswrapper option.  Basically you can install your .EXE file onto a windows computer, and extract the .inf driver file.  This can then (sometimes) sucessfully be used to make your card work on linux.  I posted a brief guide for someone else earlier:
[http://www.ubuntuforums.org/showthread.php?t=170631]("http://www.ubuntuforums.org/showthread.php?t=170631")

If you have wired access to the net from your linux machine, then your task will be a lot easier.  You can simply download ndiswrapper-utils and ndisgkt from the Synaptic package manager.

Let us know whether you can access the net from your linux machine.  If you can't then we need to know if your on a 64bit or i386 PC and also ideally the model of your wireless card.[/QUOTE]

you can extract files from an .exe in linux:
from the ndiswrapper install page

Extracting drivers from EXEs or CAB files

If theres no windows driver listed for your card, or your card isn't there at all, you might as well try to locate a driver, and add it if you succeed. The drivers you find may be packaged as an executable file. These notes were extracted from the List of cards, there may be more there.

    * Use [cabextract] on the exe file.
    * Use [unshield] to extract from CAB files, typically named data1.cab, data1.hdr, data2.cab. Also read [here] for a bit more detail. 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")
go there to read it and get link for cabextract.. just scroll down till you see excracting drivers from exes

---

