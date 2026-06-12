---
title: "WinMD5sum and InfraRecorder not running"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by David_UK on 2006-12-30
First move towards linux.  I have downloaded Ubuntu 6.06 with the intention of running from CD.  As described, I have also downloaded WinMD5Sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
After installing and rebooting, the program seems to do nothing.  If I 'send to' the image as described nothing happens, and if I try to run the program first nothing opens.  No disc activity.
I'm using an old Win98SE PC here - is WinMD5Sum incompatible?
Is there an alternative (I didn't understand what to do with the formilab option - a bit beyond me at the moment)?

ALSO

Infra Recorder gives an error when I try to run it:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
'Infrarecorder failed to scan your SCSI/IDE busses.  Please make sure that your system is properly configured'.

Any suggestions as to how to tackle either problem would be gratefully received.

---

### Post by David_UK on 2006-12-30
Ok.  Have downloaded a different version of WinMd5Sum which is running.

Would appreciate guidance on problem 2.  I have Nero installed - can I use that instead?  Select burn image perhaps?

Thanks

---

### Post by David_UK on 2007-01-01
Ok nevermind.  Have networked the file across to another PC running XP - Infra Recorder worked fine there.

---

### Post by meng on 2007-01-01
david - sorry you didn't get a response earlier. We do try, but some threads go unanswered. Good job on solving your own problem, but don't feel that you will never get help here.

---

### Post by David_UK on 2007-01-12
Thanks meng!

I do appreciate the time and effort that the guys here put into helping us.

---

### Post by lotusleaf on 2007-01-12
[color=red]MD5 Programs:[/color]

* **md5deep** - [http://md5deep.sourceforge.net/](http://md5deep.sourceforge.net/)
md5deep is a command line program which is also available for Windows. You can use it in Linux from the command line or point and click with Krusader (which has a GUI) if you install both md5deep and [Krusader](http://freshmeat.net/projects/krusader/).

> md5deep is a cross-platform set of programs to compute MD5, SHA-1, SHA-256 Tiger, or Whirlpool message digests on an arbitrary number of files. The programs run on Windows, Linux, Cygwin, *BSD, OS X, Solaris, and should run on most other platforms. md5deep is similar to the md5sum program found in the GNU Coreutils package, but has the following additional features:

    * Recursive operation - md5deep is able to recursive examine an entire directory tree. That is, compute the MD5 for every file in a directory and for every file in every subdirectory.
    * Time estimation - md5deep can produce a time estimate when it's processing very large files.
    * Comparison mode - md5deep can accept a list of known hashes and compare them to a set of input files. The program can display either those input files that match the list of known hashes or those that do not match. Hashes sets can be drawn from the National Software Reference Library, iLook Investigator, Hashkeeper, or md5sum, and other generic hash generating programs. Users are welcome to add functionality to read other formats too!
    * Piecewise hashing - Hash input files in arbitrary blocks
    * File type mode - md5deep can process only files of a certain type, such as regular files, block devices, etc. 

* **MD5summer** - [http://www.md5summer.org/](http://www.md5summer.org/)
A simple tool for the windows user
> MD5summer is an application for Microsoft Windows 9x, NT, ME, 2000 and XP which generates and verifies md5 checksums. Its output file is compatible with the output of the Linux GNU MD5Sum and it will also read Linux generated files. It is released under the General Public License,

[color=red]MD5 (and more) information:[/color]

For Windows users: [http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)
[http://en.wikipedia.org/wiki/Md5](http://en.wikipedia.org/wiki/Md5)
[http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function)
[http://www.cs.technion.ac.il/%7Ebiham/Reports/Tiger/](http://www.cs.technion.ac.il/%7Ebiham/Reports/Tiger/)
[http://planeta.terra.com.br/informatica/paulobarreto/WhirlpoolPage.html](http://planeta.terra.com.br/informatica/paulobarreto/WhirlpoolPage.html)

---

### Post by David_UK on 2007-01-14
lotusleaf

Thanks for this - excellent!

---

