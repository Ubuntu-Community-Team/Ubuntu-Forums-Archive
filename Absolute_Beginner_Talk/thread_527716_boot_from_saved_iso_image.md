---
title: "boot from saved iso image"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-08-16
hi guys!

Here is my situation: the installation of Ubuntu 7.04 stopped at 75%. This means that all of my other partitions (including one) were formatted, so there is no OS. The installation stopped because of a bad file, a scratch on the cd.... The good news is, that I have the ISO file on the partition that remained in one peace.
I've been trying to find out how to boot from that image, but no luck. I found the basisc only. What I need is a step by step description of what to do.
I have only one cdrom, working internet with live cd, no ability to boot from USB and broken floppy drive.
The best thing for me, wold be to copy/paste everything in the terminal :guitar: if someone bears with me...

Thanx!!!

---

### Post by kiasanth on 2007-08-16
you're best bet is to burn the ISO image and boot from that, if you don't have a burner or another computer networked to this one...you are in for a hard time. Copying all the files to their location (installing manually) sounds highly tedius if not impossible. you can order the Disc on the ubuntu web site for free... that will take a while though. Booting from an ISO on a real computer, I'm pretty sure that's not possible, though I would love to be proven wrong ;)

sorry I couldn't be more help

---

### Post by wolfen69 on 2007-08-16
your best bet is to find another computer and redownload and burn the image again. that's a tough one.or take the drive out and hook it to another comp and burn the image.(to save download time) i cant think of anything else

---

### Post by duruttye on 2007-08-16
The truth is, that i have another copy of an older ubuntu, but that-s up in my little girl's room, and that seemd to me far to easy to do, i was curious, what to do in this situation:).

I've been reading these forums for like a year now, and it looks like every problem has a solution. I already thought to your solutions, but I hoped that I can do something without taking something out of my pc, it is still in warranty...

I am still curious, is there any way to install from a saved iso file :)

Thanks guys!

---

### Post by duruttye on 2007-08-16
What about installing while downloading straight from the internet??

---

### Post by Bachstelze on 2007-08-16
No. Because the saved ISO File is a file that resides on a filesystem. And for the filesystem to be accessible, there must be some kind of OS already loaded, therefore you con't start the installer from there.

However, if you have a working Live CD, it should be possible to install Ubuntu with that, see [here](https://help.ubuntu.com/community/Installation/FromKnoppix) (it says Knoppix but should work with any Live CD).

---

### Post by duruttye on 2007-08-17
Unfortunatelly this is what it happens whan trying to install the **deboostrap** package:

[HTML]pkgdetails.c:193: warning: incompatible implicit declaration of built-in function ‘exit[/HTML]

---

### Post by Bachstelze on 2007-08-17
Please provide more details. What did you type in your terminal for that to appear ?

---

### Post by duruttye on 2007-08-17
After I untared the downloaded stuff, I cd-ed in the folder, then I typed sudo make, just like on the page you sent me. and after that it shows me a few pages of this error.
like this: 
[HTML]ubuntu@ubuntu:/tmp/debootstrap-1.0.1$ sudo make
gcc -Wall -W -O2   -c -o pkgdetails.o pkgdetails.c
pkgdetails.c:1:19: error: stdio.h: No such file or directory
pkgdetails.c:2:20: error: stdlib.h: No such file or directory
pkgdetails.c:3:20: error: string.h: No such file or directory
pkgdetails.c:4:19: error: ctype.h: No such file or directory
pkgdetails.c: In function ‘fieldcpy’:
pkgdetails.c:13: error: ‘NULL’ undeclared (first use in this function)
pkgdetails.c:13: error: (Each undeclared identifier is reported only once
pkgdetails.c:13: error: for each function it appears in.)
pkgdetails.c:14: warning: implicit declaration of function ‘isspace’
pkgdetails.c:15: warning: implicit declaration of function ‘strcpy’
pkgdetails.c:15: warning: incompatible implicit declaration of built-in function ‘strcpy’
pkgdetails.c: In function ‘dogetdeps’:
pkgdetails.c:25: error: ‘FILE’ undeclared (first use in this function)
pkgdetails.c:25: error: ‘f’ undeclared (first use in this function)
[/HTML]
and so on...

---

### Post by Bachstelze on 2007-08-17
```
sudo apt-get install build-essential
```

---

### Post by duruttye on 2007-08-17
Unfortenatelly it is in Romanian...
Basicly it is an error, probably because it cannot install anything on a live cd

[HTML]Citire liste de pachete... Eroare!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_restricted_binary-i386_Packages
E: Listele de pachete sau fi&#351;ierul de stare n-au putut fi analizate sau deschise.
[/HTML]

---

### Post by Bachstelze on 2007-08-17
You can install stuff in a Live CD. Try to do a *sudo apt-get update* before.

---

### Post by duruttye on 2007-08-17
Citire liste de pachete... Eroare!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_restricted_binary-i386_Packages
E: Listele de pachete sau fi&#351;ierul de stare n-au putut fi analizate sau deschise.
ubuntu@ubuntu:/tmp$ 

It says that some files are not accessibile, or cannot be opened, probabli because of the stupid scratch on the cd...

My little girl just woke up and I found two ubuntu cds, so don't bother anymore!

Thank you!!

---

