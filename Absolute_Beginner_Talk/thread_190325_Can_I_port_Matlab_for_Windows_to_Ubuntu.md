---
title: "Can I port Matlab for Windows to Ubuntu"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Phasmagon on 2006-06-06
I have aquired Matlab 6.5 for windows with a student licence from my university.
I cannot aquire a copy for Linux (the do not have it).
Is there anyway I can port the windows installation files to Linux?

Thanks

---

### Post by NeghVar on 2006-06-06
You can try Wine, it always a number of windows programs to work on Linux.

---

### Post by Phasmagon on 2006-06-06
Matlab is known to have alot of issues with wine.
Anyhow I have to create a chroot environment since I have amd64 distro (which does not support wine). And I am not going to make my life that complicated, since I have a version of windows installed.

The readme in the CD states that the CDs support both Windows and Unix systems. The problem is that it does not have any installation scripts for unix.

Maybe it's just a general readme and the statements above are just false. The fact that all archives are microsoft cabinet files supports this.

But maybe (just maybe) it is possible to install them anyway, using the appropriate script and utils, such as (cabextract).

Any suggestions?

---

### Post by hotbrainz on 2006-06-06
You could go for VMWare to run Matlab. It will be an absolutely fool proof way of doing it unless you have a low config system.  Wine does have quite a few issues. For VMware this thread is good:

[http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

---

### Post by Phasmagon on 2006-06-06
Thanks for that, but still this is not what I am looking for.
I really don't care about rebooting, it's just that matlab is native to Linux and I preffer Linuxes philosophy alot to compared to windows.
The only thing I would like to know if it is possible to do what I said previously. If not it's ok.

Thank both of you NechVar and hotbrainz

---

### Post by edgardz on 2006-06-15
If you like the linux philosophy... euh... don't use Matlab ! The big "tendance"  in linux computing  is to use Python. With package like matplotlib, ipython, numpy etc...  sky is the limit !

---

### Post by taurus on 2006-06-15
There is a version of Matlab for Linux but the question is can you transfer your student license for Windows to Linux?  I don't think they will allow you to do that but you should contact Matlab and see what they have to say.  If they allow you to do that, then you just download the Linux version from their site and use your serial number for it!!!

---

### Post by Kilz on 2006-06-15
[QUOTE=Phasmagon]Matlab is known to have alot of issues with wine.
Anyhow I have to create a chroot environment since I have amd64 distro (which does not support wine). And I am not going to make my life that complicated, since I have a version of windows installed.

The readme in the CD states that the CDs support both Windows and Unix systems. The problem is that it does not have any installation scripts for unix.

Maybe it's just a general readme and the statements above are just false. The fact that all archives are microsoft cabinet files supports this.

But maybe (just maybe) it is possible to install them anyway, using the appropriate script and utils, such as (cabextract).

Any suggestions?[/QUOTE]
Just to let you and others who read this know. [You do not need a chroot to install wine in Dapper]("http://www.ubuntuforums.org/showthread.php?t=185557")

---

### Post by jpkotta on 2006-06-15
I would ask MathWorks to switch your license to a Unix one and send you a Unix version.  They make a student Unix version.  I know this because in my university bookstore you can buy Matlab and it says on the box "for Windows, Mac, and Linux".

That said, I just use Octave on Linux.  It's just as good, unless you're doing some really heavy duty stuff or using more advanced features like the GUI toolkit or Simulink.  I bought student Mathematica instead, because Matlab and Octave suck for symbolic math and it is *exactly* the same as the professional version, unlike student Matlab which doesn't have a lot of toolboxes.

---

