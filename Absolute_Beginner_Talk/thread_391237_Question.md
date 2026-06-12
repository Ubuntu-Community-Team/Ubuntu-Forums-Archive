---
title: "Question"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-03-22
just a quicky...

if i install wine can i run programs of me windows hdd that i can access using ntfs g3

ta,
Nolander

---

### Post by bodhi.zazen on 2007-03-22
> **Nolander said:**
> just a quicky...

if i install wine can i run programs of me windows hdd that i can access using ntfs g3

ta,
Nolander


Depends on the program ....

Some users report it works, others do not.

Look up your program here : [http://appdb.winehq.org/](http://appdb.winehq.org/)

See the gray "Search" box on the Left ?

HTH

---

### Post by AndyCooll on 2007-03-22
What program are you seeking to run? Wine will run some M$ programs but not all.

:cool:

---

### Post by cowlip on 2007-03-22
you could try doing a symbolic link from your ntfs-3g program files mount point to ~/.wine/fakeroot/c/program\ files (or whatever that directory is), but of course that won't import the registry info that windows needs.  Maybe it would be better to intsall them on Linux as well

if the info for an app is stored in the registry, you cna export it from your current windows install, and then import the registry file into wine on linux. 

sudo wine regedit myexportedregistryfile.reg

alternatively, you could convert your current windows install into a vmware/qemu image and run it inside Ubuntu: [http://www.digg.com/linux_unix/Convert_Physical_Windows_Systems_Into_Virtual_Machines_To_Be_Run_On_Linux](http://www.digg.com/linux_unix/Convert_Physical_Windows_Systems_Into_Virtual_Machines_To_Be_Run_On_Linux)
 [http://www.digg.com/linux_unix/Windows_XP_apps_on_your_Ubuntu_desktop_now_with_Coherence](http://www.digg.com/linux_unix/Windows_XP_apps_on_your_Ubuntu_desktop_now_with_Coherence)

---

