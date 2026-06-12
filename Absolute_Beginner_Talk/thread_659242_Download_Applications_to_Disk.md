---
title: "Download Applications to Disk"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Howgil on 2008-01-05
I have Ubuntu 7.04 installed on a PC which is not connected to the internet.  There are some Linux applications (GRAMPS, GRISBI, GIMPSHOP) which I want to install.  I have a Windows computer which is my access to the internet.  When I go to the sites supporting these applications I don't see a way download these applications to a disk on my Windows computer for installation on my Ubuntu computer.  Is there a way to download applications and updates to a disk on a Windows computer for installation on a Ubuntu machine?  Thanks.

---

### Post by lgambett on 2008-01-05
Yes... the format suitable for an easy install over Ubuntu is the .deb format.
Download the .deb file (suppose the name is test.deb), then copy it on the Ubuntu PC, then in a terminal;
***sudo dpkg -i test.deb***

---

