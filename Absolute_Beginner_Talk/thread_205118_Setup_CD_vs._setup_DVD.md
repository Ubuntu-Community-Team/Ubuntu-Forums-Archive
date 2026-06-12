---
title: "Setup CD vs. setup DVD"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by BobSongs on 2006-06-28
Ubuntu.com offers setup/live CDs for download:

[INDENT][http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)[/INDENT]

But this link offers setup/live DVDs for download:

[INDENT][http://cdimage.ubuntulinux.org/dvd/current/](http://cdimage.ubuntulinux.org/dvd/current/)[/INDENT]

Anyone know the difference? I've got the DVD and nothing exceptional gets installed. It doesn't seem to offer a choice between versions (Kubuntu, Edubuntu, Xubuntu & Ubuntu).

---

### Post by TigerWolf on 2006-06-28
This might not awnser your question but I installed the CD version on a DVD - because my DVD drive had troubles with the CD image (freezing on install). Im assuming the DVD is either uncompressed or has more apps already installed.

---

### Post by Xzallion on 2006-06-28
The DVD's usually have more packages on them, and are mainly for people with dial-up or no internet access.  That way they can use apt-get, aptitude, or the synaptic package manager and install the packages from the DVD.  So there wouldn't be any obvious difference between the CD and DVD.

---

### Post by clarkth on 2006-06-28
The DVD also has both the live and setup versions on one disk, the cds are separate disks.

---

### Post by bruce89 on 2006-06-28
The DVD contiains all the Main and Restricted packages, where the CD's only have the things that are installed by default.

---

### Post by MaximB on 2006-06-28
I've installed my ubuntu 6.06 from a dvd
the defrence is that the dvd version has much more programs installed on the live dvd and on the "real" installation.
the drowbacks of the dvd version is that it "costs" more hard disk space for installation and that it's installs every program it has on it and you can't chose what to install and what not to install at setup - it will install everything
if you don't like some programs - you can remove them after the installation.
 p.s
I used the GUI for the installation....so in the terminal installation maybe there is a way to chose what not to install.

---

### Post by BobSongs on 2006-07-02
Here's what I've discovered.

**The setup CD**
has one kernel: i386, a generic "works on almost everything, including the toaster" kernel. It only contains the files that are installed such as OpenOffice, gedit, Firefox, etc.

**The setup DVD**
has a variety of kernels. The correct one is installed instead of the generic i386 preventing the need to switch. The DVD has a good portion of what appears to be the Main repositories. Cuts down on the need to download.

**Assessment**
**Xzallion**'s right: The DVD is an excellent way to help someone out who has a bootable DVD drive and a slow or nonexistent Internet connection.

**TigerWolf**: the DVD does not install any more software than the CD.

**clarkth**: You're right. The DVD is a LiveDVD, a graphical setup, a standard setup (like Breezy) and an OEM setup (which I haven't tried).

**bruce89**: The DVD does not contain the entire contents of the Main and Restricted repositories as these require 3 DVDs ([see here]("http://cargol.net/%7Eramon/ubuntu-dvd-en")). But it does have a lot of the Main repository and a tiny fragment of the Restricted repository, probably just enough to carry some restricted Linux kernels.

**MAXDDARK**: again, the DVD only installs what the CD installs. I verified this by removing all repositories except what the DVD had available. Then a verification of list of available items show many things not installed.

Thanks for the feed back.

---

### Post by vinodis on 2006-07-04
thanks.

---

### Post by chasisaac on 2006-07-12
Bobsongs, 

wow and thank you very much

---

