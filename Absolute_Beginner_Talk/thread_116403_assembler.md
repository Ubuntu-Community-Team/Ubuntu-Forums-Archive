---
title: "assembler"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-01-12
well i'm a beginning college student so i decided at the beginning of het new school year to give linux a try since we got that as a class, but my problem is that we also got a class where we are being teached asm, so my question is. how can i make this work on my linux ubunt 5.10 and what schould i install for it?

---

### Post by Mr_Grieves on 2006-01-12
What kind of assember language? There is almost one each for each hardware arcetecture.
Eg. separate languages and compilers (software you need).

When you know what one, you can check if that compiler is available in Ubuntu.

I know [http://www.thefreecountry.com](http://www.thefreecountry.com) got alot of free compilers for diffrent platforms. Check there when you know.

---

### Post by ignorance on 2006-01-13
well after looking a bit i found the program it's called Nasm and i'm not just sure but the linker will be VAL. But i absolutly have no idea how to let them work. All files are unzipped to there folder.

---

### Post by Gustav on 2006-01-13
nasm is in the repos so you can just sudo apt-get install nasm

---

### Post by ignorance on 2006-01-13
says that he can't find the package so that will be out of the question using sudo-apt

---

### Post by Gustav on 2006-01-13
```
$ apt-cache show nasm
Package: nasm
Priority: optional
Section: devel
Installed-Size: 2776
Maintainer: Christian Kesselheim <ckesselh@debian.org>
Architecture: i386
Version: 0.98.38-1.2
Depends: libc6 (>= 2.3.4-1)
Filename: pool/main/n/nasm/nasm_0.98.38-1.2_i386.deb
Size: 1547688
MD5sum: 7ccd53ab00dce4037d7701e04411e87f
Description: General-purpose x86 assembler
 Netwide Assembler.  NASM will currently output flat-form binary files,
 a.out, COFF and ELF Unix object files, and Microsoft 16-bit DOS and
 Win32 object files.
 .
 Also included is NDISASM, a prototype x86 binary-file disassembler
 which uses the same instruction table as NASM.
 .
 NASM is released under the GNU Lesser General Public License (LGPL).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```
maybe you'll need to enable the universe repo

EDIT: nope it's in main

---

### Post by ubuntuuser on 2006-01-13
[QUOTE=ignorance]says that he can't find the package so that will be out of the question using sudo-apt[/QUOTE]
just enable the additional repositories. Then apt-get will find the package.

edit: looks like I'm too late ;)

---

### Post by ignorance on 2006-01-13
[QUOTE=Gustav]
maybe you'll need to enable the universe repo

EDIT: nope it's in main[/QUOTE]

May i ask how i do that, it's just that i just picked up with linux and learning al the way.

---

### Post by Gustav on 2006-01-13
You don't have to enable universe to install nasm but it's always nice to do anyway :)

edit the file /etc/apt/sources.list
```
sudo gedit /etc/apt/sources.list
```
remove the #'s in front of the lines that begin with #deb.
save the file
update apt to know about your new repos
```
sudo apt-get update
```

---

### Post by ignorance on 2006-01-13
well i did the sudo gedit /etc/apt/sources.list but there wasn't any line of deb with a # in front so i did the update and then i did try the sudo apt-get install nasm again and i said once more it couldn't find the package.

---

### Post by Gustav on 2006-01-13
OK I think I see were the problem is. It seems as you have a strange sources.list file. Replace your /etc/apt/sources.list content with this:
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```
and then
```
sudo apt-get update
```
then you'll probably be able to install nasm the apt-get way

---

