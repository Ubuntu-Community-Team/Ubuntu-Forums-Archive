---
title: "Installing Perl"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by berong on 2007-07-04
hi, im a complete novice about PERL and LINUX but not complete novice on computers.. i wanna ask how to install a perl using the .TAR? i can use APT GET but i have no internet connection on my box.. can you help me about the direct commands use in it.. i can't understand the manual stated in softwares.. thnx..

---

### Post by aryn449 on 2007-07-04
Unfortunately you are going to need an internet connection to download the .tar file using apt-get.  apt-get simply downloads the files for installation from a repository on-line.  Hmmm.  Why don't you have an internet connection?  Are you unable to set it up or don't plan on having one?  Anyway,  you could download from another PC w/ connection and transfer the .tar file.  Good luck!

---

### Post by Vajra Vrtti on 2007-07-04
Do you have access to another box with an Internet connection? What OS?

---

### Post by aryn449 on 2007-07-04
Oops!  I guess an alternative would be to use the distro CD to install perl if you have that.  But wait a minute... you're online right now, right?  I'm confused then.:)

---

### Post by berong on 2007-09-16
i have my box on my home.. i use internet on a cafe...

here in philippines we have no much money to have an internet..


i have the .tar but i can't follow the instruction written on it..

---

### Post by tr333 on 2007-10-06
Are you trying to install perl itself or just a perl module from CPAN?

---

### Post by berong on 2007-11-28
im installing perl from cpan... i use another box for internet conection.. i use on an interet cafe for my internet conection with XP box.. i downloaded a perl for cpan and save it on my flash drive.. how i will save it on my Linux box.???

---

### Post by LaRoza on 2007-11-28
Perl is installed on Ubuntu, unless you have reason to get the latest version.

---

### Post by tr333 on 2007-11-30
Installing a Perl module downloaded from cpan is quite easy.

Extract the archive contents into a directory.
Read the README or INSTALL files on how to install.

It will usually be as follows, depending on whether there exists a Build or a Makefile.pl file.
for a Makefile.PL:
  run "perl Makefile.PL" to create the makefile.
  run "make" to run the makefile and compile the module (if needed).
  run "make test" to check that all tests for the module pass.  you might need to install some module dependencies, which would show up here.
  run "sudo make install" to install the perl module.

If you don't already have it installed, you will need to install GNU automake (for the 'make' program), available in the "build-essential" meta-package (along with the GCC compiler, etc).


Alternatively, if you have a direct internet connection, you can run the "cpan" shell (run 'cpan' from a terminal) to get an interactive shell for installing from CPAN.  The newer version of the cpan shell is cpanplus (cpanp) available in the Bundle::CPANPLUS module.

---

