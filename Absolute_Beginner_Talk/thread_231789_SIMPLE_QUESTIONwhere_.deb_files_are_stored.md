---
title: "SIMPLE QUESTION::where .deb files are stored"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-08-07
sudo apt-get install first downloads .deb files and then installs them,but i don't know where does it stores .deb installer packages?

---

### Post by benuski on 2006-08-07
It stores them virtually.  A .deb file contains a compressed file, the program, along with instructions for the package manager (For us, Aptitude/Adept/Synaptic) on where to put the installed program.  Once the program is installed, the .deb file does not stay on the hard drive.  Its gone.  And before the installation, they're sitting up in the repositories, not on your computer.
Hope that helps!

---

### Post by az on 2006-08-07
> **benuski said:**
> Once the program is installed, the .deb file does not stay on the hard drive.  Its gone.  

No.

Each deb is downloaded and saved in /var/cache/apt/archive/ and are deleted from there when you tell synaptic (or apt, or any package manager) to delete them.

---

### Post by croak77 on 2006-08-07
> **benuski said:**
> Once the program is installed, the .deb file does not stay on the hard drive.  Its gone. 

Try looking at /var/cache/apt/archives/.

---

### Post by benuski on 2006-08-07
Whoops.  My bad.

---

### Post by noynac on 2006-08-07
Synaptic has three preference options as to temporary files. They are:

* Leave all downloaded packages in the cache.

* Delete downloaded packages after installation.

* Only delete packages which are no longer available.

The last of the above appears to be the default. There is also a button to "delete cached package files." 

Is there any reason to retain the downloaded packages in the cache? I checked with nautilus, and the cached files appear to take up a whole lot of disk space.

noynac

---

### Post by Christmas on 2006-08-08
[quote=noynac]Is there any reason to retain the downloaded packages in the cache? I checked with nautilus, and the cached files appear to take up a whole lot of disk space.[/quote]
Well you can keep them to install them later manually with dpkg, I think you can also make your own repositories offline on a CD or hard-drive but don't know how to do that. I think you have to keep the structure like the one of the online repos or the official CD.

---

### Post by u04f061 on 2006-08-08
> **Christmas said:**
> Well you can keep them to install them later manually with dpkg, I think you can also make your own repositories offline on a CD or hard-drive but don't know how to do that. I think you have to keep the structure like the one of the online repos or the official CD.

   hi can any one tell me how to make your qwn repository on cd rom and hard drive


plzzzzzzzzzzz reply this i need it badly

---

### Post by az on 2006-08-08
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

or a more simple version for personal use (you don't need to use keys):

[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

---

### Post by u04f061 on 2006-08-08
> **azz said:**
> [https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

or a more simple version for personal use (you don't need to use keys):

[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

thanks for your reply and it has full information which a newb needed ,but still i am having some problem ,with sudo apt-get install command.which is this

ejaz@msiddique:~$ sudo apt-get install apt-move dpkg-dev
Password:
Reading package lists... Done
Building dependency tree... Done
dpkg-dev is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  apt-move: Depends: dash but it is not going to be installed
  octplot: Depends: libfltk1.1 (>= 1.1.7) but it is not going to be installed
           Depends: libgfortran0 (>= 4.0.2) but it is not going to be installed
           Depends: octave-forge (>= 2004.07.07) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

when i run apt-get -f ,this is result


ejaz@msiddique:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libcln4 libfltk1.1 libgfortran0 libginac1.3c2a libgsl0 libqhull5
  octave-forge octave2.1
Suggested packages:
  pi ginac-tools gsl-ref-psdoc gsl-doc-pdf gsl-ref-html grace octave2.1-info
  octave2.1-doc octave2.1-htmldoc octave2.1-headers octave2.1-emacsen
The following NEW packages will be installed:
  libcln4 libfltk1.1 libgfortran0 libginac1.3c2a libgsl0 libqhull5
  octave-forge
The following packages will be upgraded:
  octave2.1
1 upgraded, 7 newly installed, 0 to remove and 152 not upgraded.
1 not fully installed or removed.
Need to get 5182kB/10.3MB of archives.
After unpacking 16.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe octave2.1 1:2.1.72-8
  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/octave2.1/octave2.1_2.1.72-8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/octave2.1/octave2.1_2.1.72-8_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

the reason for this is my octave is broken and needs to be upgraded.but my proxy server is blocking  files greater than 3Mb ,but the package it needs i have in the hard drive,how to give it direction of hard drive  so that it may install from it

---

