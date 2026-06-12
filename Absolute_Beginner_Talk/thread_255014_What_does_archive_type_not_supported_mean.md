---
title: "What does archive type not supported mean???"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by thenewdeal38 on 2006-09-10
How do i fix this problem when downloading limewire for ubuntu and such. PLaease Help!!!

---

### Post by cwaldbieser on 2006-09-11
> **thenewdeal38 said:**
> How do i fix this problem when downloading limewire for ubuntu and such. PLaease Help!!!

You may need to explain with a little more detail.

I am going to guess that you downloaded a compressed archive of some type that your default uncompressing software does not handle.

For example, if you were in Windows and downloaded a .tar.bz2 file, you would probably not be able to uncompress it until you installed a program like 7-Zip.

---

### Post by nudnik on 2006-09-11
Limewire for Linux usually comes in an RPM package; in other words the archive is designed for Red Hat or Fedora.

Install an Ubuntu program called "Alien" from the repositories. Open a terminal, navigate to the directory where the RPM archive resides and type the following:

sudo -s 
[Enter your password]
sudo alien [name of the limewire archive file]

The above will create a Debian Package (hopefully) which should (with divine help) install with the Gdebi Package Manager, which you access by right clicking on the resulting Debian Package, and selecting the Gdebi tab.

](*,) << The Ubuntu Mascot:mrgreen:

---

