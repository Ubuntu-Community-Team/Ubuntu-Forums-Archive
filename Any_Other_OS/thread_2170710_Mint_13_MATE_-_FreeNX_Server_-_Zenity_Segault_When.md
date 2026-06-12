---
title: "Mint 13 MATE - FreeNX Server - Zenity Segault When Disconnecting Session"
date: 2013-08-27
forum: Any Other OS
---

### Post by Kirk Schnable on 2013-08-27
I just set up a fresh Linux Mint 13 (with MATE desktop) VM and installed freenx-server from the PPA.

My NX client connects to the server, and everything looks good until I press the "X".  The usual window to end or disconnect my session comes up like it's supposed to:
[IMG]http://binaryimpulse.com/wp-content/uploads/2013/08/linux-mint-13-freenx-zenity-segfault.png[/IMG]

But when I actually hit Disconnect or End, nothing happens, except this event in my syslog:
```
Aug 27 06:29:01 Stargazer kernel: [27328.797556] zenity[4421]: segfault at 5e ip 000000000040e33d sp 00007fff918dbd00 error 4 in zenity[400000+15000]
```

Am I dealing with a compatibility issue, a bug, or something which I might be able to fix?

Thanks,
Kirk

---

### Post by tgalati4 on 2013-08-27
```
man zenity
```

*Zenity* is an (old) notification framework.  It provides messages and pop-ups for applications that use it.  I presume that your FreeNX server uses it in a login/logout script.  Because you are running in a Virtual Machine, it's possible that *zenity* doesn't know where to send its output to.  Perhaps look through the FreeNX session scripts for *zenity* commands and add a *sleep* or *wait* function.

Zenity was around way before VM's, so I'm going to guess that it tries to send a notification through the VM when the output pipe is broken and it doesn't know how to handle this case gracefully.  I would do some research on what error 4 is in *zenity* and look for those session scripts that use *zenity*.  What is the host operating system and what VM framework are you using?

---

### Post by Kirk Schnable on 2013-08-27
I am using Linux Mint 13 as the guest OS, on vmWare ESXi 5.0.  I'm not really sure why the virtualization platform would make any difference, as I understood, Zenity interacts with your X environment...

---

### Post by tgalati4 on 2013-08-27
You are right it doesn't make a difference, unless it makes a difference and doesn't work.  If you have a spare machine, load Mint13 on it, no VM, and see if it works as it is supposed to.  That would at least isolate the confounding of the problem with a VM.

A quick search on *zenity error 4* in google brings up this bug:  [https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/890393](https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/890393)

*zenity* has an issue with addressing multiple screens in X.

---

### Post by Kirk Schnable on 2013-09-03
For the time being, I have switched to NoMachine's NX Free Edition.  I would rather run the GPL version, but the NoMachine one is doing the trick for the time being.  Thanks for your responses.

---

