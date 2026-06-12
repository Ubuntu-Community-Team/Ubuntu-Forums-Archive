---
title: "Synaptic doesn't have a current version of OpenOffice"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Baasha on 2006-05-29
I have Ubuntu 5.10 installed and it came with OpenOffice vs.1.9, but the current version for Linux on the OpenOffice site is 2.0.2.  I know in Windows, at least, the vs.1.9 was unstable and all those problems were fixed in the vs.2 releases.

If I uninstalled OOo and then did a manual install with apt-get would I screw things up?  I know that Linux has to make sure there are no problems before they put a program in the repositories, but isn't OOo a trusted source?  Version 2.02 has been out for quite a while so how come Synaptic doesn't upgrade the program?

I am concerned that if Synaptic updates to, say vs.2.0.1, and I already have 2.0.2, that it might crash my program.  How does Synaptic handle such things?

---

### Post by aysiu on 2006-05-29
If you feel the need for newer versions of applications (OpenOffice 1.9 doesn't cut it for you), then just upgrade to Dapper.

[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by Ted_Smith on 2006-06-05
If you're like me and have not been able to upgrade to Dapper (for various reasons) :

sudo gedit /etc/apt/sources.list

Then add this line:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

Save & close the file, & then run the following commands:

sudo apt-get update

sudo apt-get upgrade

Source : [http://lxer.com/module/newswire/view/53395/index.html](http://lxer.com/module/newswire/view/53395/index.html)

---

