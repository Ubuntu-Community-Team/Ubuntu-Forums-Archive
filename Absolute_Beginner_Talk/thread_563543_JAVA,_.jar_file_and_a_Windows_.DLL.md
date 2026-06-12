---
title: "JAVA, .jar file and a Windows .DLL"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by drhiii on 2007-09-30
Let me try to explain the combination of things here...

I have a .jar file that runs under Windows.  It calls a .dll that gets loaded into the Windows path.  I am trying to run this application that is started from a .jar file and is brought up under a Windows environment.   I am trying to figure out how to run this under Ubuntu, using Wine or some similar emulator, without resorting to installing something as large as VirtualBox by Innotek which is a lot for this simple application.

Is there a way to do such a thing in WINE?  To run a .jar file that calls this .dll, but under WINE or something similar.  Or do I need to go to a full blown Windows installation under something like Virtual Box to have it run under an Ubuntu installation.

tx for any help...

---

### Post by Sklasko on 2007-10-02
Perhaps you could use WINE to install Java, place the .dll in it's proper location, and then trying to open the .jar file?

---

