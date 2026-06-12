---
title: "PPC &quot;emulation&quot; on PPC"
date: 2007-01-18
forum: Apple PPC Users
---

### Post by Ubunto&amp;XP&gt;98&gt;Mac7&gt;ST&gt;994a on 2007-01-18
On my Athlon64 I can dual boot x86 and 64-bit windows xp and Ubuntu.  I can also run Vmware inside either to run the other as a guest at near normal speed of course since there is no CPU emulation.  The same can be done on Intel based Macs with Parallels - running x86 Ubuntu and  the Intel version of OS X.  I would like to have Ubuntu on my G3 iBook, but for a variety of reasons would prefer to run it in a virtual environment.  Is there any program that will do that.  Pear emulates PPC on intel, and Sheepshaver emulates classic on intel I believe.  What I want is to "emulate" PPC on PPC so I can have a nice tidy virtual hard drive file to move around if I need to for Ubuntu.

Anything out there for me?

---

### Post by dpny on 2007-01-19
In a similar situation I tried unsuccessfully to find PPC emulation software for my G5. The closest I came was Q/QEMU, but they seem to have stopped their attempts to PPC emulation after the Intel switch.

edit: There's also XEN PPC, but developement there seems to have ground to a halt as well.

---

### Post by ssam on 2007-01-19
in powerpc linux you can run mac-on-linux, but i have not seen anything to run other powerpc operating systems from within mac os x.

the mac on linux site website on the news page it says that mol will so run on mac os x. however that page is highly out of date. it looks like the project is now developed at [http://mac-on-linux.sourceforge.net/news.php]("http://mac-on-linux.sourceforge.net/news.php").

---

### Post by dpny on 2007-01-19
> **ssam said:**
> in powerpc linux you can run mac-on-linux, but i have not seen anything to run other powerpc operating systems from within mac os x.

the mac on linux site website on the news page it says that mol will so run on mac os x. however that page is highly out of date. it looks like the project is now developed at [http://mac-on-linux.sourceforge.net/news.php]("http://mac-on-linux.sourceforge.net/news.php").

I believe the promise of MOL under OS X is at least two years old. The Intel-switch seems to have taken the wind out of a lot of the PPC emulation projects.

---

### Post by calum on 2007-01-19
> **ssam said:**
> in powerpc linux you can run mac-on-linux, but i have not seen anything to run other powerpc operating systems from within mac os x.

The mac-on-mac project promised this, but development has since stopped.  The last code drop may or may not be in good enough shape to be of any use to you.

[http://maconmac.bastix.net/](http://maconmac.bastix.net/)

---

### Post by dpny on 2007-01-19
> **calum said:**
> The mac-on-mac project promised this, but development has since stopped.  The last code drop may or may not be in good enough shape to be of any use to you.

[http://maconmac.bastix.net/](http://maconmac.bastix.net/)

MOM development has been stopped for some time.

---

