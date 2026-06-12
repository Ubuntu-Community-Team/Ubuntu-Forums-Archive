---
title: "Error while copying to &quot;/&quot;."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by animalprimate on 2008-03-18
seems i cant copy to root, i cant access lost+found folder either

it tells me,

You do not have permissions to write to this folder.

knowin why?

also im not sure how to install

File-Temp-0.20.tar.gz
IO-Socket-SSL-1.13.tar.gz
Term-ReadLine-Gnu-1.17a.tar.gz
TermReadKey-2.30.tar.gz

*corresponding to the perl packages*

- Term::ReadLine::Gnu and an appropriate 4.x version of GNU libreadline
- Term::ReadKey
- IO::Socket::SSL
- File::Temp

**courtesy of CPAN *[*http://cpan.org*]("http://cpan.org")

warning! reading enclosed section could be a waiste of time.
____________________________________________________________________

this is what im tryin to do:

INSTALLATION (install Perl Mud Client)

Prior to install, make sure you have to following Perl packages installed
on your system:

- Term::ReadLine::Gnu and an appropriate 4.x version of GNU libreadline
- Term::ReadKey
- IO::Socket::SSL
- File::Temp

All these packages can be found on CPAN ([http://cpan.org](http://cpan.org)) if you do not
have them already.

Then, execute the following commands:

  perl Makefile.PL
  make
  make install

The make install step should be performed using root rights."
____________________________________________________________________

---

### Post by Jimmey on 2008-03-18
To run a command with "root rights", use the sudo prefix.

You might be able to install readline and readkey packages with Synaptic package manager - Open that up and search for them.

Entering the command ```
perl Makefile.PL && make && sudo make install
``` into a terminal should then work.

EDIT

Infact, just search synaptic for whatever you're trying to install (Perl Mud client?). It'll probably be there.

---

### Post by animalprimate on 2008-03-18
thanks chap.

---

